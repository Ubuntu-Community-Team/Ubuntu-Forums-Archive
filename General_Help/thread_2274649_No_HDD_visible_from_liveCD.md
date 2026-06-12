---
title: "No HDD visible from liveCD"
date: 2015-04-21
forum: General Help
---

### Post by fernando46 on 2015-04-21
Hi.
My system is not booting properly. LiveCD sees no HDD; Dolphin sees partitions that shouldn't be there, although Partition Manager seems to see the right ones.
When I run ```
sudo fdisk -l
``` I get the right results (I think), but also says: "Partition 1 does not start  on physical sector boundary".
I've read it could be a problm with something called raid disks, but if I run ```
sudo dmraid -E -r dev/sda1
```, it says that no raid disk is found.
I have lots of data that I would desperately like to recover, should the system revealed definitely lost. As you surely can deduce from my lines, I'm no expert. I need help with this.
Thanks!

---

### Post by dino99 on 2015-04-21
These links might help you fix that raid partition(s) issue

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
[https://help.ubuntu.com/lts/serverguide/advanced-installation.html](https://help.ubuntu.com/lts/serverguide/advanced-installation.html)
[https://www.thomas-krenn.com/en/wiki/Mdadm_recovery_and_resync](https://www.thomas-krenn.com/en/wiki/Mdadm_recovery_and_resync)

---

### Post by nerdtron on 2015-04-21
> I get the right results (I think), but also says: "Partition 1 does not start  on physical sector boundary".
I've read it could be a problm with something called raid disks, but if I run

It could be. But we are not sure yet what your previous hard drive setup was. A little more info would be nice like hardware specs and hard drive partitions, and also if you really did use software.

---

### Post by fernando46 on 2015-04-22
> **dino99 said:**
> These links might help you fix that raid partition(s) issue

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
[https://help.ubuntu.com/lts/serverguide/advanced-installation.html](https://help.ubuntu.com/lts/serverguide/advanced-installation.html)
[https://www.thomas-krenn.com/en/wiki/Mdadm_recovery_and_resync](https://www.thomas-krenn.com/en/wiki/Mdadm_recovery_and_resync)

I'm not sure I have any raid partition... How can I know for sure?

---

### Post by fernando46 on 2015-04-22
> **nerdtron said:**
> It could be. But we are not sure yet what your previous hard drive setup was. A little more info would be nice like hardware specs and hard drive partitions, and also if you really did use software.

I had a standard Kubuntu installation; a small boot partition and a bigger one that I remember has a flag called lvm... I will check tomorrow, since the computer it's in my office and I'm at home now.
Thanks!

---

### Post by fernando46 on 2015-04-23
I got news. I just tried a Ubuntu LiveCD (so long I was using a Kubuntu one) and now I do can see the HDD. The system is not booting yet, though. So now my problem is try to make it boot normally again. I think it all started when I was updating the kernel; maybe something went wrong.
Any ideas?

---

### Post by mastablasta on 2015-04-23
if the issue was kernel upgrade. boot your PC and hold shift. a grub menu should appear. select older kernel and see if you can boot into it.

by not booting -what does that actually mean? how do you know it's not booting as opposed to that you are just not seeing anything on screen?

---

### Post by fernando46 on 2015-04-23
Apparently there's nothing (?) in the boot folder. Can that have something to do with the fact that the system fails to boot (it sounds like it)? If so, what should I put in there? Any other place I should look at?

---

### Post by fernando46 on 2015-04-23
> **mastablasta said:**
> if the issue was kernel upgrade. boot your PC and hold shift. a grub menu should appear. select older kernel and see if you can boot into it.

by not booting -what does that actually mean? how do you know it's not booting as opposed to that you are just not seeing anything on screen?

Hey!
By not booting I mean it reaches the login screen then freezes. Totally. No mouse, no keyboard. BEFORE I can even type my password.

---

### Post by fernando46 on 2015-04-23
OK, I'm now at the point of copying the content of the folder 'boot' from another computer (same system, same version) to the 'boot' folder in the damaged computer. Will that work? Anyway, the problem is, I seem not to have the right permissions. 'sudo', 'gksudo' and 'gksu' won't work and I have no idea how to open Files with root privileges.

---

### Post by nerdtron on 2015-04-23
First try to boot on a older kernel. Reboot normal, but press and hold the shift key while booting. This will show you to grub. Then choose other options, which you should give you older kernel versions. select one and hit enter to boot.

---

### Post by fernando46 on 2015-04-27
Thanks, I tried, but holding the shift key while booting didn't make any difference. Grub menu didn't show up and I ended at the frozen login screen :(

---

