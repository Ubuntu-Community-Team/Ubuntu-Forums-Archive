---
title: "Permission denied '/dev/ttyUSB0'"
date: 2023-02-20
forum: General Help
---

### Post by ron-kellis on 2023-02-20
I'm trying to run Pronterface, a 3D printing application. I'm a Ubuntu user from 16 with just enough technical savvy to usually figure out how to get done the task at hand. Not a programmer and never will be. My skills lie elsewhere. 

 I am a member of the dialout group. I've found several other posts on the topic. Only one suggestion worked:
sudo chmod 666 /dev/ttyUB0 but only for one connection.
A second attempt resulted in: chmod: changing permissions of '/dev/ttyUSB0' : Operation not permitted.
A third attempt resulted in: Command 'chmod' not found, did you mean command 'chmod from deb coreutils (8.30-3ubuntu2) Try: sudo apt install <deb name>

Anyone have any insight into what it takes to use a USB COM port? Or what I've done that I can't access the port/printer like every other user of the application?

Any help is deeply appreciated. 

Ron

---

### Post by #&amp;thj^% on 2023-02-20
No insight, but I'll try to help you, show this please:
```
ls -lah /dev/ttyUSB0
```
And give me your method exactly you added yourself to dailup. (>>>Details matter always)

---

### Post by ron-kellis on 2023-02-20
:D :D :D Oh happy day!!!! Thank you! And do I really hope that putting my exact problem in the title helps others!!!

Yes, details matter MAJ Reacher (Ret) and I apologize for not providing everything I'd tried. Bad manners, and my apologies. 
IIRC it was the last that informed me I was already a member of the  dialout group. Logging off and then back on after the last attempt  flushed the terminal. 

Previously I'd tried:
crw-re---- 1 root dialout 188, 0 5 apr 23.01 ttyACMO 

Then realized looking at it later the date was when the poster had run the command and it was the wrong tty  "amateur" duh. But I have no idea if the date could have been left blank followed by "ttyUSB0"

sudo usermod -a -G dialout ron
KERNEL=="ttyUSB[0-9]*", OWNER= ron

sudo adduser ron dialout

The quick assist is deeply appreciated! I tried to find a "Thank you" or "Kudo" or "Resolved" and I regret I can't find anything. If I'm missing the obvious, please let me know.

---

### Post by #&amp;thj^% on 2023-02-20
You did great, it's hard to know what we want to see, so we just ask for what we need. :)
Good Job!

---

### Post by #&amp;thj^% on 2023-02-20
> **ron-kellis said:**
> : or "Resolved" and I regret I can't find anything. If I'm missing the obvious, please let me know.
In your first post >>>upper right hand corner "Thread Tools" mark as SOLVED

---

### Post by ron-kellis on 2023-02-20
Marked "Resolved" 
"With realization of one's own potential and self-confidence in one's ability, one can build a better world." Thank you for taking this to heart. "Wreckage of the past" at times can make this really hard for some, but we do the best we can with what we have. As to the "Why" for my plea of help, that's all it took to run the test on the "project" 3D printer and verify I need a new hot end. On the used 4 times printer <rolls eyes>.

---

