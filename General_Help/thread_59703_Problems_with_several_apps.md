---
title: "Problems with several apps"
date: 2005-08-25
forum: General Help
---

### Post by GoA on 2005-08-25
Hi, I have several problems in my machine and I think it's because of the backports. Yesterday morning I had some package problems with my Ubuntu, such as firefox, gaim and gimp. I tried to reinstall them but I only managed to remove them, not to install back so I  installed my ubuntu again. Last night after the system update it was the same situation. Also I cannot install java (did it another way), azureus which is java dependent, update mozilla, gaim, gimp.. And this is quite annoying. How should I be able to use my system if I cannot instlal a darn thing? I know there was a DoS attack on the forums but it shouldn't effect backports. Also I haven't found any info about the situation. If something is broke then at least let us know about it. This kind of situation is annouying.

---

### Post by bob k on 2005-08-25
You should start with this link after a fresh install. (download 5.04 and make an iso cd)

[http://www.ubuntuforums.org/showthread.php?t=22646](http://www.ubuntuforums.org/showthread.php?t=22646)

This will install every thing you need to get running.

you will have setup your mouse if it has side buttons and there is a numlock program that has to be setup.

after that it's just prefernces.

2 hours max

---

### Post by GoA on 2005-08-25
Yes that's the smart thing to do after re-install. However that isn't the problem. I know how to install all the things I need in my system. The problem is that the ubuntu update manager/the backports won't work properly I actually don't know what's the problem. I just know that after a fresh install there already something wrong with the system/repositories.

---

### Post by bob k on 2005-08-25
I thinkI need a little nore information. What's not installing right, and why do you think it's the repository's

---

### Post by GoA on 2005-08-25
Ok, let's start from the beginning. About three weeks ago I installed Kubuntu which worked like a charm. I tryed all kinds of things, adjustments and tweaks. I also installed Gnome into it and later removed KDE. It still worked perfectly. After that I upgraded to breezy which was a mistake so I formated my harddisk and installed basic ubuntu with gnome. After I got first time into to desktop I installed a new 686 kernel to get my 1 gb of ram used. It worked. After that I allowed ubuntu update manager to update the system. It gave me the following error: 

It is not possible to upgrade all packages.

This means that besides the actual upgrade of the packages some further action (such as installing or removing packages) is required. Please use Synaptic "Smart Upgrade" or "apt-get dist-upgrade" to fix the situation.

Following packages are not upgraded

mozilla-firefox
mozilla-firefox-gnome-support
smbclient
gaim
gimp

Ithought this was my fault so I removed them completely and tryed to reinstall. However that wasn't possible. Synaptic gives me this: mozilla-firefox:
 Depends: firefox  but it is not installable

However Synaptic doesn't show that any packages are broken. So because I didnät have any programs to use I did another reinstall. After the installation I first updated the system with update manager and the same error comes. I also upgraded kernel after that and started to do little searching of forums. I tried different repositories and I managed to update gimp and gaim. But still firefox is broken. And it doesn't find java.  

So I installed java with warty guide and managed to get it work. However synaptic doesn't understand that  because when I try to install azureus it says it's dependent on java which isn't found and cannot continue installation. 

The repositories which I use are the one in the Ubuntuguide. 

And because after repositories change I was able to upgrade gimp and gaim I think the fault is in there. 

But help, do I have to do another reinstall and make something different? Like use only terminal for install and upgrade or something else?

EDIT: [http://ubuntuforums.org/showthread.php?p=317724#post317724](http://ubuntuforums.org/showthread.php?p=317724#post317724)

---

### Post by bob k on 2005-08-25
I got the same error when I did this last install, and when I checked the versions they were current, so I didn't worry about them, and every time I do a synaptic I still get 5 applications held back. I would assume this is load that was built before the repositorys were updated.

---

