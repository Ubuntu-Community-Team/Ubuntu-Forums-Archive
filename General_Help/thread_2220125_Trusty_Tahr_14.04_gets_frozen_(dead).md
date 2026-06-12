---
title: "Trusty Tahr 14.04 gets frozen (dead)"
date: 2014-04-26
forum: General Help
---

### Post by quimmontal on 2014-04-26
Hi everyone,

I'm pretty desperate right now, I've installed and uninstalled and created new bootables usb drives with diferent tools because there was always the same problem: ubuntu suddenly freezes and dies. No error, no reason to make it break, just dies when he likes. It died one time when installing skype, it died another time when looking wallpapers, and it died another time when I had just logged in. I've been looking arround on the web but I didn't find anyone who had the same problem nor the reason  of these sudden deaths.
I just don't know what to do, its a brand new PC I builded, I builded another one and installed ubuntu 13.10 and I had no problem at all in the 2 weeks. I just can't work knowing that at any time all the work will go to ****... 

Thanks in advance for your help,

Quim

---

### Post by deadflowr on 2014-04-26
1) Could you gives us more information on what the specs for your machine are.

2) When you say dies, what do you mean?
Does it simply hang with a frozen screen, or does the machine shutdown?

---

### Post by quimmontal on 2014-04-27
> **deadflowr said:**
> 1) Could you gives us more information on what the specs for your machine are.

2) When you say dies, what do you mean?
Does it simply hang with a frozen screen, or does the machine shutdown?

Hi deadflowr thanks for your answer,

1) My machine is an Intel i7 4771 CPU, Intel Desktop Board DH87MC, 8 GB RAM, GeForce GTX 660, Ubuntu installed on Samsung SSD 840 EVO. I have windows installed in another hard drive and I haven't have any problem with it, but I don't think its an SSD problem. I changed BIOS in order to have cpu gpu always on in order to have 2 Displays, I don't think that is the problem. The machine where I installed the Ubuntu 13.10 had same specs except of an the SSD (Kingston V300) and the Graphic Card (Radeon R9 270X).

2) When I say it dies, I mean computer keeps online, but everything freezes. No respones even when trying to shutdown from the button, I am forced to restart the computer. In one of the several installs that I did, first it all freezed but the mouse, then after half a minute I could go around with the mouse it freezes also.

Thanks for your help :)

---

### Post by kurja on 2014-04-27
2) You mean that the desktop environment becomes unresposive? Can you still move the mouse cursor, I guess so if you're able to try shutting down from top right corner 'cogwheel'? If you press ctrl+alt+F2 can you get into terminal session? If yes, issue command ```
unity
``` to restart your graphical desktop, press ctrl+alt+F7 to return to gui and see if it's been resurrected?

---

### Post by quimmontal on 2014-04-27
> **kurja said:**
> 2) You mean that the desktop environment becomes unresposive? Can you still move the mouse cursor, I guess so if you're able to try shutting down from top right corner 'cogwheel'? If you press ctrl+alt+F2 can you get into terminal session? If yes, issue command ```
unity
``` to restart your graphical desktop, press ctrl+alt+F7 to return to gui and see if it's been resurrected?
 
Hi kurja and thanks for you answer,

Well, even though the mouse was still moving for a little more, everything was unresponsive, and shortcuts didn't affect at all :(

I have restarted BIOS to default, I don't think it is the problem but better than anything... I'll see if it keeps freezing randomly. Anyway, I'll have into account what to said in order to try to solve the problem, thanks for your help :)

---

### Post by quimmontal on 2014-04-27
Hi kurja, 

Just when I answered, it freezed, this time at trying to download Netbeans. Totally unresponsive, nothing works. I don't know what to do T.T

Edit: This time, when I entered the system gave me "System Problem" and Ubuntu 14.04 has experienced and internal error.

ExecutablePath> /usr/bin/Xorg
Package> xserver-xorg-core 2:1.15.1-0ubuntu2
ProblemType>Crash
Title> Xorg crashed with SIGABRT
.tmp.unity.support.test.0
ApportVersion>2.14.1-0ubuntu3
Architecture>amd64

etc, etc, I'm not able to copy the report. Any idea how to solve that? :S

---

### Post by kurja on 2014-04-27
Did you try ctr+alt+F2 when it had 'frozen'? Did you get a terminal session with that?

---

### Post by Aivaras on 2014-04-27
I have similar problems with my Acer Aspire 5750 laptop. Ubuntu just freezes approximately once a day, sometimes when I work, sometimes when I leave my laptop switched on at night. I cannot move my mouse or switch to terminal, it's not responding to Alt+SysRq+R+E+I+S+U+B command. System log shows nothing. There were no such freezes on Ubuntu 13.10.

---

### Post by quimmontal on 2014-04-27
Yes I tried but no new terminal session, neither with Ctr-Alt-T, I got a report problem with Xorg which I edited the last post, I though I would have time before you answered xD

---

### Post by quimmontal on 2014-04-27
> **Aivaras said:**
> I have similar problems with my Acer Aspire 5750 laptop. Ubuntu just freezes approximately once a day, sometimes when I work, sometimes when I leave my laptop switched on at night. I cannot move my mouse or switch to terminal, it's not responding to Alt+SysRq+R+E+I+S+U+B command. System log shows nothing. There were no such freezes on Ubuntu 13.10.

Well I shouldn't be happy that you have the same problem but I'm happy to know I am not the only one so that there may be some solution to a general problem xD
I'm thinking about just installing 13.10 and keep it working well.


Edit: It happened again. If it was only once a day maybe I could take it, but not this often. I'll just install 13.10. Sorry for bothering you all.

---

### Post by kurja on 2014-04-27
Xorg crashing should not prevent switching to terminal session with ctrl alt F2; if that key combination doesn't do anything (does it do anything, was there any response??) there must be something else gone wrong too but I don't know what it might be.

edit - what gpu driver do you have?

---

### Post by quimmontal on 2014-04-27
> **kurja said:**
> Xorg crashing should not prevent switching to terminal session with ctrl alt F2; if that key combination doesn't do anything (does it do anything, was there any response??) there must be something else gone wrong too but I don't know what it might be.

edit - what gpu driver do you have?

I had the opensource driver at first, the last time it happened I just had changed to the nvidia propietary tested driver. No response trying to change to terminal session :(

---

### Post by quimmontal on 2014-04-27
Hi everyone,

I did a last install, tried 13.10 and upgraded to 14.04. No problems given so far. Hope it keeps this way.

Thanks everyone for your help.

Quim

---

