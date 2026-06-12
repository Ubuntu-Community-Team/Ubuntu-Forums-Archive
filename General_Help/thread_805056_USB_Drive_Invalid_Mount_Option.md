---
title: "USB Drive Invalid Mount Option"
date: 2008-05-23
forum: General Help
---

### Post by SlalomMan on 2008-05-23
I am using a MicroSD card with my R4DS (that isn't important), and for some reason I need to put names in capital letters for the R4 to recognize specific folders. I tried that, and Ubuntu immediately made the folder names lowercase again. I read that putting "shortname=winnt" or "shortname=mixed" in the mount options for the drive would allow this, but It didn't work (at first...maybe a restart was needed?). So, I thought that maybe I should put a hyphen in front (don't know what I was thinking). Anyways, this is obviously an invalid mount option, and Ubuntu tells me so whenever I try to mount the drive. However, I see no way to change this and get rid of the mount options, I cannot access the mount options without mounting the drive, which I cannot do. Is there anything I can do short of reformatting the drive and losing all of my data?

---

### Post by SlalomMan on 2008-07-15
Bump.
I've checked fstab and mtab, but it wouldn't be in mtab because it hasn't been mounted yet; any way I can edit the drives mount options without mounting it?

---

### Post by vitorsouza on 2008-11-26
Just in case anyone arrives here from Google, like I did, I'd like to document the solution to my problem, which I'm not sure is the same as your problem, but anyways...

I inserted an SD card into the card reader in my laptop with Ubuntu 8.10 and it mounted read-only. I didn't know it was a problem in the SD card and I thought it was a problem in Ubuntu, so I right-clicked the drive in the desktop, asked for Properties and in the Volume tab, I added a "rw" option to that volume.

When I unmounted and remounted, I started getting "invalid mount option" messages and Ubuntu wouldn't mount the drive anymore, not even read-only. I could mount it manually using the console, but that's rather annoying.

I searched the Configuration Editor (Applications > System Tools > Configuration Editor -- if you don't see it, go to System > Preferences > Main Menu and enable it in the System Tools menu) and I found the following folder:

system > storage > _org_freedesktop_Hal_devices_volume_label_SANVOL

Inside, a key mount_options = [rw]

I right-clicked in the mount_options key and clicked on "Unset key". I removed and reinserted the SD card and it worked.

Hope this helps anyone...

---

### Post by jayrelox on 2009-04-06
Thanks **vitorsouza**!!It really helps!!!!!

More power to Linux users!!!!:guitar:

---

### Post by dibuntux on 2009-09-16
Exactly the same problem with a Kingston MiniSD on my Ubuntu 9.04 AMD64 system.

With Configuration editor I unset the key and can now read the drive - but it is still in Read only mode.

I cannot determine what was the cause that put the disk in this RO mode - what next?

---

### Post by Ravenheart on 2009-09-30
I had a similar problem with a 2Gb flash drive.  I did the same as vitorsouza and added a rw option to the volume. Then all my flash drives stopped mounting! After I unset the key, It still wouldn't mount automatically and even when I mounted it manually it was still read only. However while trying to fix the problem I had fiddled with the vfat entry in the configuration editor at 
 
system > storage > default options > vfat
 
Here I had changed the umask setting to 777 as I thought that this would give all access rights to vfat volumes. So I reset it back to 077 and then as if by magic when I plugged my flash drive in it worked as normal.
 
I still don't understand it properly but it worked for me.

---

### Post by Ravenheart on 2009-11-16
> **Ravenheart said:**
> 
 
Here I had changed the umask setting to 777 as I thought that this would give all access rights to vfat volumes. So I reset it back to 077 and then as if by magic when I plugged my flash drive in it worked as normal.
 

I found out after that umask actually controls the access rights that you don't want people to have, so a umask of 777 doesn't let anybody have any access.  Whereas a umask of 077 gives a file -rwx------ rights i.e. owner read, write, execute access

---

