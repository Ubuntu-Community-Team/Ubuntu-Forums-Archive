---
title: "Problem with Adept installer and manager"
date: 2006-12-18
forum: General Help
---

### Post by nibi on 2006-12-18
I recently installed kubuntu and not having enough technical knowledge abt linux, i just thought i'd install stuff via the user-friendly gui ("Add/Remove Programs" & "Adept manager manage packages") instead of going to the konsole and typing stuff from the forums. I first installed the nvidia drivers from there and followed a guide on the ubuntu forums to configure xorg.conf. Then i tried installing compiz but it gave me the following error message word by word:

"There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages."

after that it lists compiz as being installed even though its not. When i try uninstalling compiz it gives the same message and uninstallation doesn't happen. Then i tried installing firefox but it gave me the same error message. Firefox however was kind of installed as i could launch it and it seemed to work but since installation gave that error message i thought i'd reinstall it but it gave me the same error message when i tried to uninstall it. Unlike compiz however, it managed to uninstall.

For now i am not touching it again and thought i'd ask on the forums before doing anything. I hope someone knows abt it from experience!
O and if it matters one of my friends was changing some settings earlier in the repositories or something like that, i don't exactly remember.

---

### Post by hal10000 on 2006-12-18
Maybe something in your /etc/apt/sources.list is broken. You should at least have the following entries uncommented (without a # in front of the line):
```

deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe

```
Check this with sudo gedit /etc/apt/sources.list and fix it if necessary.
Then, from a termianl eindow do [COLOR="Red"]sudo apt-get update[/COLOR]
Btw, adept looks fine, but synaptic is better.

---

### Post by nibi on 2006-12-18
Thanks for the reply hal10000 but:

a. The command sudo gedit /etc/apt/sources.list doesn't work on my system, it says command not found.

b. I can't find synaptic anywhere, i only have adept.

I think its because i am using Kubuntu (KDE) not ubuntu (GNOME).

---

### Post by madcow72 on 2006-12-18
Gnome users often use the "gedit" command, but that won't work on Kubuntu.  Any time you see "gedit", change that to one of the following:  nano, vim, kate, etc...  Lot's of different editors you can use.

BTW, what are the error messages you're getting upon install?  Can you paste the important parts here?  Is it just the "broken package" error?

---

### Post by AlanRogers on 2006-12-18
> **nibi said:**
> a. The command sudo gedit /etc/apt/sources.list doesn't work on my system, it says command not found.Try instead:```
sudo kate /etc/apt/sources.list
```You will be asked for your password before it will proceed.

---

### Post by madcow72 on 2006-12-18
Another quick note:  don't be afraid to use the konsole, it works great and is much faster than adept when you learn it.  Just a few commands you need to know:
sudo aptitude update  (This updates your package list)
sudo aptitude search XXXX  (This will search for package XXXX in the repositories and display all packages with XXXX in the name.)
sudo aptitude install XXXX  (When you know the name of the package, this will install everything, including dependencies.)
sudo aptitude remove XXXX  (To uninstall the package.)  

Know those, and installing is quite easy from the konsole...and fast!

---

### Post by hal10000 on 2006-12-18
Can you post the content of your /etc/apt/sources.list?
Maybe there is missing some entries.

---

### Post by nibi on 2006-12-18
@madcow72
The exact error message that i get is the one i've posted above (and thanks for the konsole tutorial :) ):
"There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages."

Here's my /etc/apt/sources.list

```

deb http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

---

### Post by hal10000 on 2006-12-18
That's strange. Your sources.list seems to be ok so far.
What if you try to remove compiz via command-line [COLOR="Red"]sudo apt-get update[/COLOR], then [COLOR="Red"]sudo apt-get remove compiz[/COLOR] and then reinstall it [COLOR="Red"]sudo apt-get install compiz[/COLOR]
If this doesn't work then maybe you have installed a package which conflicts with compiz.

---

### Post by nibi on 2006-12-18
When i try sudo apt-get remove compiz-core, i get the following message:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  compiz-plugins compiz-core
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  compiz-core compiz-plugins
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 2273kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 79322 files and directories currently installed.)
Removing compiz-plugins ...
/var/lib/dpkg/info/compiz-plugins.prerm: 6: gconf-schemas: not found
dpkg: error processing compiz-plugins (--remove):
 subprocess pre-removal script returned error exit status 127
dpkg: compiz-core: dependency problems, but removing anyway as you request:
 compiz-plugins depends on compiz-core (= 1:0.3.3-0ubuntu2~git2006112~edgy1).
Removing compiz-core ...
/var/lib/dpkg/info/compiz-core.prerm: 6: gconf-schemas: not found
dpkg: error processing compiz-core (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 compiz-plugins
 compiz-core
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Also i have attached a screenshot of adept

---

### Post by madcow72 on 2006-12-18
Actually, I may be wrong about this, but you may want to try Beryl over Compiz for your windows manager.  I think its more stable and is getting more support.  I tried doing compiz a few months back and kept running into the same "broken packages" error, as well as many other errors.  Never got it to work.  I did get Beryl to work on my desktop (P4 1.5GB Ram, ATI Radeon 9250) but only with a single monitor.  My laptop however, (Pentium M, 512MB Ram, Nvidia...something) got beryl to work nicely on *dual* monitors which is really cool!  Unfortunately, things just seemed too unstable and I decided I didn't need beryl to keep my computer working, and so uninstalled.  You may want to look [here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL") for a beryl howto.

---

### Post by nibi on 2006-12-18
I have actually decided to install beryl now as it supports KWin themes but the problem is that i want to get rid of all the clutter that the unsuccessful compiz installation has created on my computer.

---

### Post by madcow72 on 2006-12-19
Maybe silly, but try:
```
sudo aptitude remove compiz
```  I keep hearing that aptitude does a better job than adept.  Maybe try:```
sudo aptitude search compiz
``` And then purge everything that comes up with an "i" next to it, (that means it's installed.)
```
sudo aptitude purge compiz
```    Otherwise, perhaps the packages really didn't get installed... In which case, if you want, maybe just try moving ahead with the beryl+AIGLX install.

---

### Post by nibi on 2006-12-19
Big HUG to everyone that helped esp madcow72..thanks m8!
just used sudo aptitude to reinstall compiz and then removed and purged it.
Now installing beryl!

---

### Post by madcow72 on 2006-12-19
You're welcome!  Let us know how it goes!  So many people have helped me to learn linux and kubuntu, that I'm glad if I can help anyone else out!

---

### Post by RasmusMH on 2007-11-04
This is perfect. After updating to Gutsy i had this error too, but after using 
sudo aptitude purge compiz-core 
i can update again.

---

### Post by TheBuzzSaw on 2007-11-05
Wow, this saved me as well! I was liking Kubuntu until I ran into this problem. Now I can resume enjoying it. ^_^

sudo aptitude purge compiz-core

---

