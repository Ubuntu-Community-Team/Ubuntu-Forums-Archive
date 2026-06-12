---
title: "random question from old guy to new guys"
date: 2024-10-05
forum: General Help
---

### Post by cryofreeze666 on 2024-10-05
back in the day when a person accidentally wiped their drives out, you'd use dos to redefine the drive sectors.  i never really thought about it before today but, reformatting, is that just an automated version of redefining the drive sectors.  i'm assuming it is, i'm just asking out of curiosity, and to make sure i'm not assuming incorrectly.  thanks

---

### Post by sgt-mike on 2024-10-06
Just another old guy but last time I recall having to supply the sectors was old SCSI and MFM drives. When IDE drives came long and DOS was kind of dead because Windows integrated  DOS then came along the SATA (which IDE can still be used with a adapter on SATA) I do not recall ever having to tell the OS after integration how to define sectors on a logical device. 
BUT depending on what one desires you can change sectors to the OS when formatting.

side bar remember OS/2? that was IBM's answer to replace Windows (I might still have a copy of that OS laying around)
 
```
I like to use sg_format for this and there are MANY ways to do it in Linux other than sg_format
Example
sg_format -v --format --size=512 /dev/sg2

That sg2 refers to the third logical device. which you really don't see unless use the appropriate command
Or for the same drive that you see in say lsblk or blkid

sg_format -v --format --size=512 /dev/sdc


```

[IMG]https://qph.cf2.quoracdn.net/main-qimg-e6a8abc5d537de519933b9a12b5ca293-lq[/IMG]

In today's dollars that would be [COLOR=#8B0000][FONT=&amp]$9241.80   
[/FONT][/COLOR][COLOR=#000000]The average car was about $6000.00 new [/COLOR]

---

### Post by cryofreeze666 on 2024-10-06
sgt mike. your brother must be a mountain, mines just a plain.  my first computer was a trash 80, though my dad did get me radio shack's version of pong before that. 

if i could remember the code i'd tell ya, it wasn't more than 50 lines if i remember correctly.

it said things like a to b, b to c, c to d
ab to bc, blah blah blah.

i'm only remembering the value names, hell i can honestly say i don't remember dos.  not that i used it often.  i usually just copied from a printout  stored in a worn out spiral notebook of **** ya needed, but not that often.

---

