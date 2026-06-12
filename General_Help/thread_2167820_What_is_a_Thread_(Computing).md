---
title: "What is a Thread (Computing)"
date: 2013-08-15
forum: General Help
---

### Post by mikel2 on 2013-08-15
i read about it on wiki and still have hard time to grasp it. can someone tell me in more simple way what it is and what i need it for

---

### Post by 3rdalbum on 2013-08-15
Threads let programs do more than one thing at a time. For instance, a video player will have one piece of code that plays the video and puts it on the screen, and another piece of code that listens for mouseclicks and keypresses (so you can click Pause or change the volume slider). Each of those pieces of code will run in two different threads.

The CPU will switch between the threads automatically so they both get to run simultaneously, or so it seems. With a multi-core CPU, different threads can run on different cores.

That's it! Only developers need to know about threads, not end users.

---

### Post by mikel2 on 2013-08-15
im a newbie c++ programmer. this explanation is good thanx

---

