---
title: "Problem with transfer speeds"
date: 2019-03-05
forum: General Help
---

### Post by johnnyh2 on 2019-03-05
Hello everybody and thanks for all the helpful information I have been able to gather doing my googling, looking for answers when installing and setting up Ubuntu server!

So, im totally new to Ubuntu but managed to set up two servers that works as backup in a home network, the users of two PC´s with Windows 10 drop files into server1 and it syncs it with a cronjob to server2 overnight.

I have been installing two mellanox connectX-2 10Gb cards, nr1 in one of the PC´s and nr2 in server1, its a peer to peer setup with static IP´s and it works great!

_**THE PROBLEM**_

It only works great with the ssd-drive that I installed Ubuntu on, I have another ssd in server1 that I planned using as a kind of swapdrive (making it possible to empty camera memory cards from PC1 to Server1 really fast).

From PC1 to Server1 (ssd /home/user/shared folder) im getting 500-970 MB/s when dropping the files into the shared folder.

Trying to mount and format the bigger 1TB ssd and doing the same thing im getting 110 MB/s.

Does the choice of file format make a difference? The ssd with the installation in ex4 and the new ssd is NTFS.

Thanks for all the help and try bear with me being a green noob!

---

### Post by TheFu on 2019-03-05
Yes. NTFS is slow. There are mount options to speed it up, but it is still a FUSE file system, outside the kernel.

If you want the fastest access for local storage, use LVM + ext4 or LVM + xfs.

---

### Post by johnnyh2 on 2019-03-06
Thanks for the reply, been getting much better speeds with ext4! Still figuring out the kernel stuff and the user and permissions. But I got it working like I want to for now!

---

### Post by HermanAB on 2019-03-06
The old file systems like XFS and JFS are significantly faster than the newer file systems.  Silicon Graphics and IBM (used to) know what they were doing...

---

