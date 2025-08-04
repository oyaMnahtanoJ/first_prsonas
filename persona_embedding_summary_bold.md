# Persona Embedding Overview

## Dataset Summary

| Metric | CDP | Amazon | Yelp |
|--------|-----|--------|------|
| Total interactions | 11,932,754 | 13,926,252 | 370,120 |
| Number of unique users | 1,204,164 | 7,948,368 | 251,267 |
| Number of unique items | 31,097 | 286,752 | 14,292 |
| Average interactions per user | 9.91 | 1.75 | 1.47 |

## Amazon Persona Embedding Schema

| Feature | Description | Based on column(s) |
|---------|-------------|---------------------|
| user_id | Unique user identifier | user_id |
| user_rating_group | critical / mixed / positive reviewer | rating (per user mean) |
| product_rating_group | low-rated / mid-rated / high-rated | average_rating |
| product_popularity_group | niche / common / popular items | product_number_of_ratings |
| loyalty_group | narrow / varied / broad | parent_asin (number of unique items) |
| price_sensitivity_group | budget / moderately / premium | price |
| brand_diversity_group | focused / balanced / diverse | brand (number of unique brands) |
| category | Top product category (tokenised) | categories (first category) |

User X is a **critical / mixed / positive** reviewer who tends to buy **low-rated / mid-rated / high-rated** and **niche / common / popular** items. They show a **narrow / varied / broad** purchasing pattern and prefer **budget / moderately / premium** priced products. They exhibit a **focused / balanced / diverse** brand preference. Their interests lie primarily in the category of **category**.

**Example:**

User **AE2WYNQPBMS67OHFWV63NI4MSJEA** is a **mixed** reviewer who tends to buy **low-rated** and **popular items**. They show a **varied** purchasing pattern and prefer **premium** priced products. They exhibit a **balanced** brand preference. Their interests lie primarily in the category of **Hair Care**.

## CDP Persona Embedding Schema

| Feature | Description | Based on column(s) |
|---------|-------------|---------------------|
| user_id | Unique user identifier | user_id |
| loyalty_group | narrow / varied / broad | product_id (number of unique items) |
| price_sensitivity_group | budget / moderately / premium | price |
| brand_diversity_group | focused / balanced / diverse | brand (number of unique brands) |
| session_length_group | short / intermediately / long | session_length or inferred timestamps |
| weekend_activity_group | weekday / mixed / weekend | timestamp (weekday) |
| review_volume_group | few / handful / many | number of reviews per user |

User X shows a **narrow / varied / broad** purchasing pattern and prefers **budget / moderately / premium** priced products. Their brand preference is **focused / balanced / diverse**, sessions are generally **short / intermediately / long** timed, and their activity is skewed toward the **weekday / mixed / weekend**. They post **few / handful / many** reviews overall.

**Example:**

User **258927307** shows a **broad** purchasing pattern and prefers **premium** priced products. Their brand preference is **focused**, sessions are generally **short** timed, and their activity is skewed toward the **weekday**. They post **many** reviews overall.

## Yelp Persona Embedding Schema

| Column | Description | Based on column(s) |
|--------|-------------|---------------------|
| user_id | Unique user identifier | user_id |
| user_rating_group | critical / mixed / positive | user_average_rating |
| business_rating_group | low-rated / mid-rated / high-rated | average_rating |
| business_popularity_group | niche / common / popular | review_count |
| loyalty_group | narrow / varied / broad | business_id (unique count per user) |
| time_of_day | morning / afternoon / evening | time (parsed hour) |
| weekend_activity_group | weekday / mixed / weekend | weekday |
| review_count_group | few / handful / many reviews | user_reviews |
| category | Top category | category |

User X is a **critical / mixed / positive** reviewer who typically visits **low-rated / mid-rated / high-rated** and **niche / common / popular** businesses. They exhibit a **narrow / varied / broad** visitation pattern, favour **morning / afternoon / evening** outings, are mostly **weekday / mixed / weekend** active, write **few / handful / many** reviews, and tend to explore businesses in **category**.

**Example:**

User **Jt3GylPuH64uA3zTdbMdCg** is a **critical** reviewer who typically visits **low-rated** and **common businesses**. They exhibit a **varied** visitation pattern, favour **afternoon** outings, are mostly **weekday** active, write a **handful** of reviews, and tend to explore businesses in **Hair Salons**.
