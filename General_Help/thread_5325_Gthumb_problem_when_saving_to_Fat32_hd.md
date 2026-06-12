---
title: "Gthumb problem when saving to Fat32 hd"
date: 2004-11-17
forum: General Help
---

### Post by neutron on 2004-11-17
Hya all!

I'm having a problem on my Ubuntu laptop with Gthumb. When I try to import my photo's from my Canon Powershot A40 digicam. I always save my photo's to my fat32 partition, so I've acces to them in windows too.

I tried to save the photo's on the fat32 partition, but everytime I got 
an error:

```
Could not import photos

Could not create the folder "/mnt/Data/Docs/My 
Photos/test/2004-11-17--12:34:29": Invalid parameters
```
When I lauch gthumb from the terminal I get: 
```
(gthumb: 3980): WARNING **: 
directory creation failed: /mnt/Data/Docs/My 
Photos/test/2004-11-17--12:34:29

```
When I issue 'save' for a 2nd time the application crashes. 

At first I thought there was a problem with my permissions in fstab. 
However, however every other program can actually save on that patition.
I've changed my fstab from:

/dev/hda5	/mnt/Data	vfat	rw,user,noauto	0	0

to:

/dev/hda5	/mnt/Data	vfat	rw,users,uid=1000	0	0

... but I still get the same error. When I create the folder 'test' manually it still refuses to work by the way. Launching gthumb as root  doesn't matter either.

I'll hope that I've listed all the important things. Maybe someone can check if this is reproducable on his pc. Or does anyone has a solution for this nasty problem?

Thnx in advance  :D

---

### Post by neutron on 2004-11-18
[QUOTE=neutron]Hya all!

I'm having a problem on my Ubuntu laptop with Gthumb. When I try to import my photo's from my Canon Powershot A40 digicam. I always save my photo's to my fat32 partition, so I've acces to them in windows too.

I tried to save the photo's on the fat32 partition, but everytime I got 
an error:

```
Could not import photos

Could not create the folder "/mnt/Data/Docs/My 
Photos/test/2004-11-17--12:34:29": Invalid parameters
```
When I lauch gthumb from the terminal I get: 
```
(gthumb: 3980): WARNING **: 
directory creation failed: /mnt/Data/Docs/My 
Photos/test/2004-11-17--12:34:29

```
When I issue 'save' for a 2nd time the application crashes. 

At first I thought there was a problem with my permissions in fstab. 
However, however every other program can actually save on that patition.
I've changed my fstab from:

/dev/hda5	/mnt/Data	vfat	rw,user,noauto	0	0

to:

/dev/hda5	/mnt/Data	vfat	rw,users,uid=1000	0	0

... but I still get the same error. When I create the folder 'test' manually it still refuses to work by the way. Launching gthumb as root  doesn't matter either.

I'll hope that I've listed all the important things. Maybe someone can check if this is reproducable on his pc. Or does anyone has a solution for this nasty problem?

Thnx in advance  :D[/QUOTE]
 Does anyone has a clue?

---

### Post by mr_ed on 2004-11-18
I'm pretty sure you want 
/dev/hda5 /mnt/Data vfat rw,users,umask=0

---

### Post by neutron on 2004-11-23
[QUOTE=mr_ed]I'm pretty sure you want 
/dev/hda5 /mnt/Data vfat rw,users,umask=0[/QUOTE]

Unfortunately this doesn't make any difference  :cry: 

Thnx anyway!

---

