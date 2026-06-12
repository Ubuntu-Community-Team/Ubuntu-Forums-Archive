---
title: "Can't install backup utilities in 11.04"
date: 2013-05-04
forum: General Help
---

### Post by Aurora on 2013-05-04
Hi,

Time to upgrade to the next LTS; 11.04 is no longer supported.   I'm running the Studio variant on a Lenovo T510 laptop. I want to back up my files first.  I always did that manually, with disorganized results, so wanted to try a utility.  I tried to install sbackup, dejadup, and backuppc, but none of them would install.  I get various errors depending on whether I use the terminal, Synaptic, or the Software centre.  I'll show you some terminal results:
pad@ubuntu:~$ sudo apt-get install backuppc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 backuppc : Depends: libarchive-zip-perl but it is not installable
            Depends: libtime-modules-perl but it is not installable
            Depends: libsocket6-perl but it is not installable
            Recommends: libfile-rsyncp-perl (>= 0.68) but it is not installable
            Recommends: rrdtool but it is not installable
            Recommends: libio-dirent-perl but it is not installable
E: Broken packages
pad@ubuntu:~$ sudo apt-get install grsync
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package grsync
pad@ubuntu:~$ sudo apt-get install sbackup
[sudo] password for pad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package sbackup
pad@ubuntu:~$ sudo apt-get install dejadup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dejadup
pad@ubuntu:~$ 

Software Center gives me "dependencies cannot be resolved" for dejadup and backuppc; it cannot find sbackup.

Synaptic can only find backuppc; it says "fix broken packages first!"

I realize 11.04 is unsupported, but I didn't think that meant I couldn't install standard packages.  Maybe something is messed up on my system.
Is there anything shipped with 11.04 I can use?  I can open a terminal and use rsync, but I was hoping for something easier.  I am unsure how to save just the files, not all the settings and other stuff,  from my home folder.   I tried to insall grsync as well, to no avail.

If I plug in a usb key with 12.04 while 11.04 is running, it asks me to upgrade. Would that put my data in peril?  I'm tempted.

~Paul

---

### Post by Bucky Ball on 2013-05-05
Can't you just drag and drop the contents of your /home onto the backup media? You don't need 'Desktop' or the hidden folders. Remember to grab your email and browser bookmarks also. Then do a clean install of 12.04 LTS (supported until April 2017 incidentally).

---

### Post by Aurora on 2013-05-09
> **Bucky Ball said:**
> Can't you just drag and drop the contents of your /home onto the backup media?

You mean manually copy each file, one at a time?  I suppose I could.  That would be a last resort.  Is there no way to do this as a batch process?  I could use rsync, but I  don't know how to exclude hidden files and such...it would copy over the whole thing, which would be less than optimal but OK.  Do you recommend a clean install over an upgrade?  I have a Wubi installation; I guess just delete it and start over?  Or I could partition, old-school.  The wubi was so easy compared to the old way, but there are advantages to having everything separate.

~PD

---

### Post by Bucky Ball on 2013-05-10
A clean install of Wubi to 12.04 LTS Wubi? Yes. I had no idea you could upgrade Wubi any other way. Wubi is just like using any other Windows program and that's the way it's installed. Not considered a permanent solution and intended for users to try out Ubuntu before doing a real install to a separate partition.

If you are talking about a clean install of Ubuntu to it's own partition (not Wubi) over an upgrade, then yes, I would go the clean install.

Always make it clear you are using a Wubi install to avoid confusion. It is a totally different kettle of fish to Ubuntu installed to a partition (and is not a dual-boot).

---

