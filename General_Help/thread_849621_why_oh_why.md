---
title: "why oh why?"
date: 2008-07-04
forum: General Help
---

### Post by BuffaloX on 2008-07-04
I am just wondering...
Why must I give password to mount a partition, when I can mount all sorts of external devices without password?
I understand it's some sort of security issue, but I don't understand how security is different for my external drive which auto mounts :) when I plug it in, or my internal drive which I mount manually.
The mount binary cannot be given SU rights with the 
> sudo chmod u+s,

this is blocked for some weird reason. :confused:
Especially weird since I can mount it fine by clicking the drive in nautilus.
PS
I just want to mount manually, to select a more descriptive mountpoint.

Just one of those little things. :lolflag:

---

### Post by nkri on 2008-07-04
It's because hard drives are a lot more important, expensive, and harder to replace than flash drives and the like.  They want to make sure that if you are trying to get into a partition, you are not an impersonator trying to harm the system (unless you're into that kind of thing, lol).  It's a good way of making your system safer:).

---

### Post by spupy on 2008-07-04
Nautilus can mount drives without a password because it is running with more privileges, something to do with runlevels, if I was told right.

Also there is a way to sudo require NO password for the (u)mount command. I used to do it like this but lost the Howto - looking for it right now.

---

### Post by BuffaloX on 2008-07-04
> **nkri said:**
> It's because hard drives are a lot more important, expensive, and harder to replace than flash drives and the like.  They want to make sure that if you are trying to get into a partition, you are not an impersonator trying to harm the system (unless you're into that kind of thing, lol).  It's a good way of making your system safer:).

External harddrives automounts also.
Only reason I don't automount the drive in question at boot, is because I don't want to wait for disk check at boot. How is it more unsafe to mount it 5 minutes after boot, than it is to mount it at boot?
Maybe I'm just too stupid to understand how it makes mny system safer.:lolflag:

> **spupy said:**
> Nautilus can mount drives without a password because it is running with more privileges, something to do with runlevels, if I was told right.

Also there is a way to sudo require NO password for the (u)mount command. I used to do it like this but lost the Howto - looking for it right now.
Please if you find that howto, post a link here.:popcorn:

---

### Post by p_quarles on 2008-07-04
> **nkri said:**
> It's because hard drives are a lot more important, expensive, and harder to replace than flash drives and the like.  They want to make sure that if you are trying to get into a partition, you are not an impersonator trying to harm the system (unless you're into that kind of thing, lol).  It's a good way of making your system safer:).
That is *not* the case. The difference is simply in how the system handles different types of devices. Ubuntu automatically makes the first user a member of the "plugdev" group, which in turn grants that user the privileges needed to use removable devices. 

No similar group exists for internal devices, but this is for lack of demand rather than for security reasons. 

> **spupy said:**
> Nautilus can mount drives without a password because it is running with more privileges, something to do with runlevels, if I was told right.
I don't use Nautilus, but I imagine it's mounting the drives with fewer privileges than the shell "mount" command would normally do. It is not granted more privileges. 

> Also there is a way to sudo require NO password for the (u)mount command. I used to do it like this but lost the Howto - looking for it right now.
There's a sticky thread in the Security Discussions section that mentions this feature. 

That said, the OP may want to look into giving this volume a permanent label instead of tweaking the mount command. If you're just attempting to alter the mount point, you could accomplish this by tying a device name to the drive's serial number. This way, it would respect your setting, rather than assigning a device name like "/dev/sdb1."

---

### Post by macogw on 2008-07-04
Just put "users" in the options column of the /etc/fstab for that drive, and users can mount it without sudo.

---

### Post by BuffaloX on 2008-07-04
> **macogw said:**
> Just put "users" in the options column of the /etc/fstab for that drive, and users can mount it without sudo.

Thank you:popcorn:
Can I put the drive in fstab without mounting at boot?
Please give an example of how the line would look... :guitar:

---

### Post by BuffaloX on 2008-07-04
> **p_quarles said:**
> That is *not* the case. The difference is simply in how the system handles different types of devices. Ubuntu automatically makes the first user a member of the "plugdev" group, which in turn grants that user the privileges needed to use removable devices. 

No similar group exists for internal devices, but this is for lack of demand rather than for security reasons. 


Thank you for clearing that up. :)

> **p_quarles said:**
> 
I don't use Nautilus, but I imagine it's mounting the drives with fewer privileges than the shell "mount" command would normally do. It is not granted more privileges. 

Seems the same to me...

---

### Post by macogw on 2008-07-04
> **BuffaloX said:**
> Thank you:popcorn:
Can I put the drive in fstab without mounting at boot?
Please give an example of how the line would look... :guitar:

Yep, the "noauto" option keeps it from mounting at boot.  Check out the manpage for fstab for a list of options.

---

### Post by K.Mandla on 2008-07-04
Moved to General Help.

---

### Post by chrisccoulson on 2008-07-04
spupy - Just to point out - Nautilus doesn't run with more privileges. It communicates with HAL (which is privileged) in order to mount volumes. I think HAL allows or disallows based on the current system policy (ie, Policykit etc). The default Ubuntu policy is to let only administrators mount/unmount internal volumes and let anybody mount/unmount removable drives via HAL.

The mount command bypasses HAL. Because of this, generally, any mount command will require sudo privileges unless an entry is present in the /etc/fstab with the 'user' option.

---

### Post by BuffaloX on 2008-07-05
Hm I'm doing something wrong, but I don't know what... 


> Fstab:
.. Line 11
/dev/sda4	/media/sda4-data	ext2	noauto, users	0	0


> Terminal:
bill@logic1:~$ mount /dev/sda4
[mntent]: line 11 in /etc/fstab is bad
mount: can't find /dev/sda4 in /etc/fstab or /etc/mtab


---

### Post by lswb on 2008-07-05
Make sure that the entries separeted by commas DO NOT also have a space after the comma. The line you posted, 

BAD LINE:  /dev/sda4 /media/sda4-data ext2 noauto, users 0 0 
should be:
GOOD LINE: /dev/sda4 /media/sda4-data ext2 noauto,users 0 0

---

### Post by BuffaloX on 2008-07-05
> **lswb said:**
> Make sure that the entries separeted by commas DO NOT also have a space after the comma. The line you posted, 

BAD LINE:  /dev/sda4 /media/sda4-data ext2 noauto, users 0 0 
should be:
GOOD LINE: /dev/sda4 /media/sda4-data ext2 noauto,users 0 0

It works now thank you. :popcorn:

---

### Post by nkri on 2008-07-05
> *That is not the case. The difference is simply in how the system handles different types of devices. Ubuntu automatically makes the first user a member of the "plugdev" group, which in turn grants that user the privileges needed to use removable devices.*

Sorry about that, and I don't mean to give false information, it's just what a friend told me a couple months ago when I asked the same question:(.

---

