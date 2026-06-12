---
title: "Getting a different MD5 checksum each time I check it."
date: 2017-11-04
forum: General Help
---

### Post by 44daniel on 2017-11-04
Whenever I download a large file (over 1GB), if I do an md5sum on the file in Terminal, weird things happen:


[LIST=1]
[*]The checksum returned never matches what it's supposed to be. In this case, I checked using the UbuntuStudio 17.10 iso 
[*]If I do a md5sum on the file with a short delay between each try, the hash stays the same on sequential tries (as in pics) 
[*]But if I wait a few minutes between tries, the hash of the file changes(!) (as in pics) 
[/LIST]

I've tried downloading the iso file multiple times with both direct download and Bittorrent, onto 2 different hard drives in my system. Same problem in both cases.
Problem first happened in UbuntuStudio 64 bit 17.10, then I used a live USB to clean install Ubuntu 64bit 17.10 instead, and it still happens.
Not limited to md5, same problem happens using SHA256.
I can't figure out what the problem is. Any help would be very appreciated.

---

### Post by sudodus on 2017-11-04
This indicates a serious problem.

- Maybe a library or driver is faulty (does not work with your hardware). In this case, it should work with another version of Ubuntu [Studio]. Try the LTS version (16.04) live (booted from USB).

- Maybe your RAM is bad. You can test it with **memtest** that you find in the boot meny (syslinux or grub, depending on boot method).

---

### Post by HermanAB on 2017-11-04
Because the file is still busy downloading.

---

### Post by sudodus on 2017-11-04
> **HermanAB said:**
> Because the file is still busy downloading.

Good catch :KS I did not think of this. Let us hope that you are right :-)

---

### Post by 44daniel on 2017-11-04
@[**[COLOR=#DD4814][B]sudodus**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1499021")
I installed UbuntuStudio 16.04 (LTS) as you suggested and the problem seems to be resolved now. If the problem was indeed a library or driver being faulty, is there a way I can submit information about my system so that future versions of Ubuntu can be compatible with them?

- Bad RAM wasn't the problem. I've ran Memtest86+ a few weeks ago, and I've ran it again today and there were 0 errors both times

@[**[COLOR=#000000]HermanAB[/COLOR]**]("https://ubuntuforums.org/member.php?u=44990")
The file download being incomplete wasn't the problem either, I made sure it was finished downloading and that my torrent program shut off completely before checking the md5 hash.

---

### Post by sudodus on 2017-11-05
If the error with different md5sums occurs also when the system is booted from DVD or USB, 'Try Ubuntu Studio', you can

1. Create a user account at [http://launchpad.net](http://launchpad.net)

2. Provoke the bug to create the error

3. Run the following command

```
ubuntu-bug coreutils
```

**coreutils** is the program package containing the program **md5sum**.

This may be wrong, the bug may be in some library, but I cannot identify better than this. A developer with much more insight can change the focus of the bug report later on.

4. When automatically moved to the Launchpad web site, you can try to explain with words what you did and what happened.

---

