---
title: "Cannot type password for &quot;sudo&quot; commands"
date: 2008-04-04
forum: General Help
---

### Post by _BLUE on 2008-04-04
OOPS, solved.

I'm a Linux newbie, planning on installing Damn Small to my flash drive.
I have recently installed Ubuntu to an old hard drive from my basement,

I then switched to KDE from GNOME (I suppose that's Kubuntu now.)

Everything went ok and I installed the video drivers using Envy 1.9.
Now, my hardware is properly recognized (including stupid 8800GT)

But now I have a peculiar problem. I can type in the Terminal just fine, but I am not able to enter my password when I use the "sudo" command. This is, needless to say, a problem. 

My main issue right now is installing Wine so I can play the Orange Box (great game set) in (k)ubuntu, which requires me to enter these commands before installation:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.l

I can't do that because it requires Sudo... Please help.

Full hardware:

Intel C2D E4500 @2926MHz 11x266FSB
Gigabyte GA-P35-DS3L 
BFG Tech 8800GT OC
WD400 40GB IDE hard drive with (k)ubuntu
WD4000 400GB SATA hard drive with Win Vista 64
ASUS DRW-1814-BLT DVD-burner
Xclio Goodpower 500w power supply
2GB A-DATA Extreme Edition DDR2-800

---

### Post by _BLUE on 2008-04-04
oops, forgot to subscribe.

---

### Post by _BLUE on 2008-04-04
oops, forgot there is no visual feedback for terminal. Google is your friend.

---

### Post by douggard on 2008-04-04
yea, you just type your password in and hit enter
it doesnt show it

---

