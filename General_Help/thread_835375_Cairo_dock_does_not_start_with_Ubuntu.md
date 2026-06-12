---
title: "Cairo dock does not start with Ubuntu"
date: 2008-06-20
forum: General Help
---

### Post by kismeras on 2008-06-20
Hey guys, 

Still new and learning ubuntu. I have a few questions about desktop effects. First is :

I tried AWN dock, how do i make sure it is completely uninstalled?

Second:

I am using Cairo dock, but it does not automatically start up with Ubuntu...how do i make it start with Ubuntu?

I think that's it for now.....i know i have a million more though. Thanks everyone for all of the help so far. The Ubuntu community is definitely making it easy for me to learn and want to continue to learn Linux/Ubuntu.

---

### Post by NikoC on 2008-06-20
On the AWN thing:
I assume you've found some directions on removing AWN and followed those so it should be gone. There might be a hidden AWN folder left in your home directory where settings of the program are stored, but this will not influence the speed of your system (as opposed to remaining registry entries in windows). To find out if such a folder exists, open a terminal and type in your home directory: ls -A
This will get you a list of all files and folders, including the hidden ones. To remove a folder (e.g. a folder named .awn): rm -r .awn

On the Cairo dock:
System > Preferences > Sessions
You can add programs there that should be launched on login.

Cheers.

---

### Post by kismeras on 2008-06-20
Hey, 

Thanks NikoC

I looked in system > preferences > sessions , I did not see Cairo dock listed in there. I see there is a button to add stuff, but i have no clue what to add or where to find it. Can you tell me what my next step should be? Thanks.

---

### Post by NikoC on 2008-06-20
No problem.

When you have opened Sessions, click the 'add' button on the 'Startup programs' tab.
A new dialogue box will appear in which you can enter:

Name: name of how the application will appear in the session list, so you can choose whatever you want here
Command: cairo-dock (I think that's the launch command for the dock, never used cairo myself)
Comment: no need to enter text here

When you logout and back in again, cairo dock should start automatically now.

Good luck!

---

### Post by kismeras on 2008-06-20
NikoC, 

Rock on :guitar:. Thanks a million. I got Cairo dock starting with Ubuntu now.

---

### Post by ihunter32 on 2008-06-20
hello, im also VERY new lol...

i installed Cairo Dock, and when i run it, nothing happens.

any ideas/suggestions?

---

### Post by kismeras on 2008-06-20
If you move your mouse to the bottom center of the screen, nothing happens? Also, try going to system tools and see if Cairo dock is in there.

---

### Post by thaltrego on 2008-09-10
[QUOTE=NikoC;5226560]No problem.
thanx bro, i was also snooping around for the same thing since morning.

---

