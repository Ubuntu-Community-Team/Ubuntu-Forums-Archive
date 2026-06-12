---
title: "Incorrect md5sum"
date: 2006-10-16
forum: General Help
---

### Post by satimis on 2006-10-16
Hi folks,

Browser - SeaMonkey
OS - Gentoo_64
gnome-light 


I download "ubuntu-6.06.1-server-amd64.iso" twice on Internet.  The md5sum checked was "adbb63e5d3c7c01a9ba3b7fe2d21cfe6  ubuntu-6.06.1-server-amd64.iso"

However according to its sum file it should read "8254b0f3696ed17c52a2cb59c9ebd2cc  ubuntu-6.06.1-server-amd64.iso".

Please advise what was the cause.  Whether I need to download it with wget.

Tried to download the ISO image with rtorrent
"ubuntu-6.06.1-server-amd64.iso.torrent"
without success because server not found.

TIA


B.R.
satimis

---

### Post by Sef on 2006-10-16
Sometimes you just have to keep downloading till the numbers match. Once I had to download some software about 6 times till the numbers matched.

---

### Post by PriceChild on 2006-10-16
You may want to try a different method of downloading such as wget yes.

I use gwget for large downloads.

---

### Post by satimis on 2006-10-16
Hi PriceChild,

I have the ISO image download successfully by running wget on FC5_64.  md5sum found correct.  I have no idea why there was problem to download the iso image on Gentoo_64.  Even with wget it always said connecting server failed.

Tks.

B.R.
satimis

---

