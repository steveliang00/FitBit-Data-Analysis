# FitBit Fitness Tracker Data Analysis

## Executive Summary
This project analyzes smart device fitness data from 33 FitBit users over a 31-day period (April 12, 2016 - May 12, 2016). The goal is to identify trends in user activity and sleep habits to inform marketing strategies and product features.

**Key Insights:**
*   **Activity Levels:** The average user takes **7,638 steps/day**, which is above the sedentary threshold but falls short of the 10,000-step health guideline. However, activity is unevenly distributed: **32% of days** recorded fewer than 5,000 steps.
*   **Sleep Health:** Users average **6.9 hours** of sleep, but **44% of sleep records** show users getting less than the recommended 7 hours.
*   **Sedentary Behavior:** There is a strong negative correlation between sedentary minutes and sleep duration. Users who spend more time sedentary during the day tend to sleep less, suggesting a potential behavioral link between inactivity and poor sleep hygiene.
*   **Temporal Trends:** Activity peaks consistently between **5 PM and 7 PM**, likely post-work exercise.

---

## Data Source & Methodology
*   **Dataset:** [FitBit Fitness Tracker Data](https://www.kaggle.com/datasets/arashnic/fitbit) (CC0: Public Domain).
*   **Scope:** 33 anonymized users.
*   **Metrics Analyzed:** Daily steps, calories burned, activity intensity (Very/Fairly/Lightly Active, Sedentary), sleep duration, and hourly activity patterns.
*   **Tools:** Python (Pandas, Plotly, Seaborn).

---

## Detailed Analysis

### 1. Physical Activity Profile
The user base exhibits a wide range of activity levels. While the mean daily steps (7,638) suggests a moderately active cohort, the distribution reveals significant opportunities for improvement:
*   **Sedentary Segment:** A significant portion of user-days (32%) fall into the "Sedentary" category (<5,000 steps).
*   **Intensity Breakdown:**
    *   Most active time is spent in "Lightly Active" states (e.g., casual walking).
    *   "Very Active" minutes (vigorous exercise) are skewed, with many users recording near-zero vigorous minutes on many days.

### 2. Hourly Activity Trends
Hourly data reveals clear daily rhythms:
*   **Morning:** Slow rise starting at 6 AM, peaking around 12 PM (lunch).
*   **Afternoon:** A slight dip around 3 PM.
*   **Evening:** The highest activity levels occur between 5 PM and 7 PM.
*   **Night:** Activity drops sharply after 8 PM.

**Strategic Implication:** Notification systems should target the **3 PM dip** to encourage movement or capitalize on the **5-7 PM peak** by suggesting high-intensity workouts when users are already prone to be active.

### 3. Sleep Analysis
Sleep data (available for 24 of the 33 users) highlights a potential health concern:
*   **Duration:** The average sleep time is ~419 minutes (6 hours 59 minutes).
*   **Deficit:** nearly half (44%) of all sleep logs are under 7 hours.
*   **Day of Week:** Sunday reports the highest average sleep, suggesting "catch-up" sleep on weekends.

### 4. The Sedentary-Sleep Connection
A correlation analysis uncovered a notable relationship: **Users with higher sedentary minutes tend to sleep less.**
*   *Statistical Note:* While there is inherent mutual exclusivity (there are only 24 hours in a day, so more time awake/sedentary naturally leaves less time for sleep), the strength of the relationship ($R^2 \approx 0.36$) suggests that lifestyle factors associated with high sedentary time may negatively impact sleep prioritization.

---

## Recommendations for Product Strategy

Based on the analysis, the following strategies are recommended to improve user health outcomes and engagement:

1.  **"Sleep Hygiene" Campaign:**
    *   Target the 44% of users getting insufficient sleep.
    *   Feature: "Wind-down" notifications 30 minutes before the user's typical bedtime.
    *   Insight: Emphasize the link between reducing sedentary time and improving sleep.

2.  **Combating Sedentary Behavior:**
    *   Target the 32% of "low step" days.
    *   Feature: Hourly "Step Snacking" reminders. If a user hasn't moved 250 steps in an hour (especially during the 9 AM - 5 PM window), trigger a gentle nudge.

3.  **Weekend Warrior vs. Consistent Walker:**
    *   Segment users based on their weekly consistency. Users who only peak on weekends need different motivation (recovery, injury prevention) compared to daily walkers (intensity increase).

---

## Technical Revisit & Future Improvements
*Retrospective on the initial analysis code (fitbit_analysis.ipynb)*

To further mature this analysis, the following technical improvements are recommended:
1.  **User-Level Aggregation:** The current analysis often treats every day as an independent data point. Future analysis should account for **repeated measures** (within-subject variance) to avoid pseudoreplication.
2.  **Weekend vs. Weekday Split:** Activity patterns likely differ significantly between workdays and weekends. Splitting the analysis could refine the timing of notifications.
3.  **Non-Linear Relationships:** The relationship between activity and sleep might not be linear. Exploring threshold effects (e.g., "Does >10,000 steps guarantee better sleep?") could yield clearer goals.
4.  **Data Completeness:** Weight and Heart Rate data were present but under-utilized due to missing values or complexity. Imputation or focused analysis on the subset of users with complete data could provide deeper physiological insights.
