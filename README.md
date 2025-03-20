# EY-Challenge-2025

This is my work for [The 2025 EY Open Science AI and Data Challenge: Cooling Urban Heat Islands (External Participants)](https://challenge.ey.com/challenges/the-2025-ey-open-science-ai-and-data-challenge-cooling-urban-heat-islands-external-participants)

## Dataset

The training dataset includes timestamps, latitude, longitude, and the corresponding Urban Heat Island (UHI) values. The testing dataset includes only latitude and longitude.

Due to the lack of data, participants can leverage multiple datasets to improve their models. I used the datasets recommended by the challenge:

- European Sentinel-2 optical satellite data (#1)
- Detailed local weather dataset of the Bronx and Manhattan regions on 24 July 2021 (#2)
- Building footprints of the Bronx and Manhattan regions (#3)

## Experiments

I used correlation to determine which features would be selected for my regression model. After several tests, I chose ExtraTreesRegressor as the main algorithm (except for version 1). Additionally, all versions used dataset #1.

For the train-test split, I primarily used an 80-20 ratio.

### Version 1

I used only dataset #1 and RandomForestRegressor.

### Version 2

I used dataset #2 as well. I interpolated the weather features (such as air temperature, humidity, etc.) based on the distance to the Bronx and Manhattan.

### Version 3

I used the approach from version 2 with dataset #3. I counted the number of buildings in a small area, which was then used directly as a feature.

### Version 4

Instead of interpolating the weather features, I compared the distance to the Bronx and Manhattan, then chose the weather features based on the city that was closer.

### Version 5

This approach is the same as version 4, but I used a 90-10 train-test split.

## Result

The results were calculated using R² scoring. Although versions 3 and 2 gave the best and second-best results, respectively, they were not eligible because they violated the rule of not using position-related features. Therefore, my final score is 0.811 with version 5.

This result earned me a certificate for completing the challenge with a score higher than 0.8.


![certificate](https://github.com/user-attachments/assets/68b5513e-3dc6-406d-a942-984105da4bdd)




