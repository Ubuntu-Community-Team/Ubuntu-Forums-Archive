---
title: "Installing Ubuntu vs. CD"
date: 2007-12-13
forum: General Help
---

### Post by petitevache on 2007-12-13
This may be a stupid question, but... if I install Ubuntu directly on my computer, will it affect my files? Or will I still be able to access them, will I be able to burn them onto CD's?

---

### Post by zivxx on 2007-12-13
Thats not a stupid question, but the question i want to ask you is if you want to use you entire harddisc or just part from it?

---

### Post by petitevache on 2007-12-13
Well, I'm not sure - how would both options affect my computer? Which one do you think is better? 

My situation is basically that I just want to get some files off my computer before reinstalling Windows, and I'm having some major problems with speedsticks and external harddrives which is taking a lot more time and effort than it's worth, so I thought it'd be easier to just burn my files... but I can't do that while the Ubuntu CD is in the computer.

---

### Post by CatKiller on 2007-12-13
If I were you I would use the installer to resize the Windows partition and install Ubuntu in the newly-created free space. Ubuntu will be able to read your Windows files, and, depending on the version, may even mount them automatically for you. Then you can burn them to cd, and either stick with Ubuntu as is or reinstall Windows as originally planned.

---

### Post by aysiu on 2007-12-13
If you don't have backups of all your important files, you shouldn't be installing a new operating system on your computer.

*Theoretically*, you can safely resize your existing partition and create a new partition for Ubuntu, leaving your files and current operating system intact.

*In reality*, there's a slight chance something might go wrong, or you may not understand what you're doing and accidentally erase everything on your hard drive.

**Back it up!**

---

### Post by IcemanV9 on 2007-12-13
I have this exact situation a couple of years ago. I used Slax to be loaded in the memory (RAM) and took CD out. Then, I burned all (important) files to a blank CD without a glitch.

---

### Post by petitevache on 2007-12-14
Aysiu, I'm pretty certain I wouldn't know what I'm doing and would cause some kind of problem. :D So I guess it's better I keep trying without that for the time being. 

IcemanV9, can you expand on that? What is Slax?

---

### Post by aysiu on 2007-12-14
> **petitevache said:**
> Aysiu, I'm pretty certain I wouldn't know what I'm doing and would cause some kind of problem. :D So I guess it's better I keep trying without that for the time being. 

IcemanV9, can you expand on that? What is Slax?
If you have at least 512 MB of RAM, consider [installing Ubuntu as a virtual OS inside Windows](http://www.psychocats.net/ubuntu/virtualbox).

---

### Post by IcemanV9 on 2007-12-16
> **petitevache said:**
> IcemanV9, can you expand on that? What is Slax?

Please take a look at [Slax's website]("http://slax.hosting4p.com/") for more info.

I cannot access to WinXP due to no login screen, just blue screen. There was no solution to rectify it except to reinstall WinXP. So, I booted up Slax mini-CD (livecd) with this boot command: slax copy2ram. All it did to copy all files to RAM (at least 384 Mb or more). Then, it ejected the CD when done. I used K3b app to burn all (important) files (such as resumes, photos, documents) off the WinXP partition to a blank CD. I rebuilt the box as dual boot (WinXP & Ubuntu) system.

---

