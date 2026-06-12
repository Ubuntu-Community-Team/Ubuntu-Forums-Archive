---
title: "Problems installing VMWARE Workstation 5.5"
date: 2006-07-01
forum: General Help
---

### Post by Giga on 2006-07-01
I got the .RPM file from vmware website
convert to .deb using alien.
alien -c -s vmware....  .deb
the package installer give me the status: " all dependecies are satisfied" 
i tried to install with debian dpkg and i got the error:
failed to install vmware....  .deb

There was a lock thumbnail in front of the folder..
This is why the window GRANT option pops up before start install right?
So i click on GRANT button
got the same error:
*failed to install FILANEME.deb*

So i quit and went to .tar.gz file format of vmwareworkstation 5.5 (thinking it would be easier)

i got build-essentials from Synaptic
i got linux headers 2.6.15-25-386 (my system is 386) from Synaptic
i uninstalled vmwareplayer (that i tested before and worlks well) by synaptic
(I used advanced mode, and unkmark ALL vmwareplayer options listed

finally.. i tried:

oem@ubuntu:~/Desktop/vmware-distrib$ sudo ./vmware-install.pl
Password:
A previous installation of VMware software has been detected.

Failure

Execution aborted.


Can someone please, give me a light????  What im doing wrong here?

---

### Post by digimars on 2006-07-01
It's been a while since I installed it, but I had to follow the instructions that VMWare provided in their PDF to the letter because my initial installation failed.  Something else that I think I had to do was when I ran alien, I had to specify --scripts along with the command.

You might want to remove your installation, get their installation PDF and try out --scripts along with the alien command.

---

### Post by Giga on 2006-07-01
i run with scripts " alien -c"

the problem now is: How i can get rif off from: "  previous instalation detected" 

As far as i know... there is no vmware installed..

---

### Post by fritz_monroe on 2006-09-05
I'm hoping someone else will be able to add to this.  I am also having this exact same problem.

I installed VMPlayer.  Tested out great.  I then uninstalled it and tried to install VMWare Workstation.  It complained with the same error.  I found that in /etc/init.d, there was a vmware-player link.  I used a vmware-player status and it was running even though the app was uninstalled.  I stopped it from running and ensured that there was nothing in Synaptic listing vmware.  Tried to install is again, and get the same error.

Anyone else have any suggestions?

---

### Post by fluid on 2006-09-06
just delete this directory (after uninstall) with

rm -rf /etc/vmware

then you should be able to install vmware workstation!


fyi: in /etc/vmware there are some old config-files left... i had the same problem, after deleting this directory the installation worked.

---

### Post by fritz_monroe on 2006-09-07
Unfortunately, this didn't work for me.  I uninstalled everything vmware related and deleted the folder.  When I tried to install, it gave the same error.

So what I did was created the virtual machine using qemu.  I then installed XP.  The system works great, but I've got another issue.  I can't get it to recognize the virtual network.  It says I don't have a network card.  but that's another thread.

---

### Post by gruffy-06 on 2006-10-04
Virtual Machines have problems when imported from Qemu to VMware.

---

