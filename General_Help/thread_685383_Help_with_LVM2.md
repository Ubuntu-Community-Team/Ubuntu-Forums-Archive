---
title: "Help with LVM2"
date: 2008-02-02
forum: General Help
---

### Post by pantner on 2008-02-02
Ok, i am a very new user to Linux...This is my first install.

This is what i want too do...

File Server with different HDDs in it...i have 1x750, 1x500 and 2x250 in there.

I would like to use LVM to create a Logical Partition over all of them.

I have installed Unbuntu onto the 750Gb HDD and told it too install using LVM. (like, when u boot off the CD, tell it to do the text based install, and selected Guided Install Using LVM)

i have most of everything else setup (ie, wine, utorrent) and now would like to create the logical partition of all the HDDs...

Now, the partition already on the 750Gb i *think* is using the entire Drive...i would like the shrink the main partition down to ~30Gb (just to give me some breathing room) add the other 3 HDDs to the LVM and then create one large partition over the unallocated space...

now, from what i've read (am a little confused now though) because i am using LVM2 i cannot shrink the partition on my boot drive (the 750Gb). Is that correct?????

i suppose i could just add all the drives to that partition and share out a folder store on the drive, but would prefer to keep them separate if possible...

PLEASE HELP! :)
Thankyou!

---

### Post by zvacet on 2008-02-02
[This](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall) maybe?

---

