---
title: "How do I make Ubuntu see multiple drives as one drive?"
date: 2008-04-06
forum: General Help
---

### Post by ryodoan on 2008-04-06
I am working on figuring out how to create an Ubuntu file server for my house.  At the moment most of the other computers in the house are Windows computers so I know I will need to set up Samba.  I have never done that before but I have seen a few guides online and I think I can work through it without many problems.

The thing that I am currently trying to figure out right now is something I heard one of my coworkers who is more familiar with linux talking about.

My fileserver has 4 hard drives in it, and they are all different sizes (160, 200, 230, 300) and are all IDE.  I dont know much about RAIDing hard drives, but I think all the hard drives need to be the same size (do they?).  What I heard from my coworker is that there is some way to make linux operating systems see multiple hard drives as one hard drive.  I think he was talking about using a program called LVM, but I could be mis-remembering the name.

In any case, is there some online guide or can someone tell me how to install ubuntu so that it sees multiple hard drives as one hard drive? Thanks in advance.

---

### Post by Cresho on 2008-04-06
I think it is better if you raid (stripe) on your motherboard.  oops!  Different sizes?

---

### Post by warp99 on 2008-04-07
You can use LVM and Raid1 (mirroring) since the drivers are of different sizes, but you can't use Raid5. Here is a guide that will show you how to setup LVM:

[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall?highlight=%28lvm%29](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall?highlight=%28lvm%29)

and LVM with Raid1:

[https://help.ubuntu.com/community/Installation/RAID1+LVM?highlight=%28lvm%29](https://help.ubuntu.com/community/Installation/RAID1+LVM?highlight=%28lvm%29)

---

