---
title: "Can't login anymore, get thrown back to Display Manager"
date: 2007-02-18
forum: General Help
---

### Post by erdalronahi on 2007-02-18
I have Gnome, Xfce and  KDE installed on my computer, though i use KDE seldom. Yesterday I worked in KDE, and now I cannot login anymore. Neither to GNOME nor to Xfce or KDE. GDM accepts my login, but after a few seconds I am thrown back to the login screen without any error message displayed.

On the other hand, a timed login after 30 seconds for another user account does work, however from this I cannot logout anymore. 

The same happens if I replace GDM with KDM. The .xsession-errors file is empty. I am running Edgy. 

Any ideas on this?

---

### Post by taurus on 2007-02-18
Boot into recovery mode from GRUB menu and post the output of this command here.

```
df  -h
```

---

### Post by erdalronahi on 2007-02-18
I never got help that fast in my life - phew! You are right, my home partition is full. 

df -h returns 100% of use. 

Thank you very much for this quick response.

---

### Post by taurus on 2007-02-18
While still in the recovery mode, run

```
aptitude clean
rm ~/.Trash/*
rm /home/**username**/.Trash/*
df -h
```
Replace the **username** with your actual login name.

---

### Post by erdalronahi on 2007-02-18
Yes, thanks, I was able to manage that from the console.

---

### Post by WBAC88 on 2007-02-19
I've tried to do the:

rm /home/username/.Trash/*

several different times, but it's not working for me. I have the same problem as the original poster, but even though df -h says my hdd is 100% full, I know that it shouldn't be because I had 1.2GB free last time I was logged in. I've tried aptitude clean, which cleared everything up the first time this happened, but this time isn't helping at all.

I also have been having problems getting rid of specific files/folders with the rm command because I can get to /home/username/ but I can't seem to get into the desktop or music/picture folders that I have in that directory. Is there a command to display this? I am very new to any sort of linux, so very basic help with this would be much appreciated. I have a Dell Inspiron laptop, 128MB RAM, 1GHtz, 5GB hdd and running Xubuntu Edgy.
Thanks a lot.

---

### Post by erdalronahi on 2007-02-23
No idea why that might be. You know that it makes a difference whether you write "desktop" or "Desktop"? In Linux filenames are case-sensitive. 

What error message do you get when you try to change into the directories?

---

### Post by geirha on 2007-02-23
I often find this usefull when I need to clean up:
```
du --max-depth=1 | sort -g
```
It gives you a good idea of what files and directories (in your current directory) uses the most space.

---

