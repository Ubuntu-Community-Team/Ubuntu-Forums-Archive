---
title: "sh can't open script?"
date: 2013-01-05
forum: General Help
---

### Post by sunny6591 on 2013-01-05
Hello

I have the same problem while installing 10.1 version of Quartus.

But I cant open the script (quartus.sh) file, its too big (around 3 GB). Can you suggest what else can be done in this case!
Thanks 

Best
Shashank Gaur

> **Los Frijoles said:**
> The setup file: [http://pastebin.com/2anxFzwp](http://pastebin.com/2anxFzwp)

I have a feeling that the |& on line 19 isn't right...I've never seen an "or-and" before (or course, for all I know its just a boolean function I've never used). However, when I change it to || the error changes to "28: bad substitution".

Edit: SOLVED! Ok, so on a whim I decided to run "bash setup". It worked! So here is the problem: the scripts all did #!/bin/sh which on my computer redirects to dash. The scripts are written for bash! So, for people who browse this later the solution is to change the symbolic link /bin/sh to bash (and if you would like, change it back when done).

---

### Post by sffvba[e0rt on 2013-01-05
*Post **moved **to own thread* (original thread link - [http://ubuntuforums.org/showthread.php?t=1885162](http://ubuntuforums.org/showthread.php?t=1885162))


404

---

### Post by The Cog on 2013-01-05
Sunny6591,

You should be able to open the file with either vi (if you know how to use it) or nano. 

Please start a new thread if you are still having problems, rather than trying to re-awaken a thread that was marked solved over a year ago. A new short thread is much more likely to get helpful answers than a long thread that is already marked solved.

How you are trying to open the file - "can't open it" doesn't tell us a lot. You can link this thread from the new one if you think it helps.

---

