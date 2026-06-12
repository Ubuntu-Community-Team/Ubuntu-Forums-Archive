---
title: "Partitioning HDD to dual-boot Windows and Ubuntu"
date: 2008-04-14
forum: General Help
---

### Post by Wally_dog on 2008-04-14
When I get my Dell desktop coming preinstalled with Ubuntu 7.10, will it be difficult to partition the hard drive so that I can dual-boot Windows XP and Ubuntu? A friend on another message board said he recommends Making a root partition that the Ubuntu system files are on, then another partition for where documents/pictures/music etc. are stored, in case I ever needed to wipe the installation, all my documents would still be there. So, I was wondering if when I receive my desktop, can I partition it like that without reinstalling Ubuntu? For the Windows XP installation, I was wondering if I could have Windows share the document partition that Ubuntu will be using, so that I have less partitions to manage. I heard something about Ubuntu using a NTFS File system... will this affect installing Windows XP?

Wally

---

### Post by sujoy on 2008-04-14
yes ubuntu can handle NTFS file system fine and you can thus share that with windows, as far as installing without reinstalling ubuntu is considered, i guess you have to wait till you get the PC because from the info you provided i cannot tell if Dell ships their preinstalled ubuntu systems with any empty hard disk partitions.

since the very point of preinstalled OS is to make life easier for the user, i doubt Dell will keep any unformated disk space for users to formay themselves and use.

---

### Post by Het Irv on 2008-04-14
If you have a Live CD you can use Gparted (Partition Manager) to create new partitions, I don't know how to reconfigure Ubuntu so that your home is on a different partition but if you just want a general storge partition to share, make sure that it is formatted NTFS.  I think you will have to change the permissions to allow Ubuntu full access to it, but it shouldn't be to hard.

---

### Post by Wally_dog on 2008-04-14
So you're saying that I can all my hard drive partitions as NTFS? Wow that does sound easy :) Is partitoning really as scary as it sounds? Right now I'm worried about messing up and not being able to reinstall Ubuntu.

---

### Post by Het Irv on 2008-04-14
Ubuntu uses ext3 for it own data, but it can read NTFS.  You will always be able to reinstall because during the reinstall process it formats the partition you are installing to.  Partitioning is not that scary you just have to be careful of what you are doing.

---

### Post by Wally_dog on 2008-04-14
When I decide to setup a Windows partition, will I have to change anything to the Ubuntu partition? And I heard somewhere that XP formats the hard drive on install...

---

### Post by Het Irv on 2008-04-14
You may have to reduce the size of your Ubuntu Partition so that you can make an XP one, but Xp will only format the partition you are putting it on, but it will install its boot loader over GRUB, making it impossible to get into Linux.  To fix that you will have to restore GRUB.  I don't know how to do that but their are other threads here in the Fourm that will tell you how to do this.

---

### Post by LaoziSailor on 2008-04-14
Wow!, this is very interesting. I want to remove GRUB and get my MBR to point back to WinXP -- see thread **[thread=225197]How-To: Grub, Windows XP, and the MBR[/thread]** and then let the NT loader take care of the dual boot.

Any help would be appreciated. It was very unnerving to think I had lost my XP and after multiple downgrade attempts it automagically got fixed somehow.

Cheers!

PS. this post is not intended as a hijack of the thread -- just seems relevant and I would be pleased if the MOD decides to place it elsewhere [not the garbage bin, I hope :lolflag: ]

---

