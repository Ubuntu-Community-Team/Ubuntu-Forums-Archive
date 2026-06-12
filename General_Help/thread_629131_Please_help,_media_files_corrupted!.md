---
title: "Please help, media files corrupted!"
date: 2007-12-02
forum: General Help
---

### Post by redefinedhero on 2007-12-02
Hi
--a short background.  I am a new user, I have only been using linux/ubuntu for 2 months,    I have a dell 700m laptop with ubuntu 7.10 on it.

Just this week I booted into linux and one of my 2 WD 500 GB hard drives would not mount. It would show up in the toolbar on top, but I was unable to mount it.  My roommate, who is an extensive ubuntu user told me that my file system could be corrupt.  Both are formatted in NTFS because I need to use Windows ever so often.  I restarted and booted into windows and it immediately started a disk check on my external hard drive.  It ran for the better part of 30 min and had masses and masses of errors.  I almost always unmount before unplugging the usb cable, and I honestly do not remember if I did or not that time, but either way I usually unmount and turn off my laptop then unplug, so would it matter if I turned my laptop off and unplugged it with out unmounting?
On to my problem, now all the media files i have on the hard drive (430 GB worth) does not play correctly or read correctly.  I have music and video files on the hard drive and it seems that they are "switched" around.  When i click on some of the music files they play really short and random clips of TV shows or movies and most video files do not even open.  Also, music files that dont play short clips don't even play at all or VLC says that they are not a valid format.  And to top it off, Gparted shows that that hard drive has and unallocated 230 odd GB of space, so it totals to almost 700 GB total space now...any ideas on how to fix that? If I could fix that then could I run Testdisk and Photorec and maybe save some files?

[IMG]http://i214.photobucket.com/albums/cc149/redefinedhero/Screenshot--dev-sdc-GParted.png[/IMG]

Does anyone have any ideas for me? I am up to trying anything and I would be greatly indebted to anyone who can help me, I am kinda freaking out because my roommate doesn't even know what to do and he usually always knows what to do.  Thanks in advance.

---

### Post by TidusBlade on 2007-12-02
I would try dragging them onto a working partition and trying to play them, if they play well, then it's the disk's fault. And if they don't, it's unfortunetly, the file's fault...

---

### Post by redefinedhero on 2007-12-02
Well, I copied a few of the files that I knew would not be played by VLC, even though I know they should be. I copied them to a different hard drive and they do not play still. I get the same error that the file format is unsupported.  Any other ideas on fixing the hard drive space problem I have?  thanks again

---

### Post by redefinedhero on 2007-12-05
bump

---

### Post by gary0 on 2007-12-06
Hi, in windows, run chkdsk /f on the drive that is playing up. Had the same sort of problem on a mates machine, the above command fixed it.

Gary.

---

