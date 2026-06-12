---
title: "[SOLVED] XUBUNTU desktop wont load after update, have to start gnome."
date: 2008-07-04
forum: General Help
---

### Post by mobilediesel on 2008-07-04
I installed whatever updates there were yesterday, I don't remember what all was there. Now when I boot my computer, it acts like it's booting but the panels never show up. The only thing that responds is CTRL-ALT-BACKSPACE to restart and pick gnome session. XFCE will not load the panels for some reason and I cannot right-click for a menu or anything else.

Is there a way to go to the package manager and roll-back the updates to XFCE to one that works?

---

### Post by bikerdave on 2008-07-05
Sounds exactly like what has happened to my Ubuntu setup, mine is the 64 bit software. I can logon as usual, but it then just shows my background with no panels. I am too new to know my way around the OS yet. Any help would be greatly appreciated and sorry for piggybacking on your post.

---

### Post by mobilediesel on 2008-07-05
> **bikerdave said:**
> Sounds exactly like what has happened to my Ubuntu setup, mine is the 64 bit software. I can logon as usual, but it then just shows my background with no panels. I am too new to know my way around the OS yet. Any help would be greatly appreciated and sorry for piggybacking on your post.

No problem about piggybacking as long as someone who knows more than we do can help us out!

---

### Post by bikerdave on 2008-07-06
> **bikerdave said:**
> Sounds exactly like what has happened to my Ubuntu setup, mine is the 64 bit software. I can logon as usual, but it then just shows my background with no panels. I am too new to know my way around the OS yet. Any help would be greatly appreciated and sorry for piggybacking on your post.

I wanted to bump this thread and also add that I am using 8.04

---

### Post by NET WT on 2008-07-06
I use Xubuntu 8.04 and also had this problem. This is what I did to get my panels back. 

I pressed Alt+F2 and typed:

> xfce4-panel

then clicked the Run button, and they came back.

---

### Post by mobilediesel on 2008-07-06
> **NET WT said:**
> I use Xubuntu 8.04 and also had this problem. This is what I did to get my panels back. 

I pressed Alt+F2 and typed:



then clicked the Run button, and they came back.

I discovered that as well but the panels are gone the next time I boot up the computer. I have to do that ALT-F2 and xfce-panel after I boot every time now.

At least I can use the computer without going into gnome, though.

---

### Post by NET WT on 2008-07-06
Do you have the "Save session for future logins" checked in the "Quit" dialogue? Make sure you do.

---

### Post by mobilediesel on 2008-07-06
> **NET WT said:**
> Do you have the "Save session for future logins" checked in the "Quit" dialogue? Make sure you do.

I tried with it checked, I tried with it unchecked. Same result either way, I have to ALT+F2 xfce-panel to get the panels to come up.

---

### Post by bikerdave on 2008-07-07
MobileDiesel, This fixed my problem. I found this thread while browsing today. Hope it fixes your problem too. It basically is re downloading your entire desktop.

[http://ubuntuforums.org/showthread.php?t=851611](http://ubuntuforums.org/showthread.php?t=851611)

---

### Post by mobilediesel on 2008-07-07
Well, after doing <alt><f2> and xfce-panel, I went into settings and deleted the panels and recreated them. Also unchecked the "allow xfce to manage desktop" and rechecked it. Now everything does what it's supposed to do.

...except for the time it didn't.

At least when things DO go wrong in Linux, you actually get suggestions on what to try next! And most suggestions WORK! When I had trouble in Windows I usually got responses like "HA! N00B!" and B.S. like that. The only reason I know Windows so freakin well now is that it KEPT BREAKING!

---

### Post by guga31bb on 2009-01-18
Hi, I'm having the same problem but alt+f2 does not work for me (when I press it, nothing happens). I also can't get an internet connection because the xubuntu-desktop forced me to uninstall WICD. I'm running Hardy. 

Any suggestions?

---

