---
title: "Acessing KDE 4's root account"
date: 2008-05-07
forum: General Help
---

### Post by Sabretooth on 2008-05-07
How do you get to the root account for KDE 4? I'm using Kubuntu's Remix version and there was no option for setting up the root account during installation.

I can't make many changes throughout my system and hence can't set up stuff like sound, the date/time, the Internet etc. There's no option to hit the root password in the control center itself, like in KDE 3. It tells me that I need to log in as root user to change everything.

Where is the root account? What is the password to it?

---

### Post by ogcub on 2008-05-07
> **Sabretooth said:**
> How do you get to the root account for KDE 4? I'm using Kubuntu's Remix version and there was no option for setting up the root account during installation.

I can't make many changes throughout my system and hence can't set up stuff like sound, the date/time, the Internet etc. There's no option to hit the root password in the control center itself, like in KDE 3. It tells me that I need to log in as root user to change everything.

Where is the root account? What is the password to it?

root account is disabled in ubuntu world, you should use sudo, gtksudo or similar thing for root tasks, I think same applies to kubuntu, you just need to use kdesu or something. 
As for options in system settings, this is bug, yuo can install kcontrol from kde3, it helps with some settings. KDE 4 isn't ready for everyday usage yet, wait for 4.1 if you want kubuntu, or try fedora next week, they should have fixed those annoying bugs.

---

### Post by Sabretooth on 2008-05-07
Aw, okay. Although I would have really appreciated a root account. Wasn't really impressed with Kubuntu anyways, I'm afraid. :D I think I'll stick to my trusty PCLinuxOS!

---

### Post by Tyke91 on 2008-05-07
whatever floats your boat man... although I believe that using sudo and gksudo/kdesudo make your account much more secure than just running straight root.

but hey, that's the joy of linux. you can choose :)

---

### Post by ASULutzy on 2008-05-07
If you're really stubborn, and know what you're doing with any Unix type system, it's not exactly hard to get a root shell.

I'll list one of like, 20 ways to do it.```
sudo su
``` should work

But honestly, the sudo thing really isn't that bad, and generally is a safer way to go. Occasionally I get frustrated if I'm doing piped things that require root and I'll just sudo su it, but overall it's really not too bad.

---

