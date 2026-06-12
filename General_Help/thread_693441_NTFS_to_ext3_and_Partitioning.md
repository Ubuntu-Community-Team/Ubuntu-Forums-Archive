---
title: "NTFS to ext3 and Partitioning"
date: 2008-02-11
forum: General Help
---

### Post by TransitMan on 2008-02-11
Ok, so I have been using one flavor or another of Ubuntu since the later part of 2005. In that time I have learned a lot, borked a few things, fixed them and learned some more. (Note I dual boot - hence the coming questions.)

I am now at a cross road where I want to dump Windows completely, but find the need for it for a couple of programs unavailable in one form or another in Linux.
I recently played with several VM's to see which one would fill the bill for the occasional foray into the Windows world, and to my surprise and delight found it to work just the way I wanted it. Not bad for a VM.

Now to the questions.

I have a number of drives formatted in NTFS. Is there a conversion method from NTFS to ext3 without borking the files?

When I get done with the conversion, would it be a safe bet to at least one partition FAT32, just in case? (Possible file sharing with another computer.)
When I do this, can I have the /, /tmp, /var, /usr, /opt, and /home located on different drives? And if so, can I get some recommendations on partitioning the drives (2 80gb SATA's out of 3. The third is going to be strictly my music files.)?

Also, in the grand scheme of things, can I make a partition just for VM's, instead of parking them within the /home or /var partitions?

---

### Post by src2206 on 2008-02-11
As you are in Windows, see if Acronis Disc Director Suite can do that. You can get a full functioning 1 month trial of it. But honestly I doubt whether it will be possible and even if it is, I would strongly recommend you to backup Data before experimenting.

You can also see if the latest version of GParted can do this, if you have not checked out already that is. :)

---

### Post by jan quark on 2008-02-11
do a backup, before even uttering the word "partitioning" aloud :)

have seen too many broken souls, who lost everything

I don't think it is possible to change the format from ntfs to ext3 without conpletely removing all data

just backup your data on a disc

> When I get done with the conversion, would it be a safe bet to at least one partition FAT32, just in case? (Possible file sharing with another computer.)

you can do this, common procedure

> When I do this, can I have the /, /tmp, /var, /usr, /opt, and /home located on different drives? And if so, can I get some recommendations on partitioning the drives (2 80gb SATA's out of 3. The third is going to be strictly my music files.)?

Also, in the grand scheme of things, can I make a partition just for VM's, instead of parking them within the /home or /var partitions?

That's beyond me :)

---

### Post by DoctorMO on 2008-02-11
> Also, in the grand scheme of things, can I make a partition just for VM's, instead of parking them within the /home or /var partitions?

Not really, unless your VM supports interacting directly with hard drives and most of them don't. Fund your local VM software supplier for this feature.

---

