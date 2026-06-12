---
title: "problems with touchpad, fonts, logout and file permissions"
date: 2008-01-22
forum: General Help
---

### Post by viherpeukalo on 2008-01-22
I'm using Kubuntu 7.10 with KDE 3, kernel version 2.6.22-14-generic and fglrx 8.45.4 as my ATI driver. The computer is Fujitsu-Siemens Amilo D 1845.

I have a bunch of annoying little problems.

1. When I copy files from a cd, dvd or a usb memory stick or hdd, the files copy fine but the files are marked to have only read permissions. I can change the permissions after copying, it's no problem, but i'd like things to run smoothly. How can I change the permissions to be read+write straight after copying?

2.[SOLVED] My touchpad seems to have a secret button (!) on the upper-right corner, that takes me to some random websites that i've been to earlier. How do I get rid of this? 
- I had to change konqueror settings for the touchpad.

3. Logout goes well sometimes when I do it just after login, but usually the screen just goes dark or gives these random colours. This might be a problem with fglrx, but I didn't have the problem in all the earlier versions.

4.[SOLVED] After installing KDE 4 all the fonts turned very pixel-y and crude. I haven't found anti-aliasing or subpixeling to help any.
- A range of font sizes was excluded from anti-aliasing & subpixeling

I'd really appreciate a pointer or two.

[edit: some problems solved]

---

### Post by jksrecko on 2008-01-25
> **viherpeukalo said:**
> 
3. Logout goes well sometimes when I do it just after login, but usually the screen just goes dark or gives these random colours. This might be a problem with fglrx, but I didn't have the problem in all the earlier versions.


Same here. Problem appeared after installing newest fglrx (8.45.4). At least they fixed lower right corner corruption.

Also, resuming out of suspension complains. I'd like to add that suspend to ram doesn't work (doesn't even suspend) when running Compiz, or any other OpenGL app (e.g. screensaver).

---

