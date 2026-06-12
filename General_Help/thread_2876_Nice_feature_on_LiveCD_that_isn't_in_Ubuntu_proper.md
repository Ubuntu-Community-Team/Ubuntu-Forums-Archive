---
title: "Nice feature on LiveCD that isn't in Ubuntu proper"
date: 2004-11-01
forum: General Help
---

### Post by kollivier on 2004-11-01
Hi all,

Just yesterday, I decided to try out the Ubuntu LiveCD and give the distro a test drive. I was suitably impressed at the simplicity and yet the professional feel of the distro. Even though it's very new, I think it's a nice one-CD distro with intelligent default programs. It just feels more clean and comfortable than other distros, IMHO.

Anyways, when trying out the LiveCD, one of the features I really liked was that all my other Windows partitions showed up in the "Computer Browser" section of Nautilus. However, after I downloaded and installed Ubuntu, I only see the Linux partition in my computer - the other partitions aren't automatically loaded. (They do, of course, still exist - I'm writing this from my Windows partition on the same computer.)

So my question is, what is the LiveCD doing differently, and is there any easy way to get those partitions to load at startup like they do on the LiveCD? I'm running this on a PC I've had for 4-5 years, and having all those data files easily available will make a huge difference. 

I should point out I'm a software developer, but a relative Linux newbie. I do know the basics of Unix, and can go into /etc and places like that, but I would need some very clear instructions on what to do to make this happen. Thanks in advance for any help!

Kevin

---

### Post by mduduzi on 2004-11-01
Post the contents of the following file and we'll see if we can help:  /etc/fstab

It's text file and you just read it with any editor.

Further and more importantly, we'll need to know what kind of file systems you have you windows on (NTFS, Fat32)?

More info on your hard disk partioning is important, but we can ask that later.

---

### Post by stodge on 2004-11-01
I remember noticing the same thing on my PC. I have a VFAT partition (/dev/hdb1) that is detected by the Live CD but not by the installable version. I'm comfortable with adding it.

---

### Post by kollivier on 2004-11-01
Interesting, when I boot my installed Ubuntu Linux, my fstab file only has about five entries, and excluding the CD-ROM and floppy, those are /dev/hda5 (my ext3 Ubuntu partition), /dev/hda6 (a swap partition) and /dev/hdd8 (another swap partition). However, this is what I get when booting from the LiveCD:

/etc/fstab contents start
--------------------------------------------------------------------
# UNCONFIGURED FSTAB FOR BASE SYSTEM
# Added by Morphix
/dev/hda1 /mnt/hda1 vfat noauto,users,exec,umask=000,uid=warty 0 0
# Added by Morphix
/dev/hda5 /mnt/hda5 ext3 noauto,users,exec 0 0
# Added by Morphix
/dev/hda6 none swap defaults 0 0
# Added by Morphix
/dev/hdb1 /mnt/hdb1 ntfs noauto,users,exec,ro,umask=000,uid=warty 0 0
# Added by Morphix
/dev/hdd5 /mnt/hdd5 ntfs noauto,users,exec,ro,umask=000,uid=warty 0 0
# Added by Morphix
/dev/hdd6 /mnt/hdd6 ntfs noauto,users,exec,ro,umask=000,uid=warty 0 0
# Added by Morphix
/dev/hdd7 /mnt/hdd7 ext3 noauto,users,exec 0 0
# Added by Morphix
/dev/hdd8 none swap defaults 0 0
# Added by Morphix
/dev/cloop0 /mnt/cloop0 auto noauto,users,exec 0 0
/dev/sda1 /mnt/sda1 auto noauto,users,exec,umask=000,uid=warty 0 0
/cdrom1 /cdrom1 supermount auto,user,fs=auto,dev=/dev/cdrom1
-----------------------------------------------------------------
end contents

So it seems Morphix has some pretty smart logic for auto-detecting devices and adding them into /etc/fstab. I guess I can copy and paste these things into my installed /etc/fstab, but as you can see I have more than a couple partitions, and I may have less or more in the future, and so it would be really nice if Ubuntu somehow managed these things for me, as the LiveCD does.

(And, to the person who asked earlier, as you can see in /etc/fstab the main partition is FAT32 and the others are NTFS.)

Thanks for your help and quick replies!

Kevin

---

