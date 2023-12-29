# A1 Problem Review

## Info
* **Problem title:** 活跃变量分析和迭代求解器(Live Variable Analysis and Iterative Solver)
* **Problem description:** [中文](https://tai-e.pascal-lab.net/pa1.html), [English](https://tai-e.pascal-lab.net/en/pa1.html)
* **Difficulty:** &#11088;
* **Files touched:** 
	1. LiveVariableAnalysis.java
	2. Solver.java
	3. IterativeSolver.java

## Procedure 
I started by [setting up](https://tai-e.pascal-lab.net/en/intro/setup.html) the environment for the assignment. The part **Run Tai-e as An Application** describes how to run the *pascal.taie.Assignment* as an naive test. To run the tests provided in the **test** folder, you need to find the corresponding java file in it (named as *LiveVarTest.java* in A1), right click and choose 'Run', you don't need to modify run configurations for this file.

It turned out that [Part 3](https://tai-e.pascal-lab.net/en/pa1.html#_3-1-tai-e-classes-you-need-to-know) was the real entry point of this assignment, since the two solver functions in this part give the outer structure of the algorithm, it made sense to start by implementing them. 

1. *initializeBackward* was pretty easy, as it only resembles the first three rows in the algorithm.
2. *newBoundaryFact* and *newInitialFact* were both trivial as well.
3. *doSolveBackward* gave the structure of the while loop, the idea was straightforward. There should be a boolean variable recording any changes in 'IN\[B\]', note that *transferNode* returns a boolean, which aligns with this goal. 
4. *meetInto* was also trivial, but it did surprise me how this function actually applied changes on the variables passed to it due to the **reference semantics** used by Java language.
5. *transferNode* took me the most significant amount of time. The main difficulty was in understanding the *Stmt* class and realizing how to cast *RValue* and *LValue* into *Var* so that they could be used in *Fact*'s functions.

## Reflection
This assignment was overall easy. The live variable analysis algorithm itself was trivial, but understanding the **taie** features took time.
