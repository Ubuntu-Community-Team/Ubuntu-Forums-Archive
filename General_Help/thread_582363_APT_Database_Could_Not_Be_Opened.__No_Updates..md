---
title: "APT Database Could Not Be Opened.  No Updates."
date: 2007-10-19
forum: General Help
---

### Post by umechanism on 2007-10-19
**Using Feisty 7.04 with KDE.**  

I am trying to update some files using Adept Updater in KDE.  Doing so gives the below message,


"[COLOR="Blue"]The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.[/COLOR]"

So, I tried running apt-setup and apt-get update as suggested and I received the below messages in terminal;

[COLOR="Blue"]mrmsudawgs@closet:~$ sudo apt-setup
sudo: apt-setup: command not found
mrmsudawgs@closet:~$ sudo apt-get update
E: Malformed line 47 in source list /etc/apt/sources.list (dist parse)
mrmsudawgs@closet:~$   [/COLOR]

I'm a total Noob so I do not understand what this means other than "it's broken".  That, I understand.  It was working just fine yesterday and I've only lately been trying to get gtkpod and Amarok to work properly so I've not been rewriting code or anything like that.  (I can't write code - figure of speech.)

Any help is appreciated.

M

---

### Post by dabl on 2007-10-19
So you tried Automatix, and it borked your sources list, eh?

Open a console window, or press Alt-F2, and enter ```
kdesu kate /etc/apt/sources.list
``` and then go down to the line that is screwed up, which would be line 47, and either delete it or fix it so that it looks like the lines above it.  :)

---

### Post by umechanism on 2007-10-19
I'm not sure what I did to break it but your suggestion worked like a charm!  I'm back in business!!

Thank you very much!!

M:popcorn::guitar:

---

### Post by Fady on 2007-10-27
hey i have same prob i tried resolving it but i get this!

kdesu kate /etc/apt/sources.list
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

and the sources list comes up is that where the line is? and what do u mean by screwed up? im noooOOOoob so plz bare with me

---

### Post by umechanism on 2007-10-27
Have you added any new, third party repositories?  If so, that may be the problem - at least that was my problem.  If you did add a new repository, open the sources list as previously described and scroll down that list until you find the URL of the third party repositories that you added.  Delete them.

My updates started working again after I deleted this one certain repository.  I learned that not all repositories are kept current and some of them do not work at all.  It is those that caused my updates to stop working.

Hope this helps.

---

### Post by Fady on 2007-10-27
> **umechanism said:**
> Have you added any new, third party repositories?  If so, that may be the problem - at least that was my problem.  If you did add a new repository, open the sources list as previously described and scroll down that list until you find the URL of the third party repositories that you added.  Delete them.

My updates started working again after I deleted this one certain repository.  I learned that not all repositories are kept current and some of them do not work at all.  It is those that caused my updates to stop working.

Hope this helps.

Thank You Very Much!!!!!!!!!!!!!!

---

