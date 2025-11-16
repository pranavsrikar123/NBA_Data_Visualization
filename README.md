# NBA Team Performance Analysis: What Wins Championships?

This project is a collection of data analyses and visualizations exploring the statistical profile of NBA teams, with a focus on identifying what metrics correlate most strongly with winning and winning championships.

Using NBA game data from 1980 to 2023, this analysis cleans and aggregates team-level statistics for each season to answer several key questions:
* Do "defense wins championships"?
* Is it better to take *more* shots or *better* shots?
* Which offensive stats have the strongest correlation with a high win percentage?
* What does the statistical "fingerprint" of a championship-caliber team look like?

## Key Analyses and Visualizations

### 1. The Championship Quadrant (Offense vs. Defense)

This is the central analysis of the project. It calculates a weighted **Offensive Rating** and **Defensive Rating** for every team in every season since 1985. The results are plotted on a "Championship Quadrant" chart.

* **Plot:** A Plotly scatter plot with all team-seasons as faint gray dots and championship-winning teams highlighted as gold stars.
* **Quadrants:** The plot is divided into four quadrants based on the league-average offense and defense for that season:
    * **Championship Zone** (High Offense, High Defense)
    * **Grit & Grind** (Low Offense, High Defense)
    * **Offense Only** (High Offense, Low Defense)
    * **Lottery Bound** (Low Offense, Low Defense)
* **Key Finding:** A vast majority of NBA champions fall into the top-right "Championship Zone," demonstrating that while a great offense is important, an elite, above-average defense is a non-negotiable requirement for winning a title.

### 2. Offensive Efficiency: More Shots vs. Better Shots?

This analysis explores the relationship between shot quantity (Field Goal Attempts) and shot quality (Field Goal Percentage) and how they relate to winning.

* **Plot:** A scatter plot of Field Goal Attempts per Game (FGA/G) vs. Field Goal Percentage (FG%).
* **Color:** Points are colored by Win Percentage.
* **Key Finding:** The plot is divided into quadrants based on the median FGA and FG%. The analysis shows that teams in the "High FG%, Low FGA" quadrant (quality over quantity) have a higher average win percentage than teams in the "Low FG%, High FGA" quadrant.

### 3. Profiling Top Teams: The Contender Spider Chart

This visualization creates a statistical "fingerprint" for the top contenders in a given season by comparing them to the league average across multiple categories.

* **Plot:** A polar (spider) chart showing the % deviation from the league average for key metrics like:
    * Offensive & Defensive Efficiency
    * Shooting % (FG%, 3P%, FT%)
    * Defensive Impact (Steals, Blocks)
    * Rebounding
* **Use Case:** The chart profiles the champion (e.g., GSW in 2022) against other top teams, identifying their unique strengths and weaknesses. It also includes a "recommendation" for the best-fit team for a hypothetical free agent (nicknamed "DeBron").

### 4. Which Offensive Stats Correlate Most with Winning?

To determine which stats matter most, this analysis plots Win Percentage against seven different offensive metrics.

* **Plots:** A grid of scatter plots and binned bar charts showing the relationship between Win % and:
    1.  Average Points per Game
    2.  Field Goal %
    3.  3-Point %
    4.  Free Throw %
    5.  Average Assists
    6.  Average Offensive Rebounds
    7.  Average Turnovers
* **Key Finding:** **Average Points per Game** and **Field Goal Percentage** show the strongest positive correlations with winning, while **Average Turnovers** has the strongest negative correlation.

## Data

This project relies on several CSV files, which are assumed to be in a `csv/` sub-directory:
* `game.csv` (The primary file for most analyses)
* `line_score.csv`
* `team_details.csv`
* `team_history.csv`
* `final_team_win_rate.csv`

The script in Cell 2 also generates an intermediate file, `csv/team_offense_vs_wins.csv`.

## How to Run

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
    cd your-repo-name
    ```

2.  **Create a virtual environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3.  **Install the required libraries:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Add the data:**
    * Create a folder named `csv` in the root of the project.
    * Place all the required CSV files (listed above) into the `csv/` folder.
    * *Note: The notebook is not perfectly consistent with paths. You may need to adjust `pd.read_csv("game.csv")` in Cell 1 to `pd.read_csv("csv/game.csv")`.*

5.  **Run the Jupyter Notebook:**
    ```bash
    jupyter notebook "Final Project.ipynb"
    ```
    (You will need to rename the provided `.html` file back to `.ipynb` or copy the code into a new notebook.)
