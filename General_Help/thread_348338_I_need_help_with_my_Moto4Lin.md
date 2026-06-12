---
title: "I need help with my Moto4Lin"
date: 2007-01-28
forum: General Help
---

### Post by ubageek on 2007-01-28
Hey everyone out there in the great, vast network, I need some help with Moto4Lin, I recently downloaded it and it loads up and everything but it just doesn't want to connect to my razer v3i, can anyone help me because this is really annoying me, If anyone can help that would be totally awesome.

---

### Post by phersotty on 2007-01-28
I didn't even know there was such a thing.  I am checking it out right now.
Have you looked at the how to ?  [http://www.ubuntuforums.org/showthread.php?t=56253&highlight=moto4lin]("http://www.ubuntuforums.org/showthread.php?t=56253&highlight=moto4lin")

---

### Post by phersotty on 2007-01-29
moto4Lin works !! on my V3 razr.  At first it wasn't working because I over looked > Set 'ACM Device' = '/dev/ttyACM0'  I think if you follow the guide it should work for you too!!  Good luck !!

---

### Post by wormser on 2007-10-07
> **phersotty said:**
> moto4Lin works !! on my V3 razr.  At first it wasn't working because I over looked  > Set 'ACM Device' = '/dev/ttyACM0'  I think if you follow the guide it should work for you too!!  Good luck !!



This worked for me too.

---

### Post by amh4501 on 2007-11-14
hi everyone i'm a newcomer so please be patient i'm trying to use moto4lin to manage music on my verizon razr v3m and just can't seem to get it to work not sure what i'm doing wrong i'm running fiesty fawn and my device is set to /dev/tty/acm/0 and every time i try to change it to /dev/tty/ACM0 then close the preference window it reverts back to the previous is it the same thing? any way i just keep getting [info] Phone is unpluged. Please connect it
[info] Phone pluged as AT
[info] Switching device /dev/ttyACM0 to P2K mode...
[info] AT E0 answer: AT E0 
[info] Phone answer: OK 
[info] Phone is unpluged
[info] Phone pluged as P2K
Getting file list
[error] Unable to get drive list
Complete
Try to connect
[info] Interface 0 is claimed by cdc_acm.
[info] Driver cdc_acm detached from interface 0
[info] Phone connected as P2K
[error] Unable to get phone model
[error] Unable to get drive name
[error] Phone is busy. Please try later
[error] Unable to get file count
[error] Unable to get drive name
Try to disconnect
[info] Phone disconnected
[info] Switching device /dev/tty/acm/0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
Getting file list
[error] Unable to get drive list
Complete
  any suggestions on a resolution or pointers would be appriciated is it maybe because it's a verizon phone

---

### Post by cornelius2 on 2008-01-05
> **amh4501 said:**
> every time i try to change it to /dev/tty/ACM0 then close the preference window it reverts back to the previous is it the same thing? any way i just keep getting [info] Phone is unpluged. Please connect it


I have the same problem on Gutsy. Is there a solution to this?

---

