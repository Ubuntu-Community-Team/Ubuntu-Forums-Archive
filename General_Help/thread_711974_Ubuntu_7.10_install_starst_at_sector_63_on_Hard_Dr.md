---
title: "Ubuntu 7.10 install starst at sector 63 on Hard Drive"
date: 2008-03-01
forum: General Help
---

### Post by openheart on 2008-03-01
Hey all this question grew out of a post I made about the size of my harddrive. In the course of discussion someone noticed that the active boot partition started at sector 63, I install G parted and it does not really give me any clue about what is on those sectors at all. does anyone have any ideas? what is going on here?

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   189309959    94654948+  83  Linux
/dev/hda2       189309960   195366464     3028252+   5  Extended
/dev/hda5       189310023   195366464     3028221   82  Linux swap / Solaris

blkid
/dev/hda1: UUID="35ea4265-37f9-43e7-bbad-bbd6bafbbe55" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: UUID="773c1e1f-0c80-4b4d-bce4-3f5e37cc3632" TYPE="swap"

---

### Post by openheart on 2008-03-01
Anyone here ever seen this type of thing before? I am going crazy here and about ready to smash hard drive with hammer!

---

