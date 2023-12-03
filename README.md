# prompt-engineering

## Specific instruction

- Provide as much specificity as possible for GPTs looking for information from a given context
- Don't just end with a word or sentence, give a detailed explanation of what the word or sentence refers to

## Clear instruction

- Garbage in, garbage out
- Remove offensive content

## Provide context

- Don't just write a specific prompt, give your reasons and intentions for writing it
- Providing background or reference information can also help you control the outcome

## Formatting Structures

- Formatting refers to ensuring that prompts have a certain pattern or structure when written
- Users can direct GPT to generate a specific type of text by explicitly telling it what format or form they want

## Maintain consistency

- Try the prompts you've created multiple times and under different conditions to see if they still maintain a consistent format
- Due to the nature of probability models, the content of the response will not always be the same, but you should continue to verify that you are not producing results that are completely outside of the intent of the prompt creator

## 12 techniques

### Few shot

- Technique for adding examples to AI model
- The most common In-Context learning Methods
- Shows weakness when dealing with complex reasoning tasks

### Role playing

- Assign specific roles to AI model
- Drives to professional and relevant responses
- But there is no guarantee that the result is always true
- Better effect if you create a name for the role

```shell
From now on, you must play the role of (role) and give all answers as if (role) were doing it.
Your name is (name of role). 
I will ask (role) a question called '(question)'.
```

### Markdown

- Control the results by using markdown in reverse
- This is a method of dividing paragraphs or emphasizing specific phrases and words using Markdown
- Since GPT recognizes the given sentence in a structured way, better results can be expected

```shell
#test1
##test2
- first story: **bold**
- second story: *tilt*
```

### Fukatsu

- Technique to create a template by suggesting output format and constraints
- This method uses Markdown’s paragraph separator (#)
- A template that uses four sections: statements, constraints, input statements, and output statements

```shell
#Command
You are (role).
Please output the best (topic of the article) based on the constraints and input statements below.

#Constraints
(explain constraints)

#Input
(question or instruct)

#Output 
```

## Formatting

- A technique to specify a specific output format based on the Fukatsu prompt
- This method uses Markdown’s paragraph separator (#)
- If you use square brackets ([]), the GPT model fills in the contents inside the square brackets and outputs them
- Very useful

```shell
#Command
You are (role).
Please output the best (topic of the article) based on the constraints and input statements below.

#Constraints
(explain constraints)

#Input
(question or instruct)

#Output
(specify output format using square brackets) 
```

## Shunsuke

- A template technique that specifies materials in the form of ‘variables’ and divides the order of work into stages
- It is not structured to be executed like an actual program

```shell
#Content detail
This content is (topic).

#Variables
[var1] = val1
[var2] = val2
[var3] = val3

#Command
Please write about (first requested task) based on [var2] for [C1] = [var1].
Please write about (second requested task) based on [C2] = [C1].

#Execute
$ run [C1] [C2]
```

## Q&A

- A technique to construct Few Shots in the form of questions and answers
- Present questions in advance as if the GPT model answered them on its own
- This is a technique that can control the constraints of the GPT model

```shell
Q: (users question)
A: (assuming it is an GPTs answer, write answer)
```

## Continuation

- A technique that presents part of a sentence and guides GPT to generate the next sentence
- This is a method of presenting part of a sentence and printing it out sequentially
- There are various derivation methods that utilize the characteristics of the GPT model well

```shell
#Continue writing
(present the previous sentence)
```

## Chain of thought

- A technique that induces more accurate results by first presenting a ‘detailed result derivation process’ to the language model
- The accuracy of the results is increased through logical reasoning, but the correct answer is not always output

```shell
(Present the reasoning process in detail, or enter 'Please think step by step')

Please answer according to this reasoning process.
```

## Multi-persona

- A technique for organizing results by encouraging virtual characters to discuss each other
- Able to derive creative discussions and stories about various scenarios or situations
- Proven to perform well in interactive board games and puzzle problem solving

```shell
(enter the topic and background to be discussed)

What will the story be like?

<settings>
1. (name of character 1): (persona characteristics and opinions)
1. (name of character 2): (persona characteristics and opinions)
...(set as many characters as you want)

(name of character 1): (a character's First comment)
```

## Hallucination induction

- A technique that reverses the hallucination phenomenon
- It can be possible to break away from realistic constraints and create new scenarios and more creative results
- There are various induction methods

```shell
Use your imagination and make the request below.

(enter your question)
```

## ReAct

- A technique that induces inference and execution in an AI model by utilizing an external search function
- Techniques to minimize hallucination
- A separate external plugin or processing by the development department is required

```shell
Answer the following questions as best as you can.
You can access search.

Use the following format.

Question: Input questions that need to be answered.
Thought: Always think what to do.
Action: Search specifically.
Action Input: Write keywords to search.
Observation: Summarize the result of the action

(...repeat at least 2 times)

Thought: I know the final answer.
Fianl answer: Show the final answer of Question.

start!

(write a question)
```