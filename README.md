# Experiment 6 : Sentiment Analysis of Product Reviews Using TextBlob

## Aim
To load product review text, perform sentiment polarity analysis using the `TextBlob` library, classify reviews into **Positive**, **Negative**, or **Neutral** categories, and visualize the overall sentiment distribution using a Matplotlib bar chart.

## Algorithm

1. **Start** the program.
2. **Import Libraries**: Import `TextBlob` from the `textblob` package for Natural Language Processing (NLP) sentiment analysis and `matplotlib.pyplot` as `plt` for bar chart visualization.
3. **Create Review Dataset**: Define a Python list `reviews` containing 10 sample customer product review strings.
4. **Initialize Sentiment Counters**: Set `positive = 0`, `negative = 0`, and `neutral = 0` to track category counts.
5. **Analyze & Classify Each Review**:
   * Iterate through each `review` in `reviews`.
   * Create a `TextBlob(review)` object and extract `polarity = analysis.sentiment.polarity`.
   * Classify the review:
     * If $\text{polarity} > 0.1$, label as `"Positive"` and increment `positive`.
     * Else if $\text{polarity} < -0.1$, label as `"Negative"` and increment `negative`.
     * Else, label as `"Neutral"` and increment `neutral`.
   * Display the review text, rounded polarity score, and assigned sentiment label.
6. **Display Summary Counts**: Print the total count of Positive, Negative, and Neutral reviews.
7. **Visualize Sentiment Distribution**:
   * Plot a bar chart using `plt.bar()` with sentiment categories on the X-axis and review counts on the Y-axis.
   * Add a title, axis labels, and render the chart via `plt.show()`.
8. **Stop** the program.

## Functions and Methods Used

| Category | Function / Attribute | Purpose / Description |
| :--- | :--- | :--- |
| **Sentiment Analysis** | `TextBlob(text)` | Wraps a text string in a TextBlob NLP object for linguistic analysis |
| | `.sentiment.polarity` | Computes a floating-point sentiment polarity score in the range $[-1.0, +1.0]$ |
| **Formatting & Math** | `round(polarity, 2)` | Rounds raw polarity scores to 2 decimal places for clean console output |
| **Visualization (Matplotlib)** | `plt.figure()`, `plt.bar()` | Initializes a figure window and renders a color-coded vertical bar chart |
| | `plt.title()`, `plt.xlabel()`, `plt.ylabel()`, `plt.show()` | Configures chart title, axis labels, and displays the final visualization |

## Program
    # Sentiment Analysis on Product Reviews using TextBlob
    
    from textblob import TextBlob
    import matplotlib.pyplot as plt
    
    # Step 1: Create a list of sample product reviews
    reviews = [
        "This product is excellent and amazing!",
        "I love this product very much.",
        "The quality is good and worth the money.",
        "Very happy with my purchase.",
        "The product works perfectly.",
        "This product is terrible and disappointing.",
        "I hate this product.",
        "The quality is poor and bad.",
        "The product is average.",
        "It is okay, nothing special."
    ]
    
    # Step 2: Initialize counters
    positive = 0
    negative = 0
    neutral = 0
    
    # Step 3: Analyze sentiment for each review
    for review in reviews:
        analysis = TextBlob(review)
        polarity = analysis.sentiment.polarity
    
        if polarity > 0.1:
            sentiment = "Positive"
            positive += 1
        elif polarity < -0.1:
            sentiment = "Negative"
            negative += 1
        else:
            sentiment = "Neutral"
            neutral += 1
    
        print(f"Review: {review}")
        print(f"Polarity: {round(polarity, 2)}")
        print(f"Sentiment: {sentiment}")
        print("-" * 50)
    
    # Step 4: Display summary
    print("\nSentiment Summary")
    print("Positive Reviews:", positive)
    print("Negative Reviews:", negative)
    print("Neutral Reviews:", neutral)
    
    # Step 5: Plot sentiment distribution
    labels = ["Positive", "Negative", "Neutral"]
    counts = [positive, negative, neutral]
    
    plt.figure(figsize=(7, 5))
    plt.bar(labels, counts)
    plt.title("Product Review Sentiment Analysis")
    plt.xlabel("Sentiment")
    plt.ylabel("Number of Reviews")
    plt.show()

## Output
<img width="590" height="510" alt="image" src="https://github.com/user-attachments/assets/62ffe39a-9b41-405b-899e-e22ab0772507" />
<img width="505" height="457" alt="image" src="https://github.com/user-attachments/assets/d985ddc7-1d73-47ac-af26-3cebde2cf3f2" />
<img width="771" height="592" alt="image" src="https://github.com/user-attachments/assets/188928ac-b6e1-4d9b-874c-d6de186a3a53" />


## Result
The program successfully loads a list of sample product reviews, applies `TextBlob` sentiment polarity scoring to classify each review's emotional tone, prints summary counts, and visualizes the overall distribution with a Matplotlib bar chart.
