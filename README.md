# ANA-515-Assignment-1

**---
title: "ANA 515 Assignment 1"
author: "Sree Veereshwar Kumar Vallem"
date: "6/5/2022"
output:
  word_document: default
  pdf_document: default
  html_document: default
---


```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

```{r gun_deaths, include=FALSE}
url <- "https://raw.githubusercontent.com/fivethirtyeight/guns-data/master/full_data.csv"
gun_deaths <- read.csv(url)
dim(gun_deaths)
```

```{r youth, include=FALSE}
library(tidyverse)
library(knitr)
library(bslib)
youth <- filter (gun_deaths, age <=65)
summary (youth)
```

```{r, include=FALSE}
View(youth)
totaldeaths <- nrow(gun_deaths)
sixtyfiveandolder <- nrow(gun_deaths)-(nrow(youth))
```
We have data of about `r totaldeaths` individuals killed by guns. Only `r sixtyfiveandolder` are older than 65. The distribution of the remainder is shown below:


```{r youth_dist, echo=FALSE}
youth %>% ggplot(aes(age)) +geom_freqpoly(binwidth = 1)
```

```{r race-dist, echo=FALSE}
youth %>% ggplot(aes(fct_infreq(race)%>% fct_rev()))+geom_bar() + coord_flip() + labs(x="Victims race")
```
**
