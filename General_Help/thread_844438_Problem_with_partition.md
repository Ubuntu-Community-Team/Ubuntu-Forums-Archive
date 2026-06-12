---
title: "Problem with partition"
date: 2008-06-29
forum: General Help
---

### Post by thechristelegacy on 2008-06-29
For the longest time I had Ubuntu v5 installed and I wanted to upgrade to 8.04. I read online that the easiest way to upgrade was to just download 8.04 and reinstall linux. So I downloaded 8.04, popped in the install CD and ran the installer. When I got to the partitioning phase of the install it asked me how much I wanted to allocate to windows, and how much I wanted to allocate to linux. Because of this I assumed that it was going to reinstall over my old version of linux, well I guess it didn't. I was wondering how to get rid of my old versions of linux.

Is it safe to just go into gparted from the live CD and delete them?

The 8.04 v doesn't have a boot flag, whereas the 5.v does, so that makes me a little nervous.

Also it seams that there are multiple partitions under the same one.

This is what shows on gparted

/dev/sda4 extended    --lba 
---     /dev/sda7 ext3  (ubuntu 8.04)
---     unallocated unallocated
---     /dev/sda8 linux swap ( new swap )
---    /dev/sda5 ext3 /    boot (old ubuntu)
---    /dev/sda6 linux swap (old swap)

My second question I have 30 gigs of unallocated space above, and I want to add that onto my windows partition (/dev/sda2) how do I go about doing that? I thought I would just be able to resize my windows partition to use that exrta space, but I guess since its somehow part of /dev/sda4 I can't.

Thanks for your time guys, I really appreciate it.

Anthony

---

### Post by Rocket2DMn on 2008-06-29
You can delete the other partitions from the LiveCD, you may need to remove any entries in your new /etc/fstab for them if they were auto added, then you need to update GRUB from within your new install if there are options there.
```
sudo update-grub
```
If it turns out it is using the old install of GRUB and you delete that install, you will need to reinstall GRUB.  This is easiest with the Super Grub Disk - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) but can also be done with the LiveCD.

Since you have a new install, and some strange partitioning problems, it may be easiest to delete all the partitions except your windows, make it all unallocated space, and reinstall with just a new root and swap partition.  Then you only have 3 partitions - windows, linux, swap - and it will be clean.

Don't worry about the boot flag.

---

### Post by thechristelegacy on 2008-06-29
Thanks for the reply.

If I do end up deleting all partitions minus the windows one, will Windows boot if grub isn't there? Or will I have to install ubuntu first?

Thanks,
Anthony

---

### Post by Rocket2DMn on 2008-06-29
If you don't want to put Ubuntu back on it right away, you will need to restore Windows to the MBR.  This means booting from the Windows cd, entering the recovery console, and running
```
fixmbr
``` (assuming Windows XP).  For Vista, see [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Otherwise you will need to reinstall Ubuntu which will automatically setup GRUB for you.

---

### Post by thechristelegacy on 2008-07-01
I think I'm going to go with the clean install. I have a few worries I want to put to rest before I do this though. I'll post a screen shot of my gparted screen.

As you can see all the linux stuff is under that partition that says extended. Gparted won't let me just delete extended, does that mean I have to delete the rest of the partitions within the extended partition first and then I can get rid of the extended?

Or is there a way to move that unallocated space and add it to my NTFS partition?

Thanks for your time,
Anthony
[IMG]http://www.languagearena.com/tony/ss.jpg[/IMG]

---

### Post by konungursvia on 2008-07-01
Delete the contents (logical partitions) of extended first, then delete the primary partition extended afterwards.

---

