---
title: "apt-get problem"
date: 2007-09-09
forum: General Help
---

### Post by swoskow on 2007-09-09
When I boot Ubuntu it puts me in a command line and says to install apt-get by apt-get install.  I do this but it will not install.  I exit and it finishes the boot.  In a terminal I tried the same command apt-get install and get the messsage that I am missing power management dependencies (this is not a laptop).  I hope someone can help.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu6) ...
 * Loading ACPI modules...                                                                     [ OK ] 
 * Starting ACPI services...                                                                          invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 gnome-power-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by rsambuca on 2007-09-09
Did this ubuntu installation ever work?  or did it start doing this recently?  If the latter, what were you doing prior to this?  Details please.

---

### Post by nowshining on 2007-09-09
it says what it says you are missing dependencies - what ubuntu version are you running - feisty ??

---

### Post by swoskow on 2007-09-09
> **rsambuca said:**
> Did this ubuntu installation ever work?  or did it start doing this recently?  If the latter, what were you doing prior to this?  Details please.

yes - it has been working for awhile and it works now.

---

### Post by swoskow on 2007-09-09
> **nowshining said:**
> it says what it says you are missing dependencies - what ubuntu version are you running - feisty ??

yes feisty

---

### Post by nowshining on 2007-09-09
is this the first install - meaning that you just installed it and such or have you had it for awhile, because let me tell u gutsy fixes those dependency problems by doing it automatically when downloading.. :) compared to feisty tho. - just some inf..

---

### Post by swoskow on 2007-09-09
> **rsambuca said:**
> or did it start doing this recently?  If the latter, what were you doing prior to this?  Details please.

it just started doing this.

i was not doing anything special.  just using it.  i didn't even install any new packages.  i did have a problem that ubuntu just stopped booting.  in the log in screen it would give a message the the last session only lasted 10 seconds and it needed to start in a safe mode.  for some reason it showed my root partition was full (i had 40 gb set aside for root.  I used the gparted live cd to increase the size of the root partition and it booted OK after that.

---

### Post by swoskow on 2007-09-09
> **nowshining said:**
> is this the first install - meaning that you just installed it and such or have you had it for awhile, because let me tell u gutsy fixes those dependency problems by doing it automatically when downloading.. :) compared to feisty tho. - just some inf..

see my previous post about expanding the root partition - that might help.  No - i did not just install this.  it has been installed for at least 6 months

---

### Post by nowshining on 2007-09-09
do this open up a terminal and note if you ever have auto log out you can try this also..
 
open up a terminal
 
sudo rm ~./gnome2/session



and reboot and see what happens now..

---

### Post by swoskow on 2007-09-09
> **nowshining said:**
> do this open up a terminal and note if you ever have auto log out you can try this also..
 
open up a terminal
 
sudo rm ~./gnome2/session



and reboot and see what happens now..

it gave the following:
rm: cannot remove `~./gnome2/session': No such file or directory

I am rebooting now

---

### Post by nowshining on 2007-09-09
hmmmm...

---

### Post by swoskow on 2007-09-09
I rebooted and the same message came up - it wants me to install apt-get still

---

### Post by nowshining on 2007-09-09
try going in there to manually delete it - that command really worked once on me ..

however open up the filemanager - (in other words click something to open up the browse files such as computer....

go to view - show hidden files or ctrl + h on the keyboard

navigate to your home folder

find .gnome2 

(hidden files / folders are hidden with a dot in front of the name)

and delete the sessions folder..

maybe the command is wrong i gave - hmmm i gotta recheck that one tho..

---

### Post by rsambuca on 2007-09-09
Did you say 40GB for root?  And it is full?

You are having a gdm/gnome issue, and I honestly don't think these type of errors just appear out of nowhere. There must have been something you were changing.

---

### Post by nowshining on 2007-09-09
the problem tho is actually this line
 
* Starting ACPI services... invoke-rc.d: initscript acpid, action"start" failed.
 
it loads them tho, but seems to be unable to invoke or start up that certain script..odd...

---

### Post by swoskow on 2007-09-09
yes 40 gb - no it is not full.

---

### Post by swoskow on 2007-09-09
just to clarify - it was full but i expanded the root partition so now it is not full

---

### Post by rsambuca on 2007-09-09
You keep contradiction yourself.  First it is full, now it isn't?

Edit: ahh, ok.

---

### Post by nowshining on 2007-09-09
um did you do an upgrade or full install ??

---

### Post by swoskow on 2007-09-09
> **rsambuca said:**
> You keep contradiction yourself.  First it is full, now it isn't?

Edit: ahh, ok.

sorry -   it was full at 40 gb so i expanded the partition using gparted to 55 gb and now it is not full after i expanded.

---

### Post by swoskow on 2007-09-09
an upgrade using the alternate cd

---

### Post by nowshining on 2007-09-09
that might be ur problem [http://www.linuxforums.org/forum/ubuntu-help/66332-e-sub-process-usr-bin-dpkg-returned-error-code.html](http://www.linuxforums.org/forum/ubuntu-help/66332-e-sub-process-usr-bin-dpkg-returned-error-code.html)

seems like they did an upgrade - the answer was not final on that and that link is old but It may be the source of your problem in the end and a full re-install would be a fix - be sure to make backups tho..

---

### Post by swoskow on 2007-09-09
> **nowshining said:**
> that might be ur problem [http://www.linuxforums.org/forum/ubuntu-help/66332-e-sub-process-usr-bin-dpkg-returned-error-code.html](http://www.linuxforums.org/forum/ubuntu-help/66332-e-sub-process-usr-bin-dpkg-returned-error-code.html)

seems like they did an upgrade - the answer was not final on that and that link is old but It may be the source of your problem in the end and a full re-install would be a fix - be sure to make backups tho..

it is similar.  i was hoping to avoid a complete re-install if possible.  anyway, that is what it may come to or i may just leave it since it does not appear to be affecting anything accept at boot.

also, thank you for you very much for helping

---

### Post by nowshining on 2007-09-09
your welcome - but someone may have a fix, I only found few google links unless u know other languages you can try out those - I only did the english one...

search google for

"* Starting ACPI services... invoke-rc.d: initscript acpid, action"start" failed"

Again I only did quotes you can try without them..

---

### Post by swoskow on 2007-09-09
> **nowshining said:**
> your welcome - but someone may have a fix, I only found few google links unless u know other languages you can try out those - I only did the english one...

search google for

"* Starting ACPI services... invoke-rc.d: initscript acpid, action"start" failed"

Again I only did quotes you can try without them..

OK - i'll keep trying

---

### Post by swoskow on 2007-09-09
i did more reading and i found a few posts relating to the apt-get and fsck. ([http://ubuntuforums.org/showthread.php?t=546864&highlight=fsck](http://ubuntuforums.org/showthread.php?t=546864&highlight=fsck)).  

This is the cause of the problem - my /var/log/fsck is showing the following message " /dev/md1 contains a file system with errors, check forced"  /dev/md1 is a raid 5 with 4 hard drives.  i scanned the hard drives with mdadm and it is not showing any problem wit the discs.  i can also read/write etc to the raid discs.  it wants me to run fsck manually without -a or -p options but i am not sure how to do this (i am trying to read now to find out how).  thier must be something in the disc check that is not right.

---

### Post by swoskow on 2007-09-09
The entire output reads:
dev/md1 Inode 905410 has imagic flag set
dev/md1: unexpected Inconsistencies: run fsck manually (i.e. without -a or -p)
fsck died with exit 4 status

---

### Post by nowshining on 2007-09-09
ahhh more info. great :) now your teaching me.. :P

---

### Post by swoskow on 2007-09-09
nowshining - thanks for sticking around.  

I have been following this thread but I am not getting too far.  my raid devices don't have the uuid in the /etc/fstab [http://ubuntuforums.org/showthread.php?t=364216&highlight=imagic+flag+set](http://ubuntuforums.org/showthread.php?t=364216&highlight=imagic+flag+set)

---

### Post by nowshining on 2007-09-09
so is problem 1 fixed or not and ur welcome ??

---

### Post by swoskow on 2007-09-09
i ran the fsck and it is saying i have bad files sectors on my raid devices.  I have 2 raid set ups (md0 and md1) - the fsck for md0  showed a bad sector and fixed it.  the fsck for md1 said too many bad sectors to fix. i unmounted the 2 raid devices and rebooted but the same happened.  it must be something to do with a file sytem on md1 but all the disks are working fine and the scan by mdadm showed nothing wrong with the disks.  not sure what to do except save everything on the raid dev and reconfigure it.  any other suggestions?

---

### Post by nowshining on 2007-09-09
i don't have a raid setup altho I was remembered I got an extra pci board to add more hard drives - I was having a problem with a computer that when I finally found out the CMOS chip went out..and was hoping when I did break pins on it that would fix it but it didn't work and it said raid on it..anyway...

back on topic... I have no clue as to continue but google keywords or yahoo them or clusty.com them..or any search engine for that matter, however u'll have to wait until someone will hopefully come along, unless you want to backup and format and do a FULL install... and go from there.....which I believe would be better.. what OS did you upgrade from anyway..

---

### Post by swoskow on 2007-09-09
i will hang out and see if anyone might be able to help.  i have had ubuntu on this computer for awhile now.  originally it came with xp.  i initially installed the version of ubuntu just before feisty (i think it was dapper) then upgraded to fiesty once it came out (maybe once gutsy is ready an upgrade might fix the problem).  i really don't think it is the disks but i guess it could be the file system.  not sure, but I will back everything up and in the meantime maybe someone will help.

is there something like defragging in ubuntu or is that what fsck does?

again thanks for you help - I really appreciate it.

---

### Post by nowshining on 2007-09-09
i really see it as the upgrade part - one thing I didn't mention and just remembered was that compared to earlier versions the Hard drives used the ATA driver for IDE ones, that changed in Feisty where the SCSI drivers both manage ATA and SCSI drives...which could explain the problem and the need to do a full feisty install edit: to fix the problem wholly :edit or like u said stick with it and then get gutsy and then backup and then do a format and re-install since Gutsy is about a month away..

---

### Post by swoskow on 2007-09-09
> **nowshining said:**
> i really see it as the upgrade part - ..
I agree - searching the forums, shows a fair amount of posts with this problem and they all seem to develop after upgrading.

---

### Post by nowshining on 2007-09-09
so what's your FINAL decision ?? or have you chose one yet??

---

