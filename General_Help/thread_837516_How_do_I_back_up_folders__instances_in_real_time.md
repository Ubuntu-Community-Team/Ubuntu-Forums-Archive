---
title: "How do I back up folders / instances in real time?"
date: 2008-06-22
forum: General Help
---

### Post by Chongo on 2008-06-22
I have three computers:

Laptop - Kubuntu 8.04

Media PC - Mythbuntu 8.04

Webserver - Xubuntu 8.04 Server & Xen

I would like to be able to back up the main documents and media files either onto my Windows hard drive (in the same machine via the NTFS3g driver) onto my Media PC, or onto my external network hard drive (which has FTP / Samba).

I would like to be able to back up the main folders on my media PC to the second hard drive on my media PC in real time (but not the whole OS / hard drive)

I would like to be able to back up whole Xen instances on my server to the second hard drive on my server in real time.

*

Please could someone advise me how best I do this, I have a low - moderate level of knowledge about Linux, and am not sure how best to proceed.

At the moment the operating system is on one hard drive and the other is mounted to the file system as /backup (on the media PC and server).

Do I need some kind of Software RAID thing that will just backup specific folders or instances, and if so could you point me towards something which explains me how to do this?

*

Many thanks!

Tom

---

### Post by fjgaude on 2008-06-22
I use grsync to do these kinds of things. It's in the repository. Give a look and see if that's what you need.

---

