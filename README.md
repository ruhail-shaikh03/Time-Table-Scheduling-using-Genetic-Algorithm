# Time-Table-Scheduling-using-Genetic-Algorithm
# Genetic Algorithm for Course Scheduling

## Introduction
Course scheduling is a complex optimization problem faced by educational institutions, requiring the allocation of courses to specific time slots and rooms while satisfying various constraints. This project presents a genetic algorithm (GA) approach to address the course scheduling problem, aiming to efficiently generate schedules that meet the requirements and preferences of students and faculty.

## Problem Description
The course scheduling problem involves assigning courses to time slots and rooms, considering constraints such as room capacity, instructor availability, and avoiding conflicts between courses. The objective is to find an optimal or near-optimal schedule that maximizes resource utilization and minimizes scheduling conflicts.

## Genetic Algorithm Overview
Genetic algorithms are population-based optimization techniques inspired by the principles of natural selection and genetics. They operate on a population of candidate solutions (chromosomes), iteratively evolving the population through selection, crossover, and mutation to produce better solutions over successive generations.

## Data Preparation

### Course Data
- The course data is sourced from real-world university course allocation drives, reflecting the actual courses offered by the institution.
- Each course entry consists of the course name, section, and instructor. These details are essential for identifying unique courses and determining their scheduling requirements.
- The course data is processed from a text file, with each line containing course information in a structured format. The parsing logic extracts relevant details such as course name, section, and instructor.

### Binary Encoding of Courses
- To incorporate course information into the genetic algorithm, each course is encoded into a binary representation.
- The encoding scheme assigns a unique binary code to each course, facilitating its representation within the chromosome.
- Courses are encoded with additional bits to distinguish between theory and lab classes, providing flexibility in scheduling different types of courses.

### Time Slots and Days
- Time slots and corresponding days are essential components of the scheduling problem, defining the temporal availability for course scheduling.
- The provided code includes hardcoded time slots for each day of the week, ensuring uniformity and consistency in scheduling.
- Time slots are encoded into binary representations, enabling their integration into the chromosome structure for efficient scheduling.

### Room Data
- Rooms are fundamental resources required for conducting courses, and their availability and capacity influence the scheduling process.
- The code incorporates a list of available rooms, including both regular classrooms and specialized labs.
- Each room is assigned a unique binary code, allowing it to be represented in the chromosome along with other scheduling parameters.

### Combining Room and Lab Encodings
- To streamline the scheduling process and accommodate both regular classrooms and labs, binary encodings for rooms and labs are combined into a single dictionary.
- This combined encoding simplifies the chromosome representation and ensures that the algorithm can handle different types of course requirements.

## Implementation Details

### Chromosome Representation
Each chromosome represents a potential course schedule and consists of a sequence of course assignments, where each assignment includes room, time slot, and course information encoded as binary strings.

### Fitness Evaluation
The fitness of each chromosome is determined by evaluating its adherence to constraints and objectives, such as minimizing scheduling conflicts and maximizing room utilization. Each chromosome is given a value of 0, which is the best fitness without soft constraints. Every time a constraint is broken, a value of 10 is added to fitness which is worse. Every time a constraint is followed, a value of 1 is added. All hard constraints and soft constraints are implemented.

### Selection
- The `selection(population)` function selects individuals from the population based on their fitness scores.
- Initially, the population is sorted based on the fitness scores.
- The best two individuals (`x1` and `x2`) and the worst two individuals (`x3` and `x4`) are selected based on their positions in the sorted list.
- This approach ensures that the best individuals have a higher chance of being selected for reproduction, while still maintaining diversity by including some less fit individuals.

### Crossover
- The `crossover(x1, x2)` function performs crossover between two parent chromosomes (`x1` and `x2`) to produce two offspring.
- The crossover operation exchanges genetic material between the parents at randomly selected positions (indices).
- 150 indices are randomly selected from each parent chromosome, and the elements at these positions are exchanged.
- This process results in two offspring chromosomes with genetic material from both parents, promoting exploration of the solution space.

### Mutation
- Mutation introduces random changes to individual chromosomes to maintain diversity and explore new solutions.
- The `mutate(x1, lab, room)` function performs mutation on a chromosome (`x1`).
- Two indices in the chromosome are randomly selected and replaced with random values, ensuring that the mutation respects the constraints of the problem (e.g., changing room or time slot).
- Mutation is crucial for escaping local optima and introducing new genetic material into the population, contributing to the genetic diversity necessary for the algorithm's effectiveness.

## Experimental Results
Experiments conducted using real-world course scheduling data demonstrated the performance of the genetic algorithm in generating clash-free schedules. The algorithm successfully produced schedules that met the specified constraints and objectives, demonstrating its effectiveness in tackling the course scheduling problem.

## Conclusion
The genetic algorithm presented in this project offers a promising approach to address the challenging course scheduling problem. By leveraging evolutionary principles and optimization techniques, the algorithm efficiently explores the solution space, generating schedules that optimize resource utilization and satisfy various constraints. Further research and experimentation can refine the algorithm and extend its applicability to diverse scheduling scenarios.
