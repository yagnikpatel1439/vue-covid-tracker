<template>
    <select 
    v-model="selected" 
    class="form-select mt-10 block border w-full p-3 rounded"
    @change="onChange()"
    >
        <option value="0">Select Country</option>
        <option v-for="country in countries" :key="country.ID" >
            {{ country.Country }}
        </option>
    </select>
</template>

<script>

export default {
    name: 'CountrySelect',
    props: ['countries'],
    data() {
        return {
            selected: 0
        }
    },
    methods: {
        onChange() {
            const country = this.countries.find((item) => item.ID === this.selected)
            // console.log(country)
            this.$emit('get-country', country)
        }
    }

}
</script>
