# Ex.No. 7 – Develop a Prompt-Based Application for Personal Needs

## Date: 05/09/2026
## Register No.: 212223220106

# Aim

To develop a prompt-based personal productivity application using ChatGPT that can organize daily tasks, manage reminders, provide useful suggestions, and answer general queries by progressively improving prompts from simple to advanced designs.



# AI Tools Required

- ChatGPT
- Python
- Any suitable IDE / Code Editor
- Command Prompt / Terminal
- Optional: Google Gemini or other Large Language Model tools



# 1. Introduction

A prompt-based application uses carefully designed natural-language instructions to control the behaviour of a Large Language Model (LLM).

In this experiment, a **Personal Productivity Assistant** is designed to help users manage their daily activities. The application accepts natural-language instructions and generates useful responses based on the user's requirements.

The assistant is designed to support:

- Daily task management
- Reminder management
- Task prioritization
- Daily planning
- General queries
- Productivity suggestions
- Wellness suggestions
- Preference-based responses

The experiment demonstrates how prompt engineering can transform a simple chatbot into a practical personal productivity application.


# 2. Application Title

## Personal Productivity Assistant

The proposed application acts as an intelligent assistant that understands natural-language instructions and helps users organize their academic and personal activities.


# 3. Problem Statement

Students and working users often manage multiple activities such as assignments, project work, examinations, meetings, deadlines and personal tasks.

A conventional task list requires users to manually enter and organize every activity.

The proposed prompt-based application uses an LLM to understand natural-language requests such as:

> "I have to complete my project report by Friday and prepare for tomorrow's exam."

The assistant identifies the tasks, determines their priority, organizes them and provides an actionable plan.



# 4. Base Prompt – Simple Prompt

The first version uses a simple prompt:

> **"You are a personal productivity assistant. Help me manage my daily tasks and answer my questions."**

### Example User Input

> "I have to complete my project report and study for tomorrow's exam."

### Example Output

```text
Today's Tasks:

1. Complete project report
2. Study for tomorrow's exam

Suggested order:
1. Study for tomorrow's exam
2. Complete the project report
```

### Observation

The simple prompt provides a basic response but does not define:

- Priority rules
- Output format
- Deadline handling
- Scheduling behaviour
- User preferences
- Wellness recommendations


# 5. Improved Prompt – Role-Based Prompt

### Prompt

> **"Act as an intelligent personal productivity assistant for a college student. Help organize academic, project and personal tasks. Understand natural-language requests, identify deadlines, prioritize tasks, suggest schedules, provide general productivity suggestions and answer questions clearly. Always provide practical and actionable recommendations."**

### Example User Input

> "I need to complete my project documentation by Friday and prepare for an exam tomorrow."

### Example Output

```text
Priority Tasks:

1. Prepare for tomorrow's exam
   Priority: HIGH
   Deadline: Tomorrow

2. Complete project documentation
   Priority: MEDIUM
   Deadline: Friday

Suggested Plan:

Today:
- Focus on exam preparation.
- Spend a short session reviewing project documentation.

Tomorrow:
- Complete the remaining project documentation.

Friday:
- Final review and submission.
```

### Observation

The role-based prompt produces a more useful response because the AI understands the user's context as a student.


# 6. Advanced Prompt – Structured Prompt

### Prompt

> **"You are a personal productivity assistant designed for a college student. Process every user request using the following workflow:**
>
> 1. Identify tasks and activities.
> 2. Extract deadlines and time requirements.
> 3. Classify each task as High, Medium or Low priority.
> 4. Identify dependencies between tasks.
> 5. Suggest an achievable schedule.
> 6. Identify possible conflicts.
> 7. Provide productivity or wellness suggestions when appropriate.
> 8. Present the final response using clear headings and bullet points.
>
> Do not invent deadlines or appointments that the user has not provided. If important information is missing, clearly state the assumption or ask for clarification."

### Example User Input

> "I have an internal exam tomorrow morning, a project review on Thursday and I need to submit my assignment on Friday."

### Example Output

```text
PERSONAL PRODUCTIVITY PLAN

HIGH PRIORITY
1. Internal Exam
   Deadline: Tomorrow morning

MEDIUM PRIORITY
2. Project Review
   Deadline: Thursday

3. Assignment Submission
   Deadline: Friday

RECOMMENDED PLAN

Today:
- Prepare for the internal exam.
- Complete important revision topics.

Tomorrow:
- Attend the examination.
- Begin preparing for the project review.

Thursday:
- Complete project review preparation.

Friday:
- Finalize and submit the assignment.

PRODUCTIVITY TIP
Avoid starting multiple major tasks simultaneously.
Focus on the nearest deadline first.
```

# 7. Advanced Prompt – Preference-Aware Assistant

### Prompt

> **"Act as my personal productivity assistant. Your main goal is to help me manage academic and personal activities efficiently.**
>
> **User preferences:**
> - Prefer simple and realistic schedules.
> - Give high-priority academic deadlines more importance.
> - Avoid creating overly packed schedules.
> - Divide large tasks into smaller steps.
> - Provide concise responses.
> - Include short breaks when planning long study sessions.
>
> For every request:
> 1. Understand the user's task.
> 2. Identify deadlines.
> 3. Determine priority.
> 4. Break complex tasks into manageable steps.
> 5. Suggest a realistic schedule.
> 6. Mention conflicts or missing information.
> 7. Adapt the response according to the stated preferences.
>
> Never claim that a reminder or event has actually been scheduled unless a scheduling system is connected."

### Example User Input

> "I have to finish my final-year project presentation, study for an exam and complete my assignment this week."

### Example Output

```text
YOUR PRIORITY PLAN

1. Exam Preparation – HIGH
2. Project Presentation – HIGH
3. Assignment – MEDIUM

TODAY
- 1 hour: Exam preparation
- 30 minutes: Break
- 1 hour: Project presentation
- 30 minutes: Assignment

TOMORROW
- Continue exam preparation.
- Prepare presentation slides.
- Complete one section of the assignment.

RECOMMENDATION
Focus on the exam first because it has the nearest academic deadline. 
Break the project and assignment into smaller tasks rather than completing everything at once.
```


# 8. Application Workflow

```text
                USER
                  │
                  ▼
       Natural Language Input
                  │
                  ▼
          Prompt Processing
                  │
                  ▼
          Large Language Model
             (ChatGPT)
                  │
        ┌─────────┼─────────┐
        ▼         ▼         ▼
      Tasks    Schedule   Queries
        │         │         │
        ▼         ▼         ▼
    Priority   Conflicts  Answers
        │         │         │
        └─────────┼─────────┘
                  ▼
          Productivity Plan
                  │
                  ▼
            User Response
```


# 9. Simulated Command-Line Application

A simple Python interface can be used to simulate the prompt-based application.

```python
def productivity_assistant(user_input):
    prompt = f"""
    You are a personal productivity assistant.

    Help the user:
    - organize daily tasks
    - identify priorities
    - understand deadlines
    - create practical schedules
    - provide general productivity suggestions

    User request:
    {user_input}

    Provide a clear and actionable response.
    """

    return prompt


print("=== Personal Productivity Assistant ===")

while True:
    user_input = input("\nYou: ")

    if user_input.lower() in ["exit", "quit"]:
        print("Assistant: Goodbye!")
        break

    prompt = productivity_assistant(user_input)

    print("\nGenerated Prompt:")
    print(prompt)
```

This prototype demonstrates how user input can be converted into a structured prompt before being sent to an LLM.


# 10. Example Interactions

## Interaction 1 – Task Management

### User

> "I need to complete my project report today."

### Assistant

```text
Task: Complete project report
Priority: HIGH
Deadline: Today

Suggested approach:
1. Complete pending sections.
2. Review the document.
3. Check formatting.
4. Save the final version.
```


## Interaction 2 – Scheduling

### User

> "I have an exam tomorrow and a project meeting in the evening."

### Assistant

```text
Schedule:

Morning:
- Exam preparation / examination

Afternoon:
- Rest and review project requirements

Evening:
- Project meeting

Priority:
1. Exam
2. Project meeting
```


## Interaction 3 – Wellness Suggestion

### User

> "I have been studying for several hours."

### Assistant

```text
Suggested Break:

- Take a short break.
- Drink water.
- Stretch or walk for a few minutes.
- Avoid continuous screen usage.
- Resume studying after the break.
```


## Interaction 4 – General Query

### User

> "Explain cloud computing in simple words."

### Assistant

```text
Cloud computing means using computing resources such as
servers, storage and software over the Internet instead of
running everything directly on your own computer.

Example:
Google Drive allows users to store files online and access
them from different devices.
```


# 11. Prompt Progression

| Prompt Version | Main Feature | Output Quality |
|---|---|---|
| Simple Prompt | Basic assistant role | Basic |
| Role-Based Prompt | Student context | Good |
| Structured Prompt | Defined workflow | Very Good |
| Preference-Aware Prompt | User preferences + constraints | Excellent |

The progression demonstrates that adding **context, structure, constraints and preferences** improves the usefulness of the LLM response.


# 12. Evaluation Table

| Parameter | Simple Prompt | Role-Based | Structured | Preference-Aware |
|---|---:|---:|---:|---:|
| Relevance | Medium | High | Very High | Very High |
| Clarity | Medium | High | Very High | Very High |
| Personalization | Low | Medium | High | Excellent |
| Task Organization | Low | Good | Excellent | Excellent |
| Scheduling | Low | Good | Excellent | Excellent |
| Adaptability | Low | Medium | High | Excellent |
| Practical Usefulness | Medium | High | Excellent | Excellent |



# 13. Advantages

1. Natural-language interaction.
2. Easy task management.
3. Personalized recommendations.
4. Faster daily planning.
5. Helps organize academic activities.
6. Can provide productivity suggestions.
7. Can adapt responses to user preferences.
8. Reduces manual task organization.
9. Supports multiple types of queries.
10. Can be extended with external tools and APIs.

# 14. Limitations

1. An LLM may misunderstand ambiguous instructions.
2. AI-generated schedules may not always be realistic.
3. Actual reminders require integration with a calendar or notification system.
4. AI should not claim that an action was completed when it was not.
5. User preferences must be explicitly provided or stored through an appropriate memory mechanism.
6. AI-generated information should be verified when accuracy is important.
7. The basic prototype does not provide persistent task storage.


# 15. Future Enhancements

The prototype can be extended with:

- Google Calendar integration
- Automated reminders
- Task database
- Mobile application
- Voice input
- Speech output
- Persistent user preferences
- Email integration
- To-do list synchronization
- AI-based deadline prediction
- Automatic task prioritization
- Productivity analytics
- Notification system


# 16. Key Observations

1. Simple prompts can perform basic tasks but provide limited personalization.
2. Role-based prompts improve contextual understanding.
3. Structured prompts produce more consistent and organized responses.
4. Preference-aware prompts provide highly personalized results.
5. Clear constraints reduce incorrect assumptions.
6. Prompt engineering can convert a general-purpose LLM into a specialized application.
7. Natural-language interaction makes the application easy to use.
8. External integrations are required for actual reminders and calendar operations.

# 17. Final Prompt

> **"Act as my personal productivity assistant for academic and personal activities. Help me organize tasks, identify priorities, understand deadlines, create realistic schedules, suggest short productivity and wellness breaks, and answer general questions.**
>
> **For every request:**
>
> 1. Identify all tasks and activities.
> 2. Extract deadlines and time requirements.
> 3. Classify tasks as High, Medium or Low priority.
> 4. Break large tasks into smaller actionable steps.
> 5. Create a realistic schedule without overloading the user.
> 6. Identify conflicts and missing information.
> 7. Provide concise and practical recommendations.
> 8. Adapt suggestions to the user's stated preferences.
>
> **Important:** Do not claim that a reminder, appointment or task has actually been scheduled unless an external scheduling or reminder system has confirmed it.
>
> Respond using clear headings, bullet points and actionable steps."


# 18. Expected Output

The Personal Productivity Assistant should be able to:

- Understand natural-language task requests.
- Extract tasks and deadlines.
- Assign appropriate priorities.
- Generate daily schedules.
- Identify possible conflicts.
- Provide productivity suggestions.
- Provide general answers.
- Adapt responses to user preferences.
- Break complex tasks into manageable steps.



# Result

**The prompt-based Personal Productivity Assistant was successfully designed and implemented as a prototype. The experiment demonstrated the progression from simple to advanced prompts and showed that structured, contextual and preference-aware prompts produce more relevant, personalized and actionable responses. The application successfully demonstrates how Large Language Models can be used to solve everyday productivity and planning problems.**
