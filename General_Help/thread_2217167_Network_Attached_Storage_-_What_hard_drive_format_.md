---
title: "Network Attached Storage - What hard drive format should I use?"
date: 2014-04-15
forum: General Help
---

### Post by randypfau on 2014-04-15
I have a HP EX470 Mediasmart server I have put ubuntu on. I have little linux experience and find myself googling to practically do the simplest of tasks xD ... anyways heres what I got... 

320GB w/ 300GB of Free Space
(3) 1TB Hard Drives formatted NTFS

The 3 1TB hard drives contain different types of media, videos, music, apps, etc. I previously had them set up on Windows Home Server as raw drives that I created SMB shares on to access over my network. I upgraded to ubuntu and now is the time to set up my services. Im just wondering... should I just slide in my drives and call them good? Or **would linux or certain services handle them better if they were a different format other than NTFS**? I figured Id configure samba and uPnP with mediatomb or xbmc, other than that I dont know what other services would be good. Any suggestions?

---

### Post by papibe on 2014-04-15
Hi randypfau. Welcome to the forum ):P

Do not use NTFS, use ext4.

You don't need NTFS in order to use samba and share folders with Windows machines. Regardless of the disk filesystem, a Windows machine will access the files over the smb protocol.

In that sense, you need the best supported current filesystem: ext4.

Hope it helps. Let us know how it goes.
Regards.

---

