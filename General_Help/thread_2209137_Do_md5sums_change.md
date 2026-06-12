---
title: "Do md5sums change?"
date: 2014-03-04
forum: General Help
---

### Post by bjngchn on 2014-03-04
Making reference to : [http://ubuntuforums.org/showthread.php?t=1927046](http://ubuntuforums.org/showthread.php?t=1927046)  598b48059bafa2e0314bce8a07a9ff1f *ubuntu-10.04.4-alternate-i386.iso  I have a different string: 3019b5603e..... for kubuntu-10.04.4-alternate-i386.iso  It was downloaded from original source (probably). What to do now?: 1. Be suspicious of  all *ub* , 2. Be suspicious of the site where it was downloaded from, 3. Download again and check again. 4. ubuntu and kubuntu have different md5sums.   ============ I guess 1. would be too obvious, and probably and hopefully doesn't happen. 4 makes most sense but then answer here would be incorrect: [http://ubuntuforums.org/showthread.php?t=1927046](http://ubuntuforums.org/showthread.php?t=1927046)

---

### Post by Lars Noodén on 2014-03-04
Which site did you download from?  Your main option is to try downloading again.  I would recommend using a torrent if possible because the download process includes checksumming and by the time the image has downloaded, it is complete and accurate.

---

### Post by sudodus on 2014-03-04
You should always check the md5sums, and they should match what is uploaded at

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

The Ubuntu iso files are different from the corresponding Kubuntu, Lubuntu and Xubuntu iso files of the same version, and then the md5sums will also be different. Each md5sum is calculated from all the file's own data, and the main purpose is to give you an opportunity to check that the download was correct. It is not a method to give you a highest security guarantee, that nobody has tampered with the iso file.

But the alternate and desktop iso files of Ubuntu and Kubuntu 10.04 LTS passed end of life in April 2013, and do not receive any updates, not even security updates for the desktop program packages, so I recommend that you install a current version, 12.04 LTS or 13.10 of either of them (Ubuntu or Kubuntu). Only Ubuntu Server 10.04 LTS receives updates (until April 2015).

See this link for more tips about security [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by bjngchn on 2014-03-04
I don't remember the exact site name but it was almost as obvious as ubuntu.com...Problem here is,  this page:  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) doesn't contain all md5sum info.  kubuntu-10.04.4-alternate-i386.iso is not listed. Is this a normal (acceptable) thing ?

---

### Post by ajgreeny on 2014-03-04
Simple answer:-
If the image has not changed or been updated in any way, the md5sum will not change either.  Only updated .iso image files will have a new md5sum as happens with the daily .iso images available for 14.04, which I update regularly using zsync to avoid downloading the whole image again.

Sudodus is right about that desktop version being EOL, so there is no real point trying to install it again; the server version still has nearly two years support remaining, but I would still not bother with that old version of server software when newer versions are available.

---

### Post by bjngchn on 2014-03-04
Ok, I found it here: [http://old-releases.ubuntu.com/releases/kubuntu/lucid/MD5SUMS](http://old-releases.ubuntu.com/releases/kubuntu/lucid/MD5SUMS) ; it is strange some versions are ignored on:  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by ajgreeny on 2014-03-04
> **bjngchn said:**
> Ok, I found it here: [http://old-releases.ubuntu.com/releases/kubuntu/lucid/MD5SUMS](http://old-releases.ubuntu.com/releases/kubuntu/lucid/MD5SUMS) ; it is strange some versions are ignored on:  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

That's because those versions are now EOL, so why bother showing their hashes on the main link?

---

### Post by sudodus on 2014-03-04
The UbuntuHashes wiki page is maintained by volunteers, and it is not normal that an md5sum of a released iso file is missing, but I think it is acceptable until you find it and fix it ;-)

On the other hand, it is not high priority to fix it for an iso file that has passed end of life, so I don't expect that you should fix it. But you are very welcome to help maintaining some Ubuntu wiki page, help testing the next version (now Trusty Tahr, to be released in April as 14.04 LTS) or some other task. Choose to do something that you enjoy :-)

---

