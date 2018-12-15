# Optimizing Ambulance Allocation in the City of San Diego
Time series analysis of ambulance dispatches in the City of San Diego. Models include Prophet, ARIMA, and LSTM with recurrent neuron network.

## Dataset file
```
raw_dispatch_merged_with_comments.csv
```

## Additional Features Created from the dataset

* `New_Zone` - Map the incident data before Sep 2015 to the new divisions created on Oct 2015, labeled 0~7 as Zone 1 to Zone 8.
* `Zipcode` - Geo-decoded addresses from lat-long locations of each incident.
* `Mission_Type` - 0: Ambulance canceled, 1: Cleared at scene, 2: Transported to destination.

## Dataset related files:

* `incident_zipcode_newzone.csv` - `Master_Incident_Number` with `Zipcode`, `New_Zone`, `Mission_Type`
* `geoloc_coord.csv`: Address of the 94,307 distince lat-long points in the dataset with address resolved through geopy by OpenStreetMap API.
* `amb_hour.csv`: Ambulance unit hours dataset, with scheduled and actual hours claimed, the number of calls are also listed.

## Jupyter Notebook files:

* `geoloc_zipcode.ipynb`: Heatmap visualization of 911 calls by zip codes.
* `geoloc_api.ipynb`: Read `geoloc_coord.csv` , send the location through geopy to OpenStreetMap, and write the resolved address back to geoloc_coord.csvas an additional column
* `zones_types.ipynb`: Read `raw_dispatch_merged_with_comments.csv` , identify the `New_Zone` for incidents before September 2015, and identify the `Mission_Type``. Write the results into incident_zipcode_newzone.csv`.
* `forecast_prophet.ipynb`: Forecasts of the 24 time series by Prophet.
* `forecast_uhu.ipynb`: Forecast the unit hour time series in `amb_hour.csv` using Prophet, ARIMA, and LSTM (RNN) with performance comparison.
* `forecast_(XY).ipynb`: Forecast on selected series in the 24 time series by districts and mission type in `incident_zipcode_newzone.csv` using Prophet, ARIMA, and LSTM (RNN) with performance comparison. Here, X is the fire district values from 1-8, Y is the mission type from 1-3 (1: Cancelled, 2: Clear-at-scene, 3: Transported)


