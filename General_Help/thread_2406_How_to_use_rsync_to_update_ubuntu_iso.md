---
title: "How to use rsync to update ubuntu iso?"
date: 2004-10-27
forum: General Help
---

### Post by Prem on 2004-10-27
Hi,

After first downloading the ubuntu with Azureus (BitTorrent client, warty-release-install-i386.iso.torrent) and getting a corrupt download (can that happen with Azureus, strange?), I tried jigdo (warty-release-install-i386.jigdo) to end up with similar results. The md5 digest of downloads did not match, both the times.

The jigdo download does not even complete. Says:
------------------------------
Aaargh - 69 files could not be downloaded. This should not
happen! Depending on the problem, it may help to retry downloading
the missing files.
------------------------------
Most of the missing files are under doc/manual directory.  I have tried the update at different times of the day to get the same result.

After renaming the warty-release-install-i386.iso.tmp to warty-release-install-i386.iso, I attempted to burn to a CD with nero6. Nero6 refuses to burn it after a message about bad ISO file.

Not wanting to download the full ISO again as I get charged per MB of download, I turned towards rsync. I can not figure out how to use rsync and where to find the ISO file on an rsync server or what rsync command to use, and would appreciate help on same.

Having looked at the download server I found many directories and but no ISO file to feed to rsync. For example, on [http://mirror.isp.net.au/ftp/pub/ubuntu/](http://mirror.isp.net.au/ftp/pub/ubuntu/), I found the following directories: dists/, indices/, misc/, pool/, but no ISO file under them (or did I just miss it, is there a way to search recursively on an ftp server?)

If there is no ISO file to be used with rsync where do I find the ubuntu files to rsync, and the command to update the bad ISO I have?

Has any one else faced the problem of incomplete download of warty-release-install-i386.jigdo?

Any suggestions to solve the problem are appreciated.

Thanks
Prem

---

### Post by flygmaskin on 2004-10-27
That sounds really weird. You shouldn't be able to get a corrupt file through bittorent (unless it was corrupt from the beginning). Have you tried downloading it with the original bittorrent client?

```
$ sudo apt-get install bittorrent
$ btdownloadcurses wart-blabla-bla.torrent
```

---

### Post by Prem on 2004-10-27
I picked up the url from torrent download from ubuntu site (primary server)  as well as the bittorrent client from sourceforge directly. 

I have been using Azureus for few months now, and have download few dozens of ISO files, but have had bad iso files couple of times.

Prem

---

### Post by FLeiXiuS on 2004-10-27
[QUOTE=Prem]I picked up the url from torrent download from ubuntu site (primary server)  as well as the bittorrent client from sourceforge directly. 

I have been using Azureus for few months now, and have download few dozens of ISO files, but have had bad iso files couple of times.

Prem[/QUOTE]


have you tried directly downloading the ISO?  Not the torrent

---

### Post by Prem on 2004-10-27
I get charged per MB of download by my ISP, and having downloaded over 500MB with torrent client ( and not counting the upload), and over 500MB with jigdo, I would like to leave the downloading of ISO as last option now. 

I am hoping I can get the missing 69 files with rsync and update my ISO file.

Prem

---

### Post by FLeiXiuS on 2004-10-27
Hmm...

I haven't ever had a problem with it.  I will ask the dev's.

---

