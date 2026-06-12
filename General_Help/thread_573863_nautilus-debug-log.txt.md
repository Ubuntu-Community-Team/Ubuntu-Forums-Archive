---
title: "nautilus-debug-log.txt"
date: 2007-10-12
forum: General Help
---

### Post by frankos44 on 2007-10-12
Hi

I am interested to know why i have a file called nautilus-debug-log.txt in my home folder that appears  to be changing in size all the time. If i delete it, it comes straight back again. I expected it to be slowing the computer down as its size can be in 4Mbytes or more at times but it doesnt seem too.

Any ideas?

---

### Post by frankos44 on 2007-11-19
Seemed to be a 7.10 Beta issue. Now OK on Released version.

---

### Post by gtr225 on 2007-11-25
I have the issue as well. How can I fix it?

---

### Post by Anonii on 2007-11-25
I'm not a GNOME user, but I can guess that it's the file where Nautilus puts all the information to help on debugging everytime it crashes. 

Aw well, after a Google search (You should learn to do this yourself, it's easy!) I found this piece of text in: [http://en.opensuse.org/Bugs:GNOME#Nautilus](http://en.opensuse.org/Bugs:GNOME#Nautilus)

[B]
Nautilus has a debug logging infrastructure. If Nautilus crashes, it will write a ~/nautilus-debug-log.txt file which you can attach to a bug report. This file contains a log of your last actions, and additional information which may be useful to debug the problem. [/B]

---

### Post by gtr225 on 2007-11-25
Well the thing is, I don't think Nautilus is crashing, however it's still leaving a debug file in my home directory.

---

### Post by apetresc on 2007-11-25
Nautilus can be configured to write that file even when it doesn't crash, but it's strange that it's doing so without your telling it to. Do a ```
locate nautilus-debug-log.conf
``` and let me know if it is found.

---

### Post by FuturePilot on 2007-11-25
What does it say in the file?

---

### Post by daz4126 on 2007-12-02
I get this too, on a released verions of Gutsy (not beta). The message is:
===== BEGIN MILESTONES =====
0x8177880 2007/12/01 18:13:46.3305 (USER): debug log dumped due to signal 11
0x8177880 2007/12/01 18:13:46.3308 (USER): debug log dumped due to signal 11
0x8177880 2007/12/01 18:13:46.3309 (USER): debug log dumped due to signal 11
0x8177880 2007/12/01 18:13:46.3310 (USER): debug log dumped due to signal 11


This message then just repeats over and over.
I found this bug report, which I think explains it:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/153382](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/153382)

.... but does anybody know how to fix it?

cheers,

DAZ

---

### Post by frankos44 on 2007-12-02
Problem went away when loaded the release version of Gutsy. I never kept a copy of the file.

---

### Post by FuturePilot on 2007-12-02
> **daz4126 said:**
> I get this too, on a released verions of Gutsy (not beta). The message is:
===== BEGIN MILESTONES =====
0x8177880 2007/12/01 18:13:46.3305 (USER): debug log dumped due to signal 11
0x8177880 2007/12/01 18:13:46.3308 (USER): debug log dumped due to signal 11
0x8177880 2007/12/01 18:13:46.3309 (USER): debug log dumped due to signal 11
0x8177880 2007/12/01 18:13:46.3310 (USER): debug log dumped due to signal 11


This message then just repeats over and over.
I found this bug report, which I think explains it:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/153382](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/153382)

.... but does anybody know how to fix it?

cheers,

DAZ
Also here
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150471]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150471")

---

### Post by craigyjack on 2008-01-10
3 months and no patch for this >_>  oh well, at least the bug is marked as confirmed and high priority, so i'm assuming it'll be fixed sometime and an update will come :)   then i will no long have to seem that dang nautilus-debug-log.txt in my home directory every single day >.<

---

### Post by apetresc on 2008-01-10
> **craigyjack said:**
> then i will no long have to seem that dang nautilus-debug-log.txt in my home directory every single day >.<

If that's what's bothering you so much, you can add ```
rm ~/nautilus-debug-log.txt
``` to your .bash_profile and that will delete the file every time you log in. You know, fix the symptom but not the cause.

---

