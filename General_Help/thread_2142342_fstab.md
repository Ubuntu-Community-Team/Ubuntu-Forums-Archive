---
title: "fstab"
date: 2013-05-05
forum: General Help
---

### Post by Melatonin85 on 2013-05-05
Hi there,

I've got little problem and I'd very appreciate it if somebody could give me a hand in this case...

Beside the harddisk where ubuntu is running i have two additional harddisks in my pc. However, these harddisks contain both of 2 harddisks, which are mirrored within a raid-system (but not via a hardware, but software raid-controller).

anyway, my goal is that i want these 2 "harddisks" or "partitions" to mount automatically, so that i can just switch on the pc and be sure that the harddisks are mounted.

however, im very much struggling with it. i tried the following:
1) mount the harddisks it via file explorer (pcman). after that i typed "mount" in the console in order to get the /dev/ID of the harddisks. 
2) i edited the /etc/fstab as follows:
> 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=4fc578b0-9891-4c6f-8e19-10a770269e13 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2982530d-da33-48ad-ae87-3055947b60ca none            swap    sw              0       0
#films
/dev/mapper/sil_bhbhdhcafdbc1    /home/melatonin/Films     vfat     users,rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2    0    0
#media
/dev/mapper/sil_bhbhdccbcbai    /home/melatonin/Media    vfat users,rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2    0 0





3) tried "mount -a" in the console in order to check if the fstab is mounting the harddisks.

so far so good... "mount -a" works fine. But when i restart the PC, it doesnt boot ubuntu, it just goes to the ubuntu-loading-screen, but never goes further...
meanwhile i found out, that the first harddisk ("films") works, if i remove the command for mounting the 2nd harddisk ("media"). so actually this entry works and the 2nd entry for "media" seems to be wrong. Unfortunately i've no idea why, since both entries are actually identical.

Does anybody have a clue what i could try?

Thank you so much for your help,
Best Mela

---

### Post by Cheesemill on 2013-05-05
I'm sure you've already checked this but does the directory /home/melatonin/Media actually exist?

---

### Post by Melatonin85 on 2013-05-05
Hi Cheesemill!

thanks for your reply. Yep, I've checked the directory and set the same permission as for the directory "Films". Additionally, "mount -a" doesnt show me any errors and mounts my "Media"-Harddisk without any complain.

Best,
Mela

---

### Post by Cheesemill on 2013-05-05
Do you have a space between [COLOR=#b22222]shortname=[/COLOR] and [COLOR=#b22222]mixed[/COLOR]?

If you do then get rid of it, it's not meant to be there.

---

### Post by steeldriver on 2013-05-05
... and between *udi* and *sks* (although I'm pretty sure mount should barf if that's really there)

---

### Post by Melatonin85 on 2013-05-05
yep ive checked. There are no spaces and actually it should be "udisks2". Dunno why it got split.

---

### Post by Melatonin85 on 2013-05-05
Yay!

I finally made it work...

The following solved the problem:
I simply checked in "Preferences" / "Disks" the Settings for both harddisks. I then simply compared all the settings and applied them of the working harddisk on the other one. Interestingly, for the working harddisks it wasn't ticked "automatically mount harddisk".

---

