---
title: "wine - shoot me in the face"
date: 2007-02-22
forum: General Help
---

### Post by cisforcojo on 2007-02-22
Hey guys...
I love Ubuntu but every time it's frustrating as hell. There's always (at least) ONE THING that just refuses to work. Granted, it's much better than any other linux distro I've tried and FreeBSD as well. 

Anyways, I've almost got my box set up perfectly (after 2 full days) and now I'm stuck on WINE of all things. I have installed it (0.9.30) and no problems so far. When I run winecfg:

cojones@tipping-point:/media/eyeq$ winecfg
wine: creating configuration directory '/home/cojones/.wine'...
err:advpack:create_tmp_ini_file Unable to create temp ini file
err:advpack:create_tmp_ini_file Unable to create temp ini file
Failed to open the service control manager.
err:advpack:create_tmp_ini_file Unable to create temp ini file

I said, hey maybe just try to run a program straight out. 
cojones@tipping-point:/media/eyeq$ wine Setup.exe
wine: creating configuration directory '/home/cojones/.wine'...
err:advpack:create_tmp_ini_file Unable to create temp ini file
err:advpack:create_tmp_ini_file Unable to create temp ini file
Failed to open the service control manager.
err:advpack:create_tmp_ini_file Unable to create temp ini file


I've been working on this for about 3 hours and have scoured almost everything I can find on google and ubuntuforums.org. Maybe I've been looking at it too long. Any help you can give me would be greatly appreciated!

Collen

---

### Post by justin whitaker on 2007-02-22
Let's go simple: let wine autoconfig by typing wine notepad in a terminal.

---

### Post by cisforcojo on 2007-02-22
cojones@tipping-point:~$ wine notepad
wine: creating configuration directory '/home/cojones/.wine'...
Failed to open the service control manager.


just hangs like that and have to ^C out
I'm really at a loss on this one because I've had wine installed (and running Warcraft 3) many times before.

---

### Post by justin whitaker on 2007-02-22
> **cisforcojo said:**
> cojones@tipping-point:~$ wine notepad
wine: creating configuration directory '/home/cojones/.wine'...
Failed to open the service control manager.


just hangs like that and have to ^C out
I'm really at a loss on this one because I've had wine installed (and running Warcraft 3) many times before.

That's really weird. 

How did you install it? Manually? Synaptic? Automatix?

I'm wondering if there is a permissions issue. What permissions are on the .wine folder? 

Have you tried completely removing wine in synaptic (double checking the hidden folders are gone) and reinstalling it?

---

### Post by cisforcojo on 2007-02-22
Yea I thought something similar. I installed with Synaptic.
I don't think it's an issue with the package because I've removed everything from:
/var/cache/apt/archives/ and redownloaded it from a different repo and still the exact same problem.

About the permissions, there isn't a .wine folder yet.
What is happening is it is making random folders like:

cojones@tipping-point:~$ ls .wi*
.wine-Av3X1t:
dosdevices  drive_c  system.reg  userdef.reg  user.reg

.wine-LPHMN5:
dosdevices  drive_c  system.reg  userdef.reg  user.reg

.wine-y2h5jX:
dosdevices  drive_c  system.reg  userdef.reg  user.reg
cojones@tipping-point:~$ 

NOTE: Whenever I try the program again, I kill all 'wineserver' apps running and explorer.exe instances (and delete all temp folders) so making sure nothing is running and no temp wine folders isn't helping either.

Here are the permissions on the temp folders:
drwxr-xr-x  4 cojones cojones  4096 2007-02-23 03:26 .wine-Av3X1t
drwxr-xr-x  4 cojones cojones  4096 2007-02-23 03:43 .wine-LPHMN5
drwxr-xr-x  4 cojones cojones  4096 2007-02-23 03:27 .wine-y2h5jX

The only thing I can think of is that I had cedega installed BEFORE I had wine installed (but I never tried to install or run anything with cedega). Cedega is completely gone now and still these problems. I have no clue what is going on. The errors aren't giving me anything I can work with. The program isn't crashing, it's just hanging. Just says Failed to open system control manager or whatever and there you have it. I left it on overnight and still nothing more displayed. 

Do you know anywhere I could go to check this out? I feel like it's probably a simple fix but I don't know where to check. (I tried running it even as root, taboo I know but I was desperate. Same results).

I appreciate all your help! Haha, it's this kinda stuff that makes me go insane with Linux. I can't tell you how many hours/days I waste doing this kinda stuff

---

### Post by cisforcojo on 2007-02-23
How about this, does anyone know how I could get more informative debugging info?

I've really got nothing to work with and there's very little on the net about this (surprisingly)

---

### Post by cisforcojo on 2007-02-23
I just tried winecfg in XGL and it worked fine. (I usually use GNOME).
I am currently using the fglrx driver and I have an ATI Mobility Radeon X600.
Anyone have any idea why GNOME would be causing these problems?

I can now get winecfg to open but there is nothing in the screen (just a transparent box).

with:

wine notepad, it loads up and looks alright but I can't click on anything inside it or type. It's just a useless window.

---

### Post by sloggerkhan on 2007-02-23
I installed wine from repos and I had to modify the permissions of the entire inside of the .wine subdirectory to get it to work correctly. Initially, wine didn't have permission to write any of the autoconfig changes to file, which made it dies, or something similar to that. It's been a little while.

---

### Post by cisforcojo on 2007-02-23
Nah, the permissions are fine. None of them root'd.
Anyone have any ideas, I'd love it. I'm all out. What programs/packages would interfere with wine?

---

### Post by shrimphead on 2007-02-23
re the debugging info if you run

gdb wine

and then when you get to the gdb prompt type run, this should give you full debug output for the wine process, hopefully that'll let you get some decent error messages out

---

### Post by cisforcojo on 2007-02-24
FIXED!!!!

I use SCIM to also input Chinese and there's a bug that doesn't allow this.

For those of you with this problem:

$ XMODIFIERS=""

run that from console and it should load up fine

---

