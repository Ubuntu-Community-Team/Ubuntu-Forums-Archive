---
title: "Error Installing Kernel"
date: 2008-05-15
forum: General Help
---

### Post by NOC on 2008-05-15
Ubuntu Studio.
 
When I try to install Ubuntu Studio on the entire disk, I get this exact message:
 
********************************************
***An error occured while trying to install the kernel to the target system.***
 
***Kernel package: 'linux-rt'***
 
***Check  /var/log/syslog or see virtual console 4, for the details.***
********************************************
 
This is a brand new hdd.  If I partition my disk, install XP, then Kubuntu, I am up and running.
 
This studio version looks **very cool!**
 
But I just keep ](*,)!!  I just want to :guitar:!!
 
Does anyone have an idea what can be happening?
Thanks
-Trying to convert

---

### Post by hermes0710 on 2008-05-16
Can you post the contents of the virtual console 4 as it says? (ctrl+alt+F4 when the errors are prompted)

---

### Post by NOC on 2008-05-17
I would but I have already wiped the drive and installed Kubuntu next to winxp. currently win xp is my primary system but as you can see I'm trying to get away from windows. if i run that install again, i will have messed up the boot loader for windows, 
When I tried to install Ubuntu Studio on a disk with Windows, after the error, xp was not able to boot, I got "operating system not found"
I appreciate your help, but if you know of a way to get the computer to *find* the xp install after the failed Ubuntu Studio install, I may try it again, but now that I have Kubuntu installed, what roadblocks do I run into if I want to wipe Kubuntu and re-try Studio... i believe, from a different post, there is a way to fix that boot loader problem. if you know of some boot disk manager, please advise. I have UBCD, but have really only used Ranish...is there something on there.
 
Currently, xp and kubuntu are on the same disk working fine.
 
Maybe I should try to install Ubuntu studio on an external USB disk.
 
I'm a little bit of a machine head but I also need to be productive as well that's why I went back to Kubuntu.
 
thanks in advance!

---

### Post by sdennie on 2008-05-17
You should be able to install all the ubuntu studio components within kubuntu or regular ubuntu by installing all the ubuntustudio packages.  Something like this from a terminal should do the job:

```

sudo apt-get install ubuntustudio-*

```

---

