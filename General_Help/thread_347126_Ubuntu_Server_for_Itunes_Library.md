---
title: "Ubuntu Server for Itunes Library?"
date: 2007-01-26
forum: General Help
---

### Post by Caen on 2007-01-26
Hi,

I currently have a Mac Mini that I keep my Itunes library on but would like to create a Ubuntu media server that could hold all of the library files. I know Itunes won't run on Ubuntu, but I thought I could do it the following way since the Ubuntu box will be nothing but a media server. Please correct me if I'm wrong.

1. Install NFS partition on Ubuntu box
2. Point library folder of Itunes on Mac Mini at the NFS partition on Ubuntu box
3. Audio and Video files would then be stored on NFS partition, but accessible via Itunes on Mac Mini.

The other question I have is with the Apple TV product. We're thinking about purchasing it in the near future, but it syncs wirelessly with Itunes on another machine to acquire it's files. I'm assuming that even though the files are on the Ubuntu box via NFS, that because Itunes is running on the Mac Mini, the Apple TV product would still be able to sync wirelessly to the Itunes interface on the Mac Mini?

Do my plans look like they'll work? I want to go about this the easiest and most stable way possible.  Also, does anyone have a good tutorial at hand on NFS and making a Mac box and Linux box recognize each other for file sharing?

Thanks

---

### Post by matthewstory on 2007-01-27
Yeah, that'll work . . . assuming you can get an NFS client to work on Mac, which is possible . . . woudn't know exactly how . . . i know more about SMB with Mac, which is something you could also consider . . . making your ubuntu box a samba server . . . but this is much gnarlier than an NFS server.  For setting up the NFS server, i wrote a quick guide a couple days ago for a guy on here . . . this uses NFS user server:

[http://www.ubuntuforums.org/showthread.php?t=344608](http://www.ubuntuforums.org/showthread.php?t=344608)

I'm sure if you google NFS mac, you'll find your answer.  But yes, this should work fine, you'd just mount the NFS share on your /Users/<user name>/Music folder I believe.

---

### Post by matthewstory on 2007-01-27
one more thing, mac and linux already speak the same language, as OS X is unix . . . so that's not a concern.

---

### Post by Caen on 2007-01-27
So, are you saying I don't even need an NFS partition?  Will I be able to file share between them with my Ubuntu box setup with the standard ext3 formatting?

Thanks for your help. :)

---

### Post by cam_tram on 2007-01-28
You can just use [Firefly]("http://fireflymediaserver.org/"), it should work with Apple TV since it uses DAAP too.  As far as I know, it won't share videos though.

---

