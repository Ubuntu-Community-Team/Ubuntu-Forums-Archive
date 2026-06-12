---
title: "Re: Persistence on boot disk"
date: 2017-05-01
forum: General Help
---

### Post by warmango on 2017-05-01
I was curious if one could create a persistence file to an is then burn it, The file would have stuff like ubuntu application packages on it so I wouldn't have to use external media other than the disk, 

Types of packages 
   - Video/Audio media support
   - possibly Gimp or other art programs

Just curious if is possible and how.
The thought cave to me as I was creating a Bootable USB using MyLinuxLiveUSB creator

Edit
- was going to use version 16.04 for this

---

### Post by yancek on 2017-05-01
> I was curious if one could create a persistence file to an is then burn it

Did you mean "iso" rather than "is"?  You would need to unsquash the filesystem.squashfs file which is going to be pretty complex for someone not very experienced with Linux.

I'm not really sure what the question is.  It's pretty easy to create persistence on a usb drive, either a file or partition.  If you want to do something similar and then burn the iso file to a DVD that is possible but you are not going to be able to make changes to it after creating it.  You can also use something like systemback or pinguybuilder to create an iso of an installed system with added software which you can then burn to a DVD, size limits apply here.

You might be more specific as to what you want.

---

### Post by C.S.Cameron on 2017-05-01
Have not yet found a way to make a casper-rw file or partition read only.
When booting a copy of 'Buntu with "persistent" in the txt.cfg, syslinux.cfg or grub.cfg file, the process grabs the first casper-rw file or partition it encounters to use as persistence for that boot.

If you make the first partition of the drive FAT32 or NTFS, (with mkusb), you can store application packages there.

---

### Post by warmango on 2017-05-01
I meant iso but I typed on mobile, 

What I want is a file that's like a persistent file, but holds packages that can be temporally installed by the user. Doesn't matter whether or not I can write to the file. Only that I can write packages to it before I burn it to the disc, then use the packages

---

### Post by yancek on 2017-05-01
> Only that I can write packages to it before I burn it to the disc, then use the packages 		

Either Pinguy Builder or Systemback can create an iso file which is bootable.  You need to first install Ubuntu or one of it's derivatives then install whatever software you want and run either Pinguy or Systemback which will create an iso file which you can burn to a DVD and run and it will contain the software you added.  You can't modify this as it is an iso9660 filesystem which by definition is read-only so I'm not sure how that would fit in to your "temporary" requirement.

---

### Post by warmango on 2017-05-01
That'll do, what I meant by temp was that,

You have the package, you need to install the package so that you can use it, but your using a bootableCD/USB so it wouldn't say installed

---

