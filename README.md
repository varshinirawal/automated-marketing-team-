# Sephora Consumer Analysis Intelligence

A data analysis and NLP project that explores Sephora product and customer-review data to understand product performance, customer sentiment, brand ratings, and skincare preferences.

## Project Overview

This project combines product information with customer reviews to create a unified analysis dataset. It performs data cleaning, sentiment labeling, exploratory data analysis, and prepares product profiles for semantic search using sentence embeddings.

The notebook analyzes:
- Product ratings and recommendation rates
- Customer sentiment from reviews
- Brand and product-category performance
- Skin type-based rating patterns
- Product ingredients, highlights, and customer feedback
- Semantic product representations using embeddings

## Features

- Loads and combines multiple review CSV files
- Cleans missing values and removes unnecessary columns
- Creates weak sentiment labels based on review ratings
- Combines and cleans review titles and review text
- Tokenizes, removes stopwords, and lemmatizes review text
- Merges cleaned review data with skincare product data
- Performs exploratory analysis by brand, skin type, and category
- Generates product-intelligence documents containing product details and sample reviews
- Uses `all-MiniLM-L6-v2` from Sentence Transformers to create product embeddings

## Dataset

The project expects the following input files:

- `product_info.csv`
- `reviews_*.csv`
- `product_info_skincare.csv`

The notebook combines all review files matching the `reviews_*.csv` pattern into one DataFrame.

## Main Steps

1. **Data loading**
   - Load product and review datasets
   - Combine multiple review CSV files

2. **Data cleaning**
   - Remove records without review text
   - Fill missing skin tone and skin type values with `unknown`
   - Fill missing review titles with empty strings
   - Impute recommendation and helpfulness values by product
   - Remove unused columns

3. **Sentiment labeling**
   - Rating greater than 3: positive
   - Rating equal to 3: neutral
   - Rating less than 3: negative

4. **Text preprocessing**
   - Lowercase text
   - Remove URLs and non-alphabet characters
   - Tokenize text
   - Remove stopwords while preserving sentiment-related words
   - Apply lemmatization

5. **Data integration**
   - Merge cleaned reviews with skincare product information using `product_id`
   - Rename duplicate rating columns to `product_rating` and `review_rating`

6. **Exploratory analysis**
   - Average review rating by brand
   - Average review rating by skin type
   - Average review rating by product category
   - Sentiment distribution
   - Recommendation analysis

7. **Product intelligence**
   - Group reviews by product
   - Calculate average rating and recommendation rate
   - Collect ingredients, highlights, and sample reviews
   - Create a structured profile for each product

8. **Embeddings**
   - Load `all-MiniLM-L6-v2`
   - Convert product-intelligence documents into 384-dimensional embeddings

## Technologies Used

- Python
- Pandas
- NumPy
- NLTK
- Regex
- Sentence Transformers
- Hugging Face Transformers
- PyTorch
- Jupyter Notebook

## Installation

Install the required packages:

```bash
pip install pandas numpy nltk sentence-transformers
```

Download the required NLTK resources:

```python
import nltk
nltk.download("punkt")
nltk.download("punkt_tab")
nltk.download("stopwords")
nltk.download("wordnet")
```

## How to Run

1. Place the required CSV files in the project folder.
2. Open `sephora_cousumer_analysis_intelligence.ipynb` in Jupyter Notebook.
3. Run the cells in order.
4. The notebook generates:
   - `cleaned_reviews.csv`
   - `clean_product_skincare.csv`
   - `master.csv`
   - Product intelligence documents
   - Product embeddings

## Output Files

| File | Description |
|---|---|
| `cleaned_reviews.csv` | Cleaned and preprocessed customer-review dataset |
| `clean_product_skincare.csv` | Cleaned skincare product dataset |
| `master.csv` | Merged product and review dataset |
| Product intelligence documents | Structured product profiles with ratings, ingredients, highlights, and reviews |
| Embeddings | Vector representations for semantic product search |

## Key Insights

- Most reviews are positive, based on the rating-based sentiment labels.
- The project identifies average ratings across brands, skin types, and product categories.
- Product profiles combine structured product data with real customer feedback.
- Sentence embeddings enable future semantic search, product recommendations, and review-based insights.

## Future Improvements

- Build an interactive Streamlit dashboard
- Add semantic product search
- Create a recommendation system based on customer preferences
- Use transformer-based sentiment analysis instead of rating-based weak labels
- Add visualizations for ratings, sentiment, and brand performance
- Deploy the product intelligence system as a web application

## License

This project is for educational and analytical purposes.
