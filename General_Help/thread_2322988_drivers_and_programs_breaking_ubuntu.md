---
title: "drivers and programs breaking ubuntu"
date: 2016-05-02
forum: General Help
---

### Post by jameswdenyer on 2016-05-02
hello im trying to swicth to linux as i feel its a much safer os  and so i have been trying many different distros, and in my adventures i came across a problem

if you install the cannon pixma mg3500 driver for ubuntu like the following in the terminal:
[COLOR=#000000][I][COLOR=#FF0000]cd Downloads[/COLOR]
[/I]
[/COLOR]
[COLOR=#000000]then[/COLOR]

[COLOR=#000000][I][COLOR=#FF0000]tar -zxvf cnijfilter-mg3500series-4.00-1-deb.tar.g[/COLOR]z
[/I]
[/COLOR]
[COLOR=#000000]then [/COLOR]

[COLOR=#000000][I][COLOR=#FF0000]cd cnijfilter-mg3500series-4.00-1-deb[/COLOR]
[/I]
[/COLOR]
[COLOR=#000000]then [/COLOR]

[COLOR=#000000][I][COLOR=#FF0000]sudo ./install.sh[/COLOR]
[/I]
[/COLOR]
and then afterwards install clementine from the software store then restart your computer......it damages ubuntu.  it comes up with a window saying that there has been an internal problem with ubuntu.
i would not of known it was these 2 programs, unless i tried it first in Zorin os. you see in zorins software store when i tried to install clementine, it warns you it would cause problems first, before it allows you to install it.
 i did it anyway and least to say it became very buggy and unstable, i swicthed to ubuntu 16 hoping that it was no longer a problem, ubuntu is more stable then zorin after installing the 2 programs but i still got the error.

the error report is not coming back, but i would be greatfull if one of the linux experts here could try it in virtual box and see if you can get the same problem, because im rather worried that i have done permanent damage to my os

---

### Post by Bucky Ball on 2016-05-02
Welcome. Not sure why you're doing all this. Looks like the driver is a .deb file. You only need to double click them and it will install. You don't even need to open a terminal. 

It is in a tar.gz, though. When you uncompress that, are you left with a .deb file? If so, double click it and done, or should be. If it doesn't auto-install, install gdebi and install it with that. Gnome Software is still having a few issues from what I've read (I don't use Ubuntu so can't confirm).

>  it comes up with a window saying that there has been an internal problem with ubuntu.

Any more specific details about what error or any errors you're getting, as in the exact text, will help us help you.

---

### Post by jameswdenyer on 2016-05-02
this is the problem; the error is not coming back when i restart the system is there a way at looking at past errors? im i supposed to belive the ubuntu has just fixed itself?
and as for why i did it this way.......im a complete novice when it comes to linux, when i want to do something i just look on this forum on how and just do what im told.

i followed this thread   [http://ubuntuforums.org/showthread.php?t=2209879](http://ubuntuforums.org/showthread.php?t=2209879)

worked a treat cannon printer works perfectly on wiresless!  but thats beside the point.

---

### Post by Bucky Ball on 2016-05-02
Interesting. You could check in /var/log/syslog and see what you can find. I would 

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
``` 

... and move on as 

> this is the problem; the error is not coming back when i restart the system

... which means that, to all intents and purposes and regardless of how it was resolved, your original problem is fixed. Perhaps the machine did just need a restart. If you could tell us if you did anything different this time and it worked this time it would be helpful to others.

If your original issue is solved, which it appears to be from your last post, please mark the thread as solved. This won't close the thread to further discussion. If you have further questions best to post a new thread, link to this one if it helps to illustrate, and use a descriptive thread title.

Good luck.

---

### Post by jameswdenyer on 2016-05-02
What do those terminal commands do. What is there purpose?

---

### Post by Bucky Ball on 2016-05-02
Get your computer up to date and remove any redundant dross.

```
sudo apt autoremove [removes 'orphaned' and unused packages]
sudo apt update [updates list of available packages]
sudo apt full-upgrade [upgrades the system by removing/installing/upgrading packages, it _does not_ upgrade your OS to a newer release]
``` 

You can find out what commands do and their options for yourself by opening a terminal and:

```
 apt --help
```

For instance, choose a command/package and try one out. Put the name in a terminal and add '--help' to the end. You can also use 'man' for info. For instance:

```
man apt
```

Try it.

---

### Post by jameswdenyer on 2016-05-02
when opening synaptic package manager which i just installed. i got this error :
W: The repository 'cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) dists/ Release' does not have a Release file.
W: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
W: See apt-secure(8) manpage for repository creation and user configuration details.
W: [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:) Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:) Signature by key 3B068FB4789ABE4AEFA3BB491397BC53640DB551 uses weak digest algorithm (SHA1)
is it related?

---

### Post by Bucky Ball on 2016-05-02
Not sure, but it shows you have your install CD set as a repository. Open Software and Updates and switch it off (untick it).

PS: Please use [code] tags for terminal output. Keeps formatting, neat and easier to read. Instruction linked in my signature below.

---

