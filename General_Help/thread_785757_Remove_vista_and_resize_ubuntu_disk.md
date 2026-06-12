---
title: "Remove vista and resize ubuntu disk"
date: 2008-05-07
forum: General Help
---

### Post by slinky89 on 2008-05-07
Hi,

A while ago I installed Ubuntu. Because I was totaly new with this I was a little scared for a total switch-over so I maded a dual-boot with Vista and Ubtunu.

I gues it isn't a big suprise that I like Ubuntu way more then Windows Vista.. so I wanna remove Vista from my PC and assign the new free space to my Ubuntu partition.

My question is what is the best way to do this? I think I should format the Windows Vista partition first? But what is the best way to do this.


Thanks in advance,
Slinky

---

### Post by Cannaregio on 2008-05-07
You can do that with gparted

```
sudo gparted
```

and format to ext3 and use the ex windows partition either for another distro (so that you can try something new every month) or for Ubuntu itself (resizing your existing ubuntu part to take over the new space will be possible ONLY using gparted from a live CD, though).

However, my advice would be to reinstall completely Ubuntu from a live 8.04 CD, [COLOR="Blue"]formatting everything anew[/COLOR] (saving first on an external harddisk what you want to keep). That's cleaner and will give you the opportunity of dividing neatly the [COLOR="#0000ff"]/[/COLOR] from the [COLOR="#0000ff"]home[/COLOR].

---

### Post by smoker on 2008-05-07
remember, if grub is on your vista mbr, you will have to reinstall grub after you format the vista partition, here is a link if required: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by panda726 on 2008-05-07
I also would agree with Cannaregio's suggestion to clean install.  If you put /home on a separate partition from / , you will be able to simply run a clean install and remount your /home partion again.  This can be done without loss of data, although backing up may be a worthwhile precaution in case things go really wrong (perhaps less likely an install than some other problem that would actually cause data loss.  I have done this myself to simply upgrade from one release to another by clean install.

If you choose to reinstall, backup your /home/username folder, for all users you want to keep.  Also backup any other folders where you have stored data.  This should be none, unless you have other partitions.  This should be safe, but backing up to a separate physical disk is still a good idea before rearranging partition tables.

Keeping multiple partitions is a wonderful way to protect data from some errors that many windows users are unaware of.  Of course, we GNU/Linux users have so many more ways to make use of this:)

Tor

---

