---
title: "Problems with Komposer"
date: 2014-05-03
forum: General Help
---

### Post by MeanRoy on 2014-05-03
I've been using Komposer without a problem for a number of years.

A couple of days ago it wouldn't start up correctly. The program panel appeared after a message which read:
"invalid URL - the location cannot be opened"

I uninstalled and tried to re-install.
Although it appeared to install, clicking the icon didn't seem to do anything.
Since then I have tried everything I can think of or was suggested by Google sources.

I kept pretty good track of what I did in a tomboy notes log:

Kompozer probs!
Kompozer wont load files has error message

Uninstalled - Reinstalled from Ubuntu Software Center
No workie
Uninstalled again

added ppa:giuseppe-iuculano/ppa
installed from ppa:giuseppe-iuculano/ppa
still no workie

sudo apt-get purge kompozer
search for kompozer

Find a bunch of stuff on disk and it's owned by root!
> [INDENT]
**So after more googling**:

meanroy@meanroy-desktop:~$ sudo passwd root
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

meanroy@meanroy-desktop:~$ sudo passwd -u root 
passwd: password expiry information changed.

meanroy@meanroy-desktop:~$ sudo nautilus
Initializing nautilus-gdu extension

&#8226; deleted files found in search for kompozer 
&#8226; [COLOR="#FF0000"]noted I didn't need to log in as root (after the fact)
[/COLOR]
then to disable root:

meanroy@meanroy-desktop:~$ sudo passwd -dl root
[sudo] password for meanroy: 
passwd: password expiry information changed.
meanroy@meanroy-desktop:~$ [/INDENT]

re-installed from ppa:giuseppe-iuculano/ppa

rebooted.
Start program doesn't!

Un-installed.
ran:
 sudo nautilus
&#8226; browse to file system
&#8226; search for files "kompozer
&#8226; deleted files
^Z to quit nautilus
booted from live disk
ran fsck
0 probs report.
Booted from LiveDisk and re-ran fsck
0 problem reported, disk is clean.

re-boot
re-install older Kompozer from Ubuntu -- [COLOR="#FF0000"][SIZE=2]Note: this was not the case! ubuntu has updated to kompozer 1:0.8~b3-2~ubuntu10.04~1 [/SIZE][/COLOR]

same problem!

So in a terminal window I try:
> meanroy@meanroy-desktop:/usr/bin$ kompozer -h
Usage: /usr/lib/kompozer/kompozer-bin [ options ... ] [URL]
       where options include:

X11 options
	--display=DISPLAY		X display to use
	--sync		Make X calls synchronous
	--no-xshm		Don't use X shared memory extension
	--xim-preedit=STYLE
	--xim-status=STYLE
	--g-fatal-warnings		Make all warnings fatal

Mozilla options
	-height <value>		Set height of startup window to <value>.
	-h or -help		Print this message.
	-width <value>		Set width of startup window to <value>.
	-v or -version		Print KompoZer version.
	-P <profile>		Start with <profile>.
	-ProfileManager		Start with Profile Manager.
	-UILocale <locale>		Start with <locale> resources as UI Locale.
	-contentLocale <locale>		Start with <locale> resources as content Locale.
	-safe-mode		Disables extensions and themes for this session.
Segmentation fault
meanroy@meanroy-desktop:/usr/bin$ 

Note the Segmentation fault message!

I don't know where to go from here, anyone have a suggestion?


Roy

---

### Post by MeanRoy on 2014-05-04
After continued research I noted that this problem occurred after I had installed bluefish and attempted to configure both it and Kompozer to use firefox as the browser and Bluefish as the editor for Kompozer.
This suggests a possible involvement with Firefox.

I repeated the steps above to remove BOTH Kompozer and Bluefish completely.
re-installed kompozer from ubuntu software center.

Same problem. 
Not sure what to do about Firefox. Purge and re-install?

Noted that softcen has the newer version of kompozer 1:0.8~b3-2~ubuntu 10.04~1 , I'm not sure which ver I had installed but I think 1:0.8~b1-2: amd64 i386 .

Also note after checking dpkg.log with the system log viewer that also I installed Tidy.

Will repeat process to remove Tidy.
Then try installing 1:0.8~b1-2: amd64 i386 I suppose.

[SIZE=3][COLOR="#FF0000"]I could sure use some expert help here[/COLOR][/SIZE]

---

### Post by MeanRoy on 2014-05-04
After install of kompozer_0.8~b1-2_i386.deb things work again.

This may mean the current version on Ubuntu is broken(maybe - but I haven't found any recent complaints) or it may be that my system is B0rked(possible - it's been running a long time with lots of stuff installed) or it may be that removing Tidy fixed everything and I could run the latest version(unlikely but still possible).

For now I'm goinng to leave things as they are so I can get some work done.

Bye, it's been fun. (NOT)

---

