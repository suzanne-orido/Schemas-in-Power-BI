# Schemas-in-Power-BI

Power BI is a business intelligence and data visualization platform developed by Microsoft. It is used to connect to data from multiple sources, model that data, and produce interactive reports and dashboards for analysis and decision-making.
In the world of business intelligence, data modeling is the "blueprint" that determines whether a Power BI report will be a high-performance engine or a slow, confusing mess.

This article goes into detail on what data models are, why they are important in Power BI, and how to use star schemas and snowflake schemas when designing accurate data models.

What is a data model?
It is a visual representation of how different pieces of information relate to one another within a system.
Think of a data model as a map that defines how your information is stored, connected, and filtered. Without this map, Power BI has to guess how your tables relate, which often leads to errors.

Key components of a Data Model:

Tables: These are the containers for your data. In a good model, these are split into Fact tables (the numbers/metrics) and Dimension tables (the descriptive context).
Fact Tables
They store the measurable business events that an organization wants to analyze. Each row represents an occurrence of something that happened, at a defined level of detail. Facts answer “how much,” “how many,” or “how often.

A fact table contains dimension key columns that relate to dimension tables and numeric measure columns. The dimension key columns determine the dimensionality of a fact table, while the dimension key values determine the granularity of a fact table.

Some key characteristics include:

Large row counts
Numeric, aggregatable columns
Foreign keys linking to dimension tables
One clear grain per table
Dimension Tables
They store the descriptive context used to filter, group, and explain measures in fact tables. They answer “who,” “what,” “where,” and “when.”

Some key characteristics include:

Smaller than fact tables
Mostly categorical or textual attributes
One primary key
Referenced by fact tables through foreign keys
Rarely aggregated
Relationships in Power BI
Relationships in Power BI define how tables interact. They control which rows are included in a calculation. If relationships are wrong, results are wrong, regardless of visuals or DAX.

Common relationship types include:

One-to-many: standard and preferred (dimension → fact) Example: One Product → many Sales rows
One-to-one: rare, use cautiously Example: Employee details are split across two tables
Many-to-many: last resort, high risk Example: Customers belonging to multiple segments
Understanding Star Schema
A star schema is a data modelling structure where a central fact table is directly connected to multiple dimension tables, forming a star-like layout. It is the preferred schema for Power BI and most analytical systems.

Structure

One fact table at the center
Dimension tables radiating outward
Each dimension connects to the fact with a one-to-many relationship
No relationships between dimension tables
How it works
The fact table stores business events. Dimension tables provide descriptive context. Filters flow from dimensions to the fact, ensuring correct aggregation and predictable results.
Usually, fact tables represent the "many" aspect of a relationship, while dimension tables represent the "one" aspect.

 

Understanding Snowflake Schema
A snowflake schema is a data modelling structure in which dimension tables are normalized into multiple related tables rather than being stored as a single, flat dimension. The resulting layout resembles a snowflake rather than a star.

Structure

One central fact table
A dimension connected to the fact
That dimension is further split into sub-dimensions
Multiple joins required to reach descriptive attributes
When they appear in Power BI

When importing data directly from normalized source systems
When modelling is not intentionally redesigned for analytics
Although this reduces redundancy, too much snowflaking is discouraged because:

It increases query complexity.
It requires more joins.
It may slow down performance
Snowflake schemas are storage-efficient. Star schemas are analytics-efficient.

 

The importance of good data modelling
Good data modelling is critical because it determines whether the analysis is correct, fast, and repeatable. Visuals and calculations sit on top of the model; they cannot fix structural errors beneath it.

Accuracy
A good model enforces correct filter flow and aggregation. Measures return the same result regardless of visual layout. Poor models cause double-counting and inconsistent totals.

Performance
Power BI’s engine is optimized for star schemas and simple relationships. Clean models reduce joins, improve compression, and deliver faster query execution. Bad models scale poorly as data grows.

Simplicity
Well-modelled data requires fewer complex DAX expressions. Business logic lives in the model, not in workaround calculations. This reduces error rates and maintenance costs.

Consistency
Metrics are defined once and reused everywhere. Reports built by different authors produce the same numbers. This is essential for organizational trust.

Scalability
Good models support new measures, dimensions, and visuals without redesign. Poor models collapse under change and require rewrites.

Decision quality
Executives act on reported numbers. Incorrect models produce confident but wrong answers. That is operational risk.

In Power BI, data modelling is not preparation work. It is the core analytical task.

In conclusion, data modelling is what makes Power BI reports work correctly. When data is well organized into fact and dimension tables with clear relationships, reports are fast, and numbers are accurate. Poor modelling leads to slow reports and wrong results. Good insights start with a good data model.
