---
title: "Problem with windows media center with ubuntu"
date: 2008-06-28
forum: General Help
---

### Post by Akash Singhal on 2008-06-28
Thanks to all of you for paying attention to my problem.
I am new to ubuntu and that's why I installed ubuntu 8.04-LTS Desktop edition on my Dell 1525 laptop which already has Microsoft Windows Vista Home Premium as another os.
After installing Ubuntu I am encountering problems with windows media center...it does work at all neither it throws any error message.
I have tried to open it through command prompt but there also it shows nothing on the command prompt window..it just simply returns to the prompt..please help me out.

---

### Post by prshah on 2008-06-28
> **Akash Singhal said:**
> 
 already has Microsoft Windows Vista Home Premium as another os.
After installing Ubuntu I am encountering problems with windows media center...


What you are describing seems to be totally unrelated; Ubuntu has nothing to do with Windows Media Center and vice-versa. 

However, can you be more specific about the problem you face? Does media center not load? Does it not play audio? Does it not play video? What command did you use to open windows media center from the prompt? Can you post screenshots to clarify your problem?

---

### Post by Akash Singhal on 2008-06-28
When I click the Windows Media Center Icon nothing happens.
Also when I try to open any media file by right-clicking and then clicking "Open with Media Center" my laptop show wait sign for some time and then nothing happens.

I opened the command prompt as Administrator:
the prompt shows:

C:/Windows>

I typed eshell.exe

and the command prompt showed me

C:/Windows>

again.

---

### Post by prshah on 2008-06-28
> **Akash Singhal said:**
> When I click the Windows Media Center Icon nothing happens.
Also when I try to open any media file by right-clicking and then clicking "Open with Media Center" my laptop show wait sign for some time and then nothing happens.


Any related messages in the event log viewer? Start-Run, then ```
eventvwr.msc
```

---

### Post by Akash Singhal on 2008-06-28
There are no messages regarding windows media center in the event viewer.

---

### Post by prshah on 2008-06-28
> **Akash Singhal said:**
> 
I typed eshell.exe


> **Akash Singhal said:**
> There are no messages regarding windows media center in the event viewer.

Fine: _after_ running eshell in a command prompt _again_, can you see any eshell processes in task manager's (Ctrl-Shift-Esc) running processes? (See processes from all users). If you can, _additionally_ try running media center as normal, now can you see _another_ eshell process? (ie, 2 or more eshell processes?)

---

### Post by Akash Singhal on 2008-06-28
I have tried doing what you have asked me to do.
There was no change trying both the ways.
Here is a screenshot of the task manager showing various processes:

---

