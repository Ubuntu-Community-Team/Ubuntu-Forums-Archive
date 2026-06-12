---
title: "[SOLVED] Broken image (ubuntu-7.10-dvd-i386)... Could someone help?"
date: 2007-11-01
forum: General Help
---

### Post by rubicon on 2007-11-01
I know, it is silly to ask for help in this situation as you may say "Download it again, d'uh!", but that IS a prob. I don't want to spend a week downloading the image again. 

And I know that it isn't *fully* broken, - it have just some parts broken (checked MD5 of separate files in image - most of them are OK).

I will very appreciate help from anyone. What I exactly need is some source to download separate files.
Or - this is even better - split image file to 100MiB files and provide their MD5 for me...

It's shame for me to ask this... But again - i don't want to dl the whole image just to repair a couple of files.

---

### Post by bingoUV on 2007-11-01
If you post which files are broken, someone here might share them with you. I think you ran md5 sum on md5sum.txt in the mounted DVD, and most of the output lines were OK. Can you post the output lines which were not OK i.e.
```

sudo mkdir /tmp/gutsyDvd
sudo mount -o loop /path/to/dvd.iso
cd /tmp/gutsyDvd
md5sum --check md5sum.txt | grep  -v 'OK'

```

---

### Post by rubicon on 2007-11-01
I'd gladly do that from ubuntu running, but currently i'm on XP.

But I ran Total Commander and checked checksums, that's what I have:

OK: 5318, not found: 7, read error: 0, wrong checksum: 11

All files that 'not found' and some of 'wrong checksum' are packages from 'pool' forlder, so i can download it from archive.

Some files that i cannot find are:
 ./casper/filesystem.squashfs 
 ./install/netboot/pxelinux.cfg/default 
 ./install/netboot/pxelinux.0

---

### Post by rubicon on 2007-11-01
Forgot to mention that I already have got regular CD image for ubuntu 7.10. If that matters :)

About broken './casper/filesystem.squashfs' - can i replace it with the same file from the 'ubuntu-7.10-desktop-i386'?

---

### Post by zvacet on 2007-11-01
If you still have iso on your hard drive try this.Download same iso with torrent but direct download to the folder with existing iso.That way torrent will just chek your iso and correct it if you have some errors.

---

### Post by rubicon on 2007-11-01
> **zvacet said:**
> If you still have iso on your hard drive try this.Download same iso with torrent but direct download to the folder with existing iso.That way torrent will just chek your iso and correct it if you have some errors.
Okay, thanks for advise, I'll try this.

Wonder if this will work...

About my idea with *replacements* :) - it seems that both files have same MD5 specified in 'md5sum.txt', so I'll try this too.

---

### Post by rubicon on 2007-11-01
[QUOTE="zvacet"]If you still have iso on your hard drive try this.[/QUOTE]

This works. And know what? - it really recovered the image! \\:D/

Many thanks to ya, I don't even imagine what i'd do if you hadn't helped me!

Without *much* pain I got new Ubuntu and now going to share it with groupmates at my uni. I think more people should [SIZE="1"][at least][/SIZE] try Ubuntu!

---

### Post by zvacet on 2007-11-01
Glad I can help.

> I think more people should [at least] try Ubuntu!

I agree with you!

---

