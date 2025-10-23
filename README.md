# Module 2: Lesson 1 - State Schema
1. Learnt how to use typed state schemas (specifically TypedDict, dataclass, and Pydantic models) to ensure that every node in the LangGraph structure shares a consistent data structure.
2. This makes the overall graph more predictable and easier to manage.
3. The existing "mood" channel has been renamed to the "feeling".
4. Using values like "overwhelmed" or "underwhelmed" to represent the state or mood.
<img width="902" height="215" alt="image" src="https://github.com/user-attachments/assets/af99accf-4c41-495b-89ad-87d63c55a149" />
fig 2.1.1: Using TypedDict

<img width="1784" height="442" alt="image" src="https://github.com/user-attachments/assets/7e71da04-d9e6-4d19-9213-ae85b24de1de" />
fig 2.1.2: Using Dataclass

<img width="1788" height="356" alt="image" src="https://github.com/user-attachments/assets/095449fd-099d-4b0a-93da-9134d3c05d3e" />
fig 2.1.3: Using Pydantic

# Module 2: Lesson 2 - State Reducers
1. Learnt that reducers are used to let multiple parallel nodes safely merge their updates. This ensures that the final state contract remains predictable and consistent even with concurrent operations.
2. By using annotated keys, you can easily swap between different state merging behaviors, for example- overwrite, append, or a custom merge function, without needing to rewrite or modify the node logic itself.
3. Changed the "foo" channel with "status"

# Module 2: Lesson 3 - Multiple Schemas
1. Learnt that nodes can use a private state to exchange temporary variables. This is crucial because it allows internal logic to operate without affecting the graph's public schema or the final, external output.
2. Tweaked the code to use more explicit values such as "track/temp" and "input/output/data".
<img width="1788" height="232" alt="image" src="https://github.com/user-attachments/assets/b17c5d80-448a-4d46-9d5d-f4b406bbc94c" />
fig 2.3.1: Multiple Schemas

# Module 2: Lesson 4 - Trim and Filter Messages
1. Learnt how to manage conversations by exploring how message reducers, filters, and trimmers are used to precisely control the amount of conversation history (chat_log) sent to the model each turn.
2. Learnt that maintaining a consistent message channel allows the chat history to be reshaped or processed without breaking the core LangGraph structure.
3. List names were replaced with: chat_log and chat_track, and prompt was updated
<img width="2938" height="1668" alt="image" src="https://github.com/user-attachments/assets/96e09836-da9f-4c04-a439-725fabd283e9" />
fig 2.4.1: Trace of the chat

# Module 2: Lesson 5 - Chatbot w/ Summarizing messages and Memory
1. Learned to use review/summary to effectively compress the conversation history. This allows LangGraph to handle persistence memory across multiple steps and threads efficiently.
2. Explored how to use conditional edges as a mechanism to decide when to refresh the review. This ensures the model receives consistent context without incurring the cost of reprocessing all the messages in history.
3. The code was tweaked by replacing the key used in the graph state to review and prompts were changed to incorporate understanding.
