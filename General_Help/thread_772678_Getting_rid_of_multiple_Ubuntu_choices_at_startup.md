---
title: "Getting rid of multiple Ubuntu choices at startup"
date: 2008-04-28
forum: General Help
---

### Post by n7vrz on 2008-04-28
I tried using Wubi to install Ubuntu as a dual boot with my Vista Home Premium 64 bit. 
I tried just Wubi and the installation failed. At start up I have the choice of Vista or Ubuntu.
I tried dl'ing Ubuntu and putting it in the same folder as Wubi, then trying to install. Again it failed. I now have Vista and 2 Ubuntu at start up. 
Burn the image of the dl'd Ubuntu file to cd and tried Wubi from it's folder. Failed. Vista and 3 Ubuntu at start up.
Tried the Wubi that I saw on the cd. Failed. 4 Ubuntu. 
In total I've tried 5 different ways to install and they have all failed. 
Every time the install didn't work, I used Vista's Programs and Features to delete Ubuntu. What I want to do now is get rid of all those Ubuntu's I have at start up.
Can someone help with that?

---

### Post by darkenedsoul on 2008-04-28
Hi,

First I'll ask a question or so.

1) Are you saying that on boot-up (when you get to the Vista/Ubuntu boot options from boot.ini or whatever it's now called in Vista) you see Vista + multiple Ubuntu boot options?

2) You deinstalled Ubuntu with Vista's add/remove programs (again, whatever it's called, I have Vist Ultimate 64bit installed as a dual-boot (XP/Vista Ult. 64 ) on 2 partitions of my RAID 0 config)? Did the directories get removed for the Ubuntu installs?

I'll see if I can be of some help. If the answer to 1 and 2 are yes, have you looked at Vista's bcdedit tool? It's for editing its boot.ini or whatever its called (assuming boot.ini for compatibility-sake). You can search the web and find what switches to use to display the information. Also from within Control Panel like on XP you should be able to show the boot options and edit it from there to remove them (safely?). But don't do so until some others confirm my suggestions or expand on them. That's all I can think of atm. It sounds like it didn't completely clean up itself on de-installation.

I had installed 7.10 (twice, but uninstalled before 2nd install attempt) but it never booted so I deinstalled it via add/remove programs in Vista Ultimate 64 and it cleaned up my boot.ini file so I only see XP Pro SP2 and Vista Ultimate 64.


Mike

---

### Post by n7vrz on 2008-04-28
1. Yes
2. Yes
Didn't know about bcdedit, I'll give that a look see.

---

### Post by ochetski on 2009-08-24
Just registered to thanks.
Worked fine for me, i had 3 ubuntu options on start up.
:lolflag:

---

