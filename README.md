---
title: "Bridges_Homework_Skaar"
output: rmarkdown::github_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
library(plyr)
library(dplyr)
library(tidyverse)
library(ggplot2)
library(stringr)
```


```{r bridges}
bridges = read_csv("PA18.txt")

AllegCountyData = bridges %>%  filter(str_detect(COUNTY_CODE_003, "003"))  %>%  select(COUNTY_CODE_003, YEAR_BUILT_027, SUFFICIENCY_RATING) %>%  arrange(desc(YEAR_BUILT_027)) %>% ggplot(aes(x = YEAR_BUILT_027, y = SUFFICIENCY_RATING, color = SUFFICIENCY_RATING)) + geom_point()  + xlim(1938, 1945) + scale_color_gradient(low="red", high="green") + xlab("Year Built") + ylab("Sufficiency Rating")

AllegCountyData

# I chose to look at the most recent bridges data from Pennsylvania because I recently went on a trip there to watch the Badger women's volleyball team play in national championship. While I was there, I learned that Pittsburgh itself is home to over 400 bridges. Genny and I helped each other out during this homework. After loading the data into R, I decided the best way to analyze only bridges in the Pittsburgh area was to filter by county (Alleghany County). After reading more into the data, the sufficiency rating, or quality rating, of these bridges really interested me. I wanted to see the spread in quality of bridges made by year, and decided to specifically focus on the time period during World War II. In 1938 we see a very large spread, from ratings of around 10 to 87. From 1939-1942, we see far less spread in ratings, as well as more bridges being built. 1943 only saw 3 bridges built, but all three have sufficiency ratings between about 65 and 75. I was shocked to see 1944 did not see any bridges built at all, as there are not many years that Pennsylvania built no bridges. Finally in 1945, only three bridges were built again, but their spread was quite significant, ranging from about 23 to 85. Overall, one can conclude from this graph that the end of  World War II lead to a strong decrease in bridges being built, and many bridges built during this time have a high variation in quality ratings today.

```
