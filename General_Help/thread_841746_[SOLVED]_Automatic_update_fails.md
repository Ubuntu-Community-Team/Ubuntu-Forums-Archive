---
title: "[SOLVED] Automatic update fails"
date: 2008-06-26
forum: General Help
---

### Post by e_swallie on 2008-06-26
when i try to run the auto update system i cant get it to work i get this error message and i am a total noob, i have no idea what it means or how to fix it.  i have tried to do what it says, but either i am doing it wrong or it does not work.





An error occured

The following details are provided:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by e_swallie on 2008-06-26
when i try to run the auto update system i cant get it to work i get this error message and i am a total noob, i have no idea what it means or how to fix it. i have tried to do what it says, but either i am doing it wrong or it does not work.





An error occured

The following details are provided:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

---

### Post by e_swallie on 2008-06-26
when i try to run the auto update system i cant get it to work i get this error message and i am a total noob, i have no idea what it means or how to fix it. i have tried to do what it says, but either i am doing it wrong or it does not work.





An error occured

The following details are provided:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by ibutho on 2008-06-26
To fix it, run Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
```

---

### Post by avtolle on 2008-06-26
From the terminal (Applications>>Accessories>>Terminal)```
sudo dpkg --configure -a
```Post any error messages you get.

---

### Post by ibutho on 2008-06-26
Look [here]("http://ubuntuforums.org/showthread.php?t=841764"). Generally its good forum behaviour to not post multiple threads about the same issue,

---

### Post by bodhi.zazen on 2008-06-26
Please try not to triple post (I know accident happen)

But it cause confusion and duplication of effort.

---

### Post by e_swallie on 2008-06-26
Ah was not really a triple post they were originally 3 posts in different forums that were somehow combined into one thread  but thanks for the help your reply and the reply from avtoli fixed my problem it seems

---

### Post by bodhi.zazen on 2008-06-26
Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help 
[indent]... and users looking for solutions.[/indent]

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by e_swallie on 2008-06-26
how do i mark it as solved?

---

### Post by avtolle on 2008-06-26
Use the thread tools, top left, to mark it "solved". :-)

---

### Post by e_swallie on 2008-06-27
Thanks all for the help.

---

