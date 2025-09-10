# Investigating Netflix Movies and Guest Stars in The Office

## Project Overview

This project investigates trends in Netflix movie durations and explores the entertainment industry data to understand whether movies are getting shorter over time. The analysis examines Netflix's extensive catalog of movies and TV shows to identify patterns in content duration and genre distribution.

## Background

Netflix, which started in 1997 as a DVD rental service, has grown into the largest entertainment/media company by market capitalization, boasting over 200 million subscribers as of January 2021. With such a vast library of content, analyzing trends in movie durations provides insights into the evolving entertainment landscape.

## Dataset Description

### `netflix_data.csv`
- **Source**: Netflix's content library
- **Size**: 7,781+ entries
- **Columns**:
  - `show_id`: Unique identifier for each show/movie
  - `type`: Content type (Movie or TV Show)
  - `title`: Title of the content
  - `director`: Director name
  - `cast`: Main cast members
  - `country`: Country of origin
  - `date_added`: Date added to Netflix
  - `release_year`: Year the content was released
  - `duration`: Duration in minutes (movies) or seasons (TV shows)
  - `description`: Content description
  - `genre`: Content genre/category

## Key Research Questions

1. **Are movies getting shorter over time?**
2. **What genres are driving duration trends?**
3. **How do different content types affect duration patterns?**
4. **What factors influence movie length in the streaming era?**

## Analysis Methods

### 1. Data Exploration
- Initial data loading and inspection
- Filtering for movies only (excluding TV shows)
- Subsetting relevant columns for analysis

### 2. Visualization Techniques
- **Line plots**: Trend analysis over time
- **Scatter plots**: Duration vs. release year relationships
- **Color-coded plots**: Genre-based analysis

### 3. Statistical Analysis
- Duration trend analysis from 2011-2020
- Genre distribution analysis
- Short movie identification (< 60 minutes)

## Key Findings

### 1. Duration Trends (2011-2020)
The analysis reveals a general decline in average movie durations:
- **2011**: 103 minutes
- **2012**: 101 minutes
- **2013**: 99 minutes
- **2014-2015**: 100 minutes
- **2016-2017**: 95 minutes
- **2018**: 96 minutes
- **2019**: 93 minutes
- **2020**: 90 minutes

### 2. Genre Impact on Duration
Short movies (< 60 minutes) are primarily found in:
- **Children's content**: Often 20-30 minutes
- **Documentaries**: Typically 30-60 minutes
- **Stand-up comedy**: Usually 30-90 minutes
- **Special content**: Holiday specials, shorts

### 3. Content Type Analysis
- **Movies**: Duration measured in minutes
- **TV Shows**: Duration measured in seasons
- **Mixed content**: Requires careful filtering for accurate analysis

## Technical Implementation

### Required Libraries
```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
```

### Key Code Snippets

#### Data Loading and Filtering
```python
# Load Netflix data
netflix_df = pd.read_csv("datasets/netflix_data.csv")

# Filter for movies only
netflix_movies = netflix_df[netflix_df['type'] == "Movie"]

# Select relevant columns
netflix_movies_subset = netflix_movies[["title", "country", "genre", "release_year", "duration"]]
```

#### Visualization
```python
# Create scatter plot
plt.figure(figsize=(12,8))
plt.scatter(release_years, durations, color=colors)
plt.title("Movie Duration by Year of Release")
plt.xlabel("Release Year")
plt.ylabel("Duration (minutes)")
plt.show()
```

#### Genre Analysis
```python
# Color coding for different genres
colors = []
for lab, row in netflix_movies_subset.iterrows():
    if row["genre"] == "Children":
        colors.append("red")
    elif row["genre"] == "Documentaries":
        colors.append("blue")
    elif row["genre"] == "Stand-Up":
        colors.append("green")
    else:
        colors.append("black")
```

## Project Structure
```
Investigating Netflix Movies and Guest Stars in The Office/
├── datasets/
│   ├── netflix_data.csv
│   └── color_data.csv
├── notebook.ipynb
└── README.md
```

## Insights and Implications

### 1. Streaming Era Impact
- Shorter content may be more suitable for mobile viewing
- Binge-watching culture influences content length
- Platform algorithms may favor shorter, more engaging content

### 2. Genre Evolution
- Traditional 90-minute movies are being supplemented by shorter formats
- Documentary and children's content drive shorter average durations
- Stand-up comedy specials have become a significant content category

### 3. Market Trends
- Content creators adapting to streaming preferences
- Increased variety in content lengths
- Platform-specific content optimization

## Limitations and Considerations

1. **Data Scope**: Analysis limited to Netflix's catalog
2. **Temporal Bias**: Newer content may be overrepresented
3. **Genre Classification**: Some content may be miscategorized
4. **Cultural Factors**: Content length varies by country/region

## Future Research Directions

1. **Cross-platform Analysis**: Compare with other streaming services
2. **Audience Engagement**: Correlate duration with viewing patterns
3. **Content Success Metrics**: Link duration to popularity/ratings
4. **Cultural Analysis**: Examine regional differences in content length

## Learning Outcomes

This project demonstrates:
- Data manipulation with pandas
- Data visualization techniques
- Statistical trend analysis
- Entertainment industry data analysis
- Critical thinking about data interpretation

## Conclusion

While the data suggests a general trend toward shorter movies, this is largely driven by the inclusion of non-traditional content types (children's shows, documentaries, stand-up specials) rather than a fundamental change in feature film length. The analysis highlights the importance of considering content type and genre when analyzing entertainment industry trends.

The project showcases how data science can provide insights into cultural and industry changes, while also demonstrating the importance of careful data interpretation and context in drawing meaningful conclusions.

## References

- Netflix content library data
- Entertainment industry market research
- Streaming platform analytics
- Content consumption pattern studies
