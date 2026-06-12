---
title: "File Issues - from MAC to Ubuntu"
date: 2023-02-23
forum: General Help
---

### Post by countryboy71 on 2023-02-23
I am having a very strange issue right now, that in all my years of working in different operating systems, have never had.

Over the last number of years I have been running my media server through MacOS (Monterey; most recently) on two attached 'storage' drives. These two drives are formatted in MBR; NTFS format.  I also had NTFS...something (the name is alluding me) installed on the MAC so that I could read/write to said drives.

I had made the decision that I was going to move all the media server tasks over to Ubuntu and when I finally got it up and running (albeit with another issue I haven't figured out yet on booting), I went in and noticed that I can only see about a quarter of the files I know to be there.  This same issue is replicated on Windows10.

Is it possible that the MAC is working/saving these files in HFS+ format even though the drive is formatted another way or that journalling could be causing an issue?

I'd also note, though not sure if this is related, when I load up the 'db' file from JellyFin and look at the series information table, some of the files (the ones I can see, I believe) are there with proper path formatting; volume/folder/name, while the majority of the files & folders don't indicate any path...yet, everything is working.

Hoping someone here has experienced something like this or can put their finger on exactly what could be causing this.

Edit 1: I should have noted that I can see all expected files if I am on my MACBook.  Also, I created a folder and threw some photos in it earlier and I was able to see those on from Ubuntu.

---

### Post by ActionParsnip on 2023-02-24
HFS+ is a file system, not a file format. The files are saved to the file system. If an OS can read the file system (HFS+, NTFS, Ext4 etc) then the files will be visible. Applications can then read the data they are given from this file system.
How is Ubuntu part of this? Did you set up a Samba server to share files (for example) or are you using SSHFS etc etc.
Details please

---

### Post by HermanAB on 2023-02-26
Note that Mac and Linux are UNIX, but Windows is VMS.  So you will have user and group ownership issues between the machines which you will have to override.

---

