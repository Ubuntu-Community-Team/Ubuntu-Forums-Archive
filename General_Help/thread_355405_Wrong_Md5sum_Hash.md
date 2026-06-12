---
title: "Wrong Md5sum Hash"
date: 2007-02-07
forum: General Help
---

### Post by ausgnome on 2007-02-07
I've being trying to download  6.10  desktop for the last few days and the md5sum is always wrong 
including the bittorent downloads. I've tried 5 different servers in bthe Asia Pacific area

  Anyone know of another source ??

---

### Post by JamieC on 2007-02-07
Are you sure it is definitely wrong? An incorrect hash five times in a row seems incredibly unlikely (and unlucky!).

What tool are you using to compare the checksums? Are you sure you are using the right hashing algorithm (not SHA1?)?

What are you using to download the images?

---

### Post by taurus on 2007-02-07
How did you download the ISO image?  Did you do it in Windows, using IE or firefox?

---

### Post by mcduck on 2007-02-07
> **ausgnome said:**
> I've being trying to download  6.10  desktop for the last few days and the md5sum is always wrong 
including the bittorent downloads. I've tried 5 different servers in bthe Asia Pacific area

  Anyone know of another source ??

If you use torrent it should be practically impossible to get wrong md5, as bittorrent itself checks the files while downloading..

Are you sure that you are comparing with the right MD5 for the disk image you downloaded?

---

### Post by PriceChild on 2007-02-07
Could you paste the output of```
md5sum <<file>>
```Including the line you need to initiate the md5sum so that we can compare it to the file and check you haven't read something wrong somewhere.

E.g.```
$ md5sum portage-latest.tar.bz2 
4bc155ddae6842f79119af15633a2ef8  portage-latest.tar.bz2
```

> **mcduck said:**
> If you use torrent it should be practically impossible to get wrong md5, as bittorrent itself checks the files while downloading.Happenned to me once using Azureus grrr...

---

### Post by ausgnome on 2007-02-07
md5sum ubuntu-6.10-desktop-i386.iso
b79070a5780c6314aa32c21e3227865a  ubuntu-6.10-desktop-i386.iso

  I'm using Ubuntu/Firefox to download 

   and torrents never finish stays at 97%  then continually tries to redownload the same two "pieces" due to hash check errors

---

### Post by PriceChild on 2007-02-07
Yup that's definately wrong.

I'm wondering about whether using rsync could help things sort themselves out...

---

### Post by mcduck on 2007-02-07
well, that is definitely wrong..

I just run MD5sum on the iso file I've been using (with success) and the correct on would be this: b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso

Do you happen to have nForce-based motherboard? The built-in firewall in some of those is known to cause corrupted downloads.. Then again broken RAM can do the same thing, but if that would be the problem you'd probably already noticed that something is wrong..

---

