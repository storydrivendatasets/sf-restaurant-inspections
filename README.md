# San Francisco Restaurant Inspections

The real-world (i.e. minimally cleaned) version of San Francisco Health Inspection Data.




Slug: **sf-restaurant-inspections**

Repo link: [https://github.com/storydrivendatasets/sf-restaurant-inspections](https://github.com/storydrivendatasets/sf-restaurant-inspections)






## Dev/Reproduction notes

Data was previously found at the [San Francisco Department of Public Health](https://www.sfdph.org/dph/EH/Food/Inspections.asp)

Now we use a 2016 version...

[SFFoodProgram_Complete_Data.zip (2016 Archive)](https://github.com/storydrivendatasets/sf-restaurant-inspections/raw/main/archive/SFFoodProgram_Complete_Data.zip)


### Batch script

```sh
mkdir -p data/collected
curl -Lo data/collected/SFFoodProgram_Complete_Data.zip \
    https://github.com/storydrivendatasets/sf-restaurant-inspections/raw/main/archive/SFFoodProgram_Complete_Data.zip

unzip -d data/collected \
    data/collected/SFFoodProgram_Complete_Data.zip
    
# Archive:  data/collected/SFFoodProgram_Complete_Data.zip
#   inflating: data/collected/violations_plus.csv  
#   inflating: data/collected/businesses_plus.csv  
#   inflating: data/collected/inspections_plus.csv  
```

```sh
mkdir -p data/
rm -f data/compiled.sf-restaurant-inspections.sqlite
sqlite3 data/compiled.sf-restaurant-inspections.sqlite  
```


```sql
.mode csv
.headers on
.import data/collected/violations_plus.csv violations_plus
.import data/collected/businesses_plus.csv businesses_plus
.import data/collected/inspections_plus.csv inspections_plus
```





## Human script




