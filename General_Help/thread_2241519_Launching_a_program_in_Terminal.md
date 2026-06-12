---
title: "Launching a program in Terminal"
date: 2014-08-26
forum: General Help
---

### Post by gordon99 on 2014-08-26
I am running on Xubuntu 14.04. 
I have just installed a Duplicate Bridge scoring program from the Software Centre. It is called 'gsalliere'. The 'g' indicates that this version is suitable for GUI usage, or so it says. 
However, underneath the title it says the program has to be run from Terminal. I had imagined I would install the program and find a convenient launch icon on the Desktop, but no such luck. 
I have found a file titled 'salliere' in /usr/share/ but, of course, it is in root and, by the way, 'catfish' did not seem to be able to locate 'gsalliere' or 'salliere'. Perhaps my patience just ran out too quickly.
Could someone please inform me what commands I have to use to get the program to run and what I need to do to get a launch icon on Desktop.

---

### Post by deadflowr on 2014-08-26
perhaps try
```
man gsalliere
```
in a terminal,
to see if it has a man page, and then what options it might have to launch it.
I half expect it to launch with just the name "gsalliere".

---

### Post by yancek on 2014-08-26
A quick google indicates that there is a man page for gsalliere.  Have you tried just typing:  gsallire in a terminal hitting the Enter key?  If you need a full path, try which gsalliere or whereis gsalliere to find out where it is.

---

### Post by gordon99 on 2014-08-27
Thanks deadflowr and yancek. You were both quite right. It launched by just entering 'gsalliere' in terminal. I thought it would be more complicated than that, requiring an 'apt-get',
or some such, command.

---

