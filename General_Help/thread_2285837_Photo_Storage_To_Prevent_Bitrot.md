---
title: "Photo Storage To Prevent Bitrot"
date: 2015-07-08
forum: General Help
---

### Post by Dutcheez on 2015-07-08
Hi,

I've been researching solutions to come up with a solid storage and backup solution for all of my family's media (video, photos, and documents). I'm mostly concerned about the photos that my wife has taken over the years and they're all in RAW format. I'd like her photos to stand the test of time and I'm afraid of drive failures and bitrot. 

Currently, I have a pretty minimalistic Ubuntu setup which uses an old Dell desktop (E510) and that has one additional 2 TB drive. The 2 TB drive is ext4 partitioned for 2 time machine backups (@500 MB each) and 1 TB media share (where most of our photo library is contained) served by using netatalk AFP to 2 Macs and by using Plexconnect to an AppleTV. The 2 TB drive backs up to an external 2 TB drive once a day.

I realize my current setup doesn't protect me against bitrot and / or fire.

From what I've read ZFS and btrfs are 2 file systems that can correct for bitrot and allow me to cope with a drive failure if, for example, I run a 3 disk RAIDZ setup so that I can have let's say 3 x 4 TB drives, where one drive is there for redundancy. 

On top of that, I would backup snapshots of this setup off-site to either a cloud backup account or setup a remote server somewhere and use ZFS send.

Those are my initial thoughts, but I would really value anyone's input on this approach to see if I'm on the right track.

Thanks!

---

### Post by TheFu on 2015-07-08
zfs is 1 way.
Using par2 to create parity files will allow small imperfections to be corrected.
[http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival](http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival) is how I do this storage.

The more important any data is, the more copies we need to have on different storage devices. **Critical data deserves 5 backups**, IMHO.

---

### Post by lukeiamyourfather on 2015-07-13
I unfortunately have lost several photos of significant sentimental value due to silent data corruption. You can read about my experience on my blog.

[http://whenpicsfly.com/getting-to-know-zfs/](http://whenpicsfly.com/getting-to-know-zfs/)

After discovering ZFS I quickly jumped into the deep end with it. I've been using it for several years now personally and professionally and it has been everything I was hoping for and then some. If you decide to go with ZFS do your research first because there are some gotchas (like ECC memory).

At home I run a RAID Z3 with 8 drives to store photos and art projects. These days I wouldn't use RAID Z for anything other than research and tinkering.

---

