---
title: "shutdown dooes not flush disk caches"
date: 2012-11-02
forum: General Help
---

### Post by marcelo_ni on 2012-11-02
On my Ubuntu 10.04, the shutdown command does not flush disk caches. 
So, after a reboot, the filesystem must be fixed in a maintenance shell. 
Of course, I fear that some time the damage could prevent boot at all.

The only secure way is the famous key sequence (RSEIU while pressing alt-ctrl-sysreq), but of course, it is not very comfortable nor handy.

Does someone experiment similar troubles? Does someone know an alternate/complimentary pathway?

TIA

Marcelo

---

### Post by ajgreeny on 2012-11-02
What happens if you use the terminal command ```
sudo shutdown -h now
``` How do you usually shutdown?
Are you saying that the system runs **fsck** at each boot or that you have to run it manually to be able to boot?

I never see any problems using the standard menu shutdown method, the Quit button I added to the panel, or the keyboard key on my media keyboard which is assigned to shutdown and labelled "Power".

This also applies to other versions of the *ubuntu family I use, or have used in the past, all of which work faultlessly in that respect.

---

### Post by marcelo_ni on 2012-11-02
Only way to shutdown or restart without some filesystem corruption is the magic key sequence (RSEIU etc)

When the filesystem get "damaged", it gets checked during bootstrap, the checks fail, and I get a "maintenance shell" where I run fsck, telling "y" to all fixes, and after that, rebooting thru "shutdown -r now".

And of course, sometimes the filesystem recovery is not complete. Today I lost some of the config elements for claws-mail.

---

### Post by dcstar on 2012-11-03
> **marcelo_ni said:**
> On my Ubuntu 10.04, the shutdown command does not flush disk caches. 
So, after a reboot, the filesystem must be fixed in a maintenance shell. 
.......

Check the sequence orders of the /etc/rc0.d and rc6.d script folders.

I have seen these totally corrupted by installing a version of VMware Player a while back (fixed now).

You may need a working 10.04 system to see the correct order and then manually rename all the bad ones.

---

### Post by marcelo_ni on 2012-11-03
Thank you, David.
That is exactly the scenary: I had installed VMWARE Player, and now, VMWARE Workstation, which is what I'm using.
So, I would need to make another virtual box with a fresh 10.04. 
Don't know if I have the CD. Is't possible to download it from the Canonical site?

---

### Post by marcelo_ni on 2012-11-04
Sadly, the /etc/rc0.d and /etc/rc6.d dont differ significatively  between my current system and a freshly installed one. Of course, not regarding the lot of extra scripts in the production system, due to installed software. 

The only prefix differences are as follow (of course, I'm reporting on the common scripts)

K02bluetooth           K74bluetooth     
S01unattended-upgrades        S10unattended-upgrades
S02wpa-ifupdown             S15wpa-ifupdown
S02urandom           S30urandom

Moreover, these scripts obviously have no relation to the disk caches flushes

The rest of common files:

S20sendsigs
S31umountnfs.sh
S35networking
S40umountfs
S60umountroot
S90reboot / S90halt

are the same. And, in the production system, S90umountnfs is near the end of the list, just before S60umountroot and S90reboot or S90halt.

Some more ideas?

---

