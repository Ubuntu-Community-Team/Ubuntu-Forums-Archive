---
title: "Handling of drive formats and permissions"
date: 2019-02-13
forum: General Help
---

### Post by Chris1965 on 2019-02-13
I've been using xubuntu 18.04 x64 minimal from mini CD for quite some time now using xfce4 desktop environment. I still very much see myself as a newbie to Linux as I am not efficient at all in the terminal and now I don't try to be. I recently discovered that at least Windows and Linux don't play well with each other. I noticed when I tried to share drives over the network Linux can't handle permissions of fat32 or ntfs or share usb external drives between Linux and Windows machines externally as Windows will complain that the drive needs reformatted, like it's corrupted or something similar or it needs to repair the filesystem. I am a person who's been in computers long enough to know not to keep  any information or files on my computers for any lengthy amount of time.

My question is: With as long as the 2 have been around, surely I have to be doing something wrong because this shouldn't be an issue by now surely. I started using computers back in the DOS days before Windows 3.11 and I remember hearing of red hat linux as well and it is now 2019 folks. Do I need to install extra packages that I am not familiar with in Linux to allow Linux to understand and handle the different file systems better?   As of the present I use fat32, ntfs on my usb external hard drives and thumb drives, some are as small as 4 gig all the way up to 2 tb. Linux uses ext4 and Windows uses ntfs. 

Any help would be greatly appreciated.

---

### Post by The Cog on 2019-02-13
I think you will be fighting a losing battle. Microsoft choose not to allow Windows to be able to understand any filesystem other than their own proprietary ones. And they do their very best to prevent other systems from being able to read their proprioetary formats.

---

### Post by him610 on 2019-02-13
> Linux can't handle permissions of fat32 or ntfs
NOT true!
If you are going to share a network between Windows and Linux based computers, you might consider installing *samba* on your Linux machine. There is plenty of help on samba available. If you get stuck, or have questions, just ask.

Open your favorite internet search application; search on *ubuntu samba server 18.04*

---

### Post by yancek on 2019-02-13
> I noticed when I tried to share drives over the network Linux can't handle permissions of fat32 or ntfs or share usb external drives between Linux and Windows machines externally as Windows will complain that the drive needs reformatted,

I'm afraid you have things turned around.  It is a failure of windows.  A default windows system will NOT read much less write to a Linux filesystem while the opposite is true with Linux.  This is a deliberate action on the part of microsoft.  That is why you get the message in windows that the drive needs to be formatted, it doesn't understand other filesystems.  Millions of Linux users use windows (vfat, ntfs) filesystems for data whether dual-booting or just using both system.  Maybe you could give a specific example of whatever problem you are having.  If you are trying to read/write a Linux filesystem from windows, you will need 3rd party software.  If the opposite, you should be able to do that by default on most Linux systems.

---

### Post by oldrocker99 on 2019-02-13
Back in the dual-boot days (never again), there was a Windows app, readext IIRC, which was written to allow Windows users to read (only) ext2-formatted disks. I did work for me with ext4. 

Yes, while Linux systems can read FAT, FAT32, NTFS with no trouble at all, Windows will ask you to format an ext4 volume. They basically don't want that kind of compatibility that we are well used to.

---

### Post by CatKiller on 2019-02-13
> **Chris1965 said:**
> I noticed when I tried to share drives over the network Linux can't handle permissions of fat32 or ntfs or share usb external drives between Linux and Windows machines externally as Windows will complain that the drive needs reformatted, like it's corrupted or something similar or it needs to repair the filesystem.

As already noted by others, you have this backwards: Linux handles Windows formats just fine - within the limits of those formats. Neither FAT nor NTFS can handle permissions or anything but the barest minimum of characters for filenames natively, for example. Windows is incapable of accessing anything other than its own formats.

However, over the network, the underlying filesystem is irrelevant. You need your host to understand whichever filesystem you're using with that host, obviously, but permissions are controlled by the protocol that you're using: NFS or Samba, or whatever.

---

### Post by Chris1965 on 2019-02-13
> **CatKiller said:**
> However, over the network, the underlying filesystem is irrelevant. You need your host to understand whichever filesystem you're using with that host, obviously, but permissions are controlled by the protocol that you're using: NFS or Samba, or whatever.

I actually have samba running on my xubuntu and it is running great, I am able to share any file or folder on the drive that the OS was installed on easily. I assumed that since the external drive showed up in the network and only failed when it asked for the credentials that it was a permissions issue. Linux is most definitely a learning experience. I guess I need to go and read up on samba documentation as in the beginning I thought it pretty simple to install and initially run. So I guess I should now ask is there one file sharing program easier to use or more fully capable then the others?

---

### Post by Chris1965 on 2019-02-13
As to all the helpful reply's ................ wow, thanks so much for your time and efforts. I didn't expect so many returns right alone having the same thoughts.

---

