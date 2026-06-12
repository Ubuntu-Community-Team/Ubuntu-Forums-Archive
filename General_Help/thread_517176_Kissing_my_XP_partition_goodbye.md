---
title: "Kissing my XP partition goodbye"
date: 2007-08-04
forum: General Help
---

### Post by imbjr on 2007-08-04
When I installed Ubuntu I decided to go dual-boot, just in case I was making a big mistake. Fortunatly, after a month or so, I'm quite happy with the way things have panned out, so now I have half of my HD laid waste by an unwanted NTFS partition. I'd like to reclaim that partition, but I want it to be as risk-free as possible.

I know I could use GPartEd and either turn the NTFS partition into ext3 (for e.g.) or expand my existing linux partition into the free space that would be created. The latter sounds risky - if I were to suffer a power-down (not unheard of hereabouts) I could be face big problems. 

The former sounds less risky, but I'd like to have the new partition fully utilised by the system. I suspect unionfs is the answer but am unsure how to proceed. Preliminary experiments have not been very sucessful in using unionfs.

Or is there a third way?

---

### Post by be4truth on 2007-08-04
> **imbjr said:**
> I know I could use GPartEd and either turn the NTFS partition into ext3 (for e.g.)

I would go for this. It is a good idea to put data on a separate partition in case you screw up Ubuntu and need to reinstall it.

---

### Post by forestpixie on 2007-08-04
> **imbjr said:**
> I know I could use GPartEd and either turn the NTFS partition into ext3 (for e.g.)...Or is there a third way?

I did exactly that - well almost - I had NTFS on a different hdd. But the basics are the same. You'll need to make changes to your fstab - it'll still be looking for your NTFS discs when you reboot with the new ext3 partition.

Backup you're fstab and edit it to remove the NTFS partition - comment it out with #

I think I edited my fstab before I logged out of Ubuntu and booted the live gparted to deal with the partitioning. I assume that's how you're doing it anyway.

Then you'll need to add the new partition ot fstab and you'll be off.
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Edit - this might also help - the 3rd post
[http://ubuntuforums.org/showthread.php?t=517169](http://ubuntuforums.org/showthread.php?t=517169)

---

### Post by imbjr on 2007-08-04
My main concern - apart from if I lost power during the extension of my existing ext3 into the NTFS-less space - is that if I just replace the NTFS partition with an ext3 one, the system still has all its special directories in the first ext3 - it will not be able to grow beyond that partition, unless I somehow move some of the directories over or try to use unionfs.

I may have to just wait til the weather report says overcast-but-no-rain and extend my ext3 - praying that power will not be cut. I'm not saying this is a regular occurance, but it has happened, and it happening during a precarious procedure such as GPartEd extending will not make me happy.

PS. I've already removed the NTFS from fstab, so that's not going to be a prob.:)

---

### Post by forestpixie on 2007-08-04
> **imbjr said:**
> My main concern - apart from if I lost power during the extension of my existing ext3 into the NTFS-less space - is that if I just replace the NTFS partition with an ext3 one, the system still has all its special directories in the first ext3 - it will not be able to grow beyond that partition, unless I somehow move some of the directories over or try to use unionfs...PS. I've already removed the NTFS from fstab, so that's not going to be a prob.:)


How are your partitions setup at the moment then, how did you set Ubuntu up in the first place. Have you got a seperate /home folder - or did Ubuntu do it for you on install.

Reason I'm asking is that the files system shouldn't grow that much as you install other programs. And if you're happy with the way /home is and it's size - the new partition would be somewhere you could store things.

---

### Post by TBerben on 2007-08-04
Be careful when editing your partitions. I had this problem myself. Ubuntu's default fstab works with UUIDs instead of device names. I had an ext3-partition that contained an openSUSE installation that I didn't use anymore, so I formated that partition. This changed the UUID of the partition, however, fstab expected the former UUID. When I rebooted my computer, I got an fsck error and couldn't boot into ubuntu. I fixed the problem by booting into a livecd environment and replacing the UUIDs with regular device names.

---

### Post by xpod on 2007-08-04
> When I installed Ubuntu I decided to go dual-boot, just in case I was making a big mistake

It dont seem like yesterday that i was having the exact same concerns:)
In fact,i might not have got rid of XP as quick as i did were it not for a simple mis-understanding on my part with the installed gparted,unmounted disks and missing yellow bands of data.

No sooner had i wiped the lot to start again did i reliase my mistake.
Best thing i ever did though was to re-install that XP,SP2 etc etc etc.........then realise it was totally pointless and install Ubuntu right over the top of it all.

As William Wallace once screamed back in 1305.......Freeeeeeeeeeeedom!!!.
Ok then....Mel Gibson in 1995:)

You can always use virtualbox etc for simple XP vm if you ever need in the future btw

---

### Post by imbjr on 2007-08-04
forestpixie: I have an NTFS partition, the ext3 currently being used by Ubuntu and a FAT32 partition (swap too and two Dell-related system ones). I just let the install do a standard dual-boot install so home on the current ext3 - it might be nice to move it over to what will become the new ext3, but how I don't know.

TBerben: I hear you. I think I nearly had the same problem when I was meddling with my swap partition. I just got rid of the UUID reference and used the device reference instead.

xpod: I've already got XP stashed in a VirtualBox. The only way I can run Photoshop at the moment without going back into the old NTFS partition.

---

### Post by imbjr on 2007-08-04
Update: Looks like I may be able to basically copy the home drives into the new space and amend fstab to mount them from there. That would be a good start.

---

### Post by Irony on 2007-08-04
I've written a guide here about copying distros from partition to partition;

[http://www.pclinuxos.com/index.php?option=com_smf&Itemid=58&topic=13404.0](http://www.pclinuxos.com/index.php?option=com_smf&Itemid=58&topic=13404.0)

I've used this method hundreds of time on Ubuntu and also use it to back up distros to an external drive.

---

### Post by forestpixie on 2007-08-04
________________

---

