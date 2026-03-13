# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
The first time I ran it, the most blatant issue I noticed was that the higher/lower hints gave no indication to the actual direction of the target. If anything they were misleading. Moreover, once you complete the game, despite pressing new game, it doesn't actually let you do a new game, it refreses the number and the attempts, but the actual search function just breaks. 

- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").
Biggest issue is that the hints are backwards, so for someone trying to play the game the way it's meant to be played, it is near impossible to win. 
The other issue I noticed is that upon finishing the game there is no way to play again unless you reload the whole website, despite there being a button dedicated to a new game 
---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
I used Claude for this project.
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
One suggestion that was correct was the reworking of the hints. Just be looking at the code, it is obvious that they are flipped, but in order to test it, I made the change, pushed it, and then tested the game
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).
So one suggest that was misleading was actually while I was fixing that same hints issue. It fixed the go higher go lower as expected, but forgot about the TypeError block which had the old swapped messages. After testing it I went back in and realized something was still wrong, so I then fixed that and retested it, ensuring the code was working as expected.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
I decided a bug was fixed by manually testing the game after pushing each change. For the hints bug, I actually played through a few rounds and checked that "go higher" and "go lower" pointed me in the right direction toward the secret number. If the game behavior matched what I expected as a player, I called it fixed. If something still felt off, like when the TypeError block still had the old swapped messages, I went back and dug deeper.
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
  I ran a manual test in the browser after fixing the hints. I started a game, guessed a number I knew was low, and checked whether the hint told me to go higher — which it now correctly did. This showed me that the core comparison logic was working, but it also revealed that the TypeError message block was still broken since it still gave misleading feedback in edge cases. That test essentially uncovered a second bug hiding inside the first fix.
- Did AI help you design or understand any tests? How?
AI didn't explicitly tell me to run tests, but it did help me realize I needed to look more carefully after the first fix. When I tested the game and something still seemed wrong, I went back to Claude and it pointed out the TypeError block that had been missed. In that way, AI helped me understand that testing one part of the code isn't enough — you have to test the whole flow, not just the line you changed.
---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
The secret number kept changing because there was a line that said random.randint() at the top so every button click would randomize the value making it impossible to get
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
Streamlit "reruns" are essentially re running the entire python script each time a change is made or a button is pressed. That's why session state is a key dictionary because that survives those reruns making it useable. 
- What change did you make that finally gave the game a stable secret number?
We put the random.randint() line of code in an if statement that way it was only called when needed, and not on every rerun.
---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
  One habit I would love to develop through this project is ensuring my git pushes and commits are meaningful rather than too many for little reason or too little for large changes.
- What is one thing you would do differently next time you work with AI on a coding task?
Next time I work with AI, something I could do differently is be more specific with AI prompting, instead of asking what it thinks about a specific area, I could point to the lines I think the issue is at and go from there. 
- In one or two sentences, describe how this project changed the way you think about AI generated code.
Before this project, I assumed AI could fully create this guesser and decode it instantly but through this, I learned that it isn't that simple, and manual testing is key in order to create a fully functional application.