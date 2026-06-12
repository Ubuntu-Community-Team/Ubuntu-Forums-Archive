---
title: "Kubuntu accidental uninstall nightmare no ethernet"
date: 2008-06-14
forum: General Help
---

### Post by maninalift on 2008-06-14
EDIT:
The following is the problem as it NOW stands. To see the history of this read below the line and the posts upto #11.

After accidentally uninstalling mykubuntu desktop and getting errors in my packages, I have managed to reinstall most of kubuntu-desktop.

When I start up I get the graphical login screen but then just get a teminal in the corner of my screen uxtem. X appears to have started u. If I start kicker, kwin and kdesktop from the terminal I have a functioning desktop.

However. Konqueror for example is missing, when I try to install it I get the following error:

```
trying to overwrite `/usr/share/apps/konqueror/servicemenues/media_safelyremove.desktop', which is also in package kio-umountwrapper
dpkg-deb:subprocess paste killed by signal (Brocken pipe)
Eroors were encountered while processing:
/cdrom//pool/main/k/kdebase/konqueror_3.5.9-0ubuntu7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I can't do much with apt-get without it telling me that I need to fix kio-umountwrapper or broken dependencies (which packages depending on konqueror). Attempts to uninstall kio-umountwrapper fail.

-----------------------------------------------

I was using adept package manager to uninstall VLC and must have selected the wrong package, because to my horror I saw my desktop being uninstalled digikam... openoffice.... then the really scary bit: KWin... KDM. Then there was an error, initially I was relieved, expecting that the changes would be rolled back. They weren't. I tried reinstalling packages but the brocken KDM package seemed to prevent me from doing anything. At this point I made another mistake - I restarted the computer.

Everything uninstalled, I boot to the command propt. 

Initially I tried to apt-get fix the system but I can't detect the ethernet connection.

I have the kubuntu 8.04 64 bit alternative CD (which is the system I have installed) and tried the "fix broken system" hoping that it would walk me through the process of installing missing packages but it didn't. It also couldn't detect my ethernet card at all.

I feel that I should be able to install the packages from the CD using apt-get but I'm not sure how.

I am posting this using an openSUSE KDE4.1 beta live CD, which does seem to be able to detect my ethernet card.

Grateful for any help, thanks

p.s. Most days of the week I'm a geek and I'd give the relevent information in an orderd way but today I've killed my computer and I want to cry so please forgive my incoherent babbling.

---

### Post by prshah on 2008-06-14
> **maninalift said:**
> I was using adept package manager to uninstall VLC and must have selected the wrong package, because to my horror I saw my desktop being uninstalled

Initially I tried to apt-get fix the system but I can't detect the ethernet connection.

I am posting this using an openSUSE KDE4.1 beta live CD, which does seem to be able to detect my ethernet card.


I think Kubuntu may not be detecting your network card because you may have uninstalled Knetwork manager.

Here's a _suggestion:_

Boot into your (broken) kubuntu system, either in regular or recovery mode. Add your alternate CD to the sources.list if it isn't already present. Do a ```
sudo apt-get update
``` to ensure that the package information present in the CD is integrated in your systems apt database. Then give the command```
sudo apt-get install kubuntu-desktop
```

Good luck!

---

### Post by maninalift on 2008-06-14
OK. I knew that I had to do this but hearing someone tell me is calming (as I say I was panicing a bit). 

do I add something like

deb file:/mnt/cdrom/dists hardy restricted

?

...ah, it seem the CD I have is dapper  - not sure how that happened. Hmmm, I'll see what happens

---

### Post by prshah on 2008-06-15
> **maninalift said:**
> 
do I add something like
deb file:/mnt/cdrom/dists hardy restricted


This is what I have on my system:
```
deb cdrom:[color=red][Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)][/color]/ hardy main restricted
```

I don't know how you will replace the bit in red with a suitable title/identifier for your cd...

---

### Post by maninalift on 2008-06-15
Thanks, I'll try to figure out what that stuff means and what I should replace it with. Perhaps as it is in square-brackets it doesn't actually need to be there (ie it only pervents accessing the wrong CD). My approach didn't work.

I'll be back later either with thanks or with more detailed errors.

Cheers

---

### Post by zvacet on 2008-06-15
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by maninalift on 2008-06-15
Thanks zvacet, I was jsut coming here to post that "sudo apt-cdrom add" and "sudo apt-get update" worked but  "sudo apt-get install kubuntu-desktop" failed.

I don't know what I can do to prevent all the messages scrolling past in the terminal before I can read them. From what I can see install kubuntu-desktop, lists all of the packages that kubuntu-desktop depends upon but says "Depends: xxx but it is not going to be installed" where "xxx" is the package name. When it's finished with that it prints "E: Broken packages".

I tried "apt-get -f install", this intially looked hopeful but then went to a blank screen with blinking cursor. After rebooting there was no obvious change.

---

### Post by maninalift on 2008-06-15
OK I'm downloading a Hardy DVD now (I'm not sure why the CD I had is Dapper).

In the meantime: the apt-cdrom seems to work:
 found, 0 
Found 2 packages indexes, 0 source indexes, 0 translation, 1 signiture
...copying package list...
...Good signiture...
Reading package indexes Done
Writing new source list
...
Unmounting CD-ROM


when I apt-get update I get "Ign" (Ignore) next to the  cdrom entry.

---

### Post by maninalift on 2008-06-15
DVD seems to be doing the trick. Mind you so did the CD until I got the blinking cursor of death...

everything going OK until....


```
Errors were encountered while processing:
 /cdrom//pool/main/k/kdebase/konqueror_3.5.9-0ubuntu7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I tried -f install and got the same error

OK this is what it comes down to:

```
trying to overwrite `/usr/share/apps/konqueror/servicemenues/media_safelyremove.desktop', which is also in package kio-umountwrapper
dpkg-deb:subprocess paste killed by signal (Brocken pipe)
Eroors were encountered while processing:
/cdrom//pool/main/k/kdebase/konqueror_3.5.9-0ubuntu7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So it is a broken kio-umountwrapper that is causing the problem.

thanks for your patience guys, any more suggestions?

---

### Post by argail1980 on 2008-06-15
have you tried to revive the network? what kind of connection d'you have?

---

### Post by maninalift on 2008-06-15
curiouser and curiouser.

I restarted the computer, thinking that perhaps it is only konq that has not been installed.

I get my nice graphical login screen but then when I log in I get a black square in the top-right corner with the command prompt in it (the rest of the screen still has the login background and the cursor which I can move around the screen).

The same when I login in failsafe mode.

Thought rather than reboot I'd "exit" the session.... bad idea. The screen is full of characters in pink blue cyan magenta green... some of them flashing. Crazy.

Have to force shutdown (hold down power key)

Edit: back to the terminal (in the corner of the screen - at least I can scroll up and down now). apt-get still returns the same errors for -f install and  install kubuntu-desktop.

---

### Post by maninalift on 2008-06-15
OK. I started up KWin, kdesktop and kicker. I have some form of desktop functioning though it is all spawned from this uxterm window. I still have issues with broken packages. I can't install konqueror and stuff.

Any ideas?

---

### Post by prshah on 2008-06-15
> **maninalift said:**
> 
I get my nice graphical login screen but then when I log in I get a black square in the top-right corner with the command prompt in it (the rest of the screen still has the login background and the cursor which I can move around the screen).


Try this in the (emulated) terminal: ```

sudo /etc/init.d/kdm start
```

--OR--

switch to Ctrl+Alt+F1, login, give the command
```

sudo /etc/init.d/kdm restart
```

, then when you get the [OK], switch back with Ctrl_Alt_F7.

---

### Post by maninalift on 2008-06-15
Thanks for that. The trouble is there is an underlying reason why kdm is not starting up in the normal way.

This broken pipe thing is messing with the package management for a start. I feel like the best bet at this stage is to reinstall from scratch. The trouble is I only have a single partition and I don't fancy backing up all my data to DVDs. GParted can't deal with mounted partitions (I'm not sure whether there is a fundamental reason why this is not possible on linux but is possible on windows with partition magic).

Maybe I can free some space on my external hard disk.

Any suggestions.

---

