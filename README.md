# FWI_ODes
FWI index by ODEs
FIRE WEATHER INDEX (FWI) DYNAMICS PROGRAM 
Overview:
This program calculates the Canadian Fire Weather Index (FWI) using meteorological data. The model applies an iterative method to update fire indices such as Fine Fuel Moisture Code (FFMC), Duff Moisture Code (DMC), and Drought Code (DC) based on daily inputs of temperature, humidity, wind speed, and precipitation. The software is written in R and designed for continuous updating of fire danger indices.
How to Use This Program
1. Prerequisites:
-R: The program requires R to run. You can download R from [CRAN](https://cran.r-project.org/).
  - R Packages: The program uses the `dplyr` package. Install it by running:
  ```R
  install.packages("dplyr")
  ```
2. Prepare Your Meteorological Data:
You need to create a weather data file in the correct format. The file must be a delimited text file (e.g., CSV or TXT) with the following columns:
- Temperature: Daily temperature in degrees Celsius.
- Humidity: Daily relative humidity as a percentage.
- Wind: Daily wind speed in km/h.
- Precipitation: Daily precipitation in mm.
Here’s an example of how the first few rows of the file might look:
Day, Temperature, Humidity, Wind, Precipitation
1, 20, 45, 15, 0
2, 22, 50, 10, 2.5
3, 18, 60, 12, 0
```
File Example: Save this as `input_fire_index.txt`.
3. Define Initial Conditions:
The program requires initial values for several fire danger indices. You can set them as follows:
```R
initial_conditions <- list(FFMC = 85, DMC = 6, DC = 15, ISI = 10, BUI = 8, FWI = 5)
```
You can adjust these initial values based on your specific region or analysis.

4. Run the Program:
To run the program, follow these steps:
1. Copy the provided script into an R file or open it in RStudio.
2. Make sure the path to your input data file is correct:
   ```R
   input_data <- read_input_data("path/to/your/input_fire_index.txt")
   ```
3. Set your initial conditions as mentioned above.
4. Run the following commands to execute the simulation:
   ```R
   total_days <- nrow(input_data)  # Number of days in the dataset
fire_weather_results<-simulate_fire_weather_indices(input_data,total_days, initial_conditions)
   ```
5. View and Save Results:
   After the simulation, you can print and save the results to a CSV file:
   ```R
   print(fire_weather_results)
   write.csv(fire_weather_results, "fire_weather_results.csv", row.names = FALSE)
   ``
5. Example Output:
The output will be a CSV file containing daily fire weather indices. The structure will look like this:
Day, FFMC, DMC, DC, ISI, BUI, FWI
   1,  86.43, 7.12, 15.3, 12.04, 9.11, 6.33
  2, 88.12, 8.02, 16.4, 14.21, 10.15, 7.50
```
Each day will have calculated values for the FFMC, DMC, DC, ISI, BUI, and FWI.
Conclusion:
This program allows users to simulate the evolution of fire danger indices using meteorological data. With the ability to track daily changes in key fire weather indices, the program is valuable for real-time fire danger assessments or historical analysis.
For questions or further assistance, contact Prof. Dr. Hasan TATLI at tatli@comu.edu.tr.

