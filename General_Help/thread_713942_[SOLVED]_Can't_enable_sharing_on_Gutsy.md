---
title: "[SOLVED] Can't enable sharing on Gutsy"
date: 2008-03-03
forum: General Help
---

### Post by linuxjerk on 2008-03-03
When I try to enable folder sharing on my new install of Gutsy I get this error:

Sharing services are not installed
You need to install at least either Samba or NFS in order to share your folders.
Install Unix networks support (NFS)
Install Windows networks support (SMB)
Close Install Services


When I push the "Install Services" button the error just pops back up.

I checked in synaptic manager and both services listed in the error are already installed.

Tried some of the ways to check if the services are functioning and it doesn't work. i.e. 

sudo  /etc/init.d/samba start

sudo /etc/init.d/nfs-common start

Is this a failed install or am I loosing my mind???????????

---

### Post by linuxjerk on 2008-03-03
Is this a known bug???

Why does no one know anything about this??

---

### Post by linuxjerk on 2008-03-03
Can some one please help me on this?

---

### Post by westdj8 on 2008-03-03
Hey - same problem here . . . synaptic manager says Samba-common and smbclient are installed.    But get the repeating "please install" error when opening shared folder administration

sorry for no help - this is a brand spakin' new install, I can't imagine what I messed up.  my net connection / sound / video worked right off the bat

---

### Post by altonbr on 2008-03-03
I've never enabled Folder Sharing your way, can you please reproduce the steps?

---

### Post by westdj8 on 2008-03-04
Alton - hope you can help - maybe post your method for setting up file sharing?

My steps:

Start w/ old PC and new blank HD   (*PC specs below)
Boot from GG 7.10 CD and choose "install"
Re-boot from HD (remove CD/update bios boot order)

Tried pull down menu: "System -> Administration -> Shared Folders"

I literally haven't installed a single piece of software, or changed any settings from the default install.

thanks in advance for helping a noob

PC:  ASUSA7V333 mobo
Athlon XP2000  proc
256MB ram
200GB Western  Digital drive PATA133
?? video card

---

### Post by linuxjerk on 2008-03-04
SOLVED      SOLVED         SOLVED

Let this be a lesson to me!!!


go to:   system, administration, sofware sources      (check all the boxes)

When that's done loading you can install all restricted software.

Linux never ceases to test my patience!!!!!

---

### Post by altonbr on 2008-03-04
> **linuxjerk said:**
> SOLVED      SOLVED         SOLVED

Let this be a lesson to me!!!


go to:   system, administration, sofware sources      (check all the boxes and press revert)

When that's done loading you can install all restricted software.

Linux never ceases to test my patience!!!!!

That solution doesn't seem to make much sense since you just said "check all the boxes and the click 'revert' to restore original check boxes"... which means, whatever you did, didn't do anything.

Sorry if I misunderstand, but that's what it looks like.

---

### Post by linuxjerk on 2008-03-05
sorry my mistake. I didn't mean to say press revert.

---

### Post by westdj8 on 2008-03-05
So I got Samba installed, and my windows machine can see it on the network, but I can't login/view files.

Likewise, my ubuntu box can see tho other windows PCs, but not open/view their shared folders.

Any idea what setting I could change?

---

