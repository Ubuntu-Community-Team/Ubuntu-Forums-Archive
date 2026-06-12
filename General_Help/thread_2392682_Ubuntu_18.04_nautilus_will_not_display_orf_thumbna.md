---
title: "Ubuntu 18.04 nautilus will not display orf thumbnails"
date: 2018-05-23
forum: General Help
---

### Post by bowens44 on 2018-05-23
I have not been able to get nautilus to display thumbnails for Olympus raw files from the Olympus e-m1 mkii camera. It displays thumbnails for canon CR2 raw files but not Oly ORF files.

These are the thumbnailers I have tried :

raw.thumbnailer

[Thumbnailer Entry]
TryExec=ufraw-batch
Exec=ufraw-batch --silent --size %s --out-type=png --noexif --output=%o --overwrite --embedded-image %i
MimeType=image/x-adobe-dng;image/x-canon-cr2;image/x-canon-crw;image/x-dcraw;image/x-fuji-raf;image/x-kodak-dcr;image/x-kodak-k25;image/x-kodak-kdc;image/x-minolta-mrw;image/x-nikon-nef;image/x-olympus-orf;image/x-panasonic-raw;image/x-pentax-pef;image/x-sigma-x3f;image/x-sony-arw;image/x-sony-sr2;image/x-sony-srf;

This one works in Linux Mint 18.3 for the orf files


I have also used the default gnome-raw.thumbnailer

[Thumbnailer Entry]
TryExec=gnome-raw-thumbnailer
Exec=gnome-raw-thumbnailer -s %s %u %o
MimeType=image/x-adobe-dng;image/x-canon-cr2;image/x-canon-crw;image/x-dcraw;image/x-fuji-raf;image/x-kodak-dcr;image/x-kodak-k25;image/x-kodak-kdc;image/x-minolta-mrw;image/x-nikon-nef;image/x-olympus-orf;image/x-panasonic-raw;image/x-pentax-pef;image/x-sigma-x3f;image/x-sony-arw;image/x-sony-sr2;image/x-sony-srf;

both files will display thumbnails for canon raw

Has anyone been able to get nautilus to show the thumbnails for orf files? I have gooogled endlessly and so far none of the solutions Ive found have worked

---

### Post by robstrube on 2018-05-26
I have the exact same problem.  No thumbnails are generated for .orf files in my file manager.  I was thinking that it might be something to do with the file size thresholds (look is the preferences for the Files application).  But mine is set to 4096 MB, so essentially any file under 4GB will have a thumbnail generated.  I'd also love to find a solution!

Edit 1: BTW, I was able to determine that with the ufraw-batch approach, the thumbnails are actually failing generation.  You can confirm this by looking in your ~/.cache/thumbnails folder.  You'll see a "failure" folder, with all the thumbnail generation attempts.  This means that the DE *is* actually trying to generate the thumbnails using ufraw-batch, but for whatever reason it's failing.

Edit 2: Yup it looks like ufraw-batch is segfaulting!  Here's the appropriate log entries from my syslog (one segfault for each and every thumbnail creation attempt):

[FONT=courier new]May 26 12:49:13 RYZEN kernel: [ 2896.326148] show_signal_msg: 11 callbacks suppressed
May 26 12:49:13 RYZEN kernel: [ 2896.326150] ufraw-batch[16764]: segfault at 38 ip 00007f800c2d4b64 sp 00007fff8280a470 error 4 in liblensfun.so.0.3.2[7f800c2c1000+1a000]
May 26 12:49:13 RYZEN kernel: [ 2896.545696] ufraw-batch[16769]: segfault at 38 ip 00007ff22f849b64 sp 00007ffcc2abb780 error 4 in liblensfun.so.0.3.2[7ff22f836000+1a000]
May 26 12:49:13 RYZEN kernel: [ 2896.767056] ufraw-batch[16774]: segfault at 38 ip 00007fb0b0c74b64 sp 00007fff06c01e90 error 4 in liblensfun.so.0.3.2[7fb0b0c61000+1a000]
May 26 12:49:13 RYZEN kernel: [ 2896.989731] ufraw-batch[16779]: segfault at 38 ip 00007f8376a74b64 sp 00007ffff3628ab0 error 4 in liblensfun.so.0.3.2[7f8376a61000+1a000]
May 26 12:49:14 RYZEN kernel: [ 2897.216920] ufraw-batch[16784]: segfault at 38 ip 00007f01c5044b64 sp 00007ffdb80928b0 error 4 in liblensfun.so.0.3.2[7f01c5031000+1a000]
May 26 12:49:14 RYZEN kernel: [ 2897.448323] ufraw-batch[16789]: segfault at 38 ip 00007f63149b8b64 sp 00007fff41cb6f90 error 4 in liblensfun.so.0.3.2[7f63149a5000+1a000]
May 26 12:49:14 RYZEN kernel: [ 2897.675908] ufraw-batch[16794]: segfault at 38 ip 00007f617748fb64 sp 00007ffd09384520 error 4 in liblensfun.so.0.3.2[7f617747c000+1a000]
May 26 12:49:14 RYZEN kernel: [ 2897.903075] ufraw-batch[16799]: segfault at 38 ip 00007fd202cbab64 sp 00007ffc6b46aa60 error 4 in liblensfun.so.0.3.2[7fd202ca7000+1a000]
May 26 12:49:14 RYZEN kernel: [ 2898.131585] ufraw-batch[16804]: segfault at 38 ip 00007faf4ea4ab64 sp 00007fff1e191f90 error 4 in liblensfun.so.0.3.2[7faf4ea37000+1a000]
May 26 12:49:15 RYZEN kernel: [ 2898.357078] ufraw-batch[16809]: segfault at 38 ip 00007f6aa048fb64 sp 00007ffec108f6c0 error 4 in liblensfun.so.0.3.2[7f6aa047c000+1a000]
May 26 12:49:18 RYZEN kernel: [ 2901.370154] show_signal_msg: 12 callbacks suppressed
[/FONT]
Edit 3: This appears to actually be a bug in liblensfun.  You can see more here: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=862662](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=862662) and here is the ubuntu bug report: [https://bugs.launchpad.net/ubuntu/+source/ufraw/+bug/1768855?comments=all](https://bugs.launchpad.net/ubuntu/+source/ufraw/+bug/1768855?comments=all)

Edit 4: Please note (in bugs.launchpad) that the bug also affects you so we can get some traction on it.

---

### Post by mc4man on 2018-05-26
Is there a sample orf file somewhere?

---

### Post by bowens44 on 2018-05-28
> **mc4man said:**
> Is there a sample orf file somewhere?


Here's one of mine( I think this will work, never shred like this before)

[https://www.dropbox.com/s/tu2qblrwdqlcuvy/P5220001.ORF?dl=0](https://www.dropbox.com/s/tu2qblrwdqlcuvy/P5220001.ORF?dl=0)

---

### Post by smolinux on 2018-10-23
I had a similar issue in 18.04. I had no raw thumbnails at all in Thunar, and the same segfaulting in ufraw after trying that solution. However ufraw was still generating thumbnails before the segfault, so I think the two problems aren't related. I did some more googling and eventually ran this command:

sudo update-mime-database

And then thunar -q for good measure before opening up Thunar. And sure enough, I have thumbnails now.

---

### Post by Apanta on 2019-05-09
Sorry, maybe I'm off Topic.
I had the problem of not seeing the thumbnails of my photos, on Ubuntu 16.04.
but I wanted to tell you that I solved the problem simply by going to my home ---> Contr + h ---> .cache folder and renaming the Thumbnails folder in Thumbnails.old
By restarting the PC and going to my photo archive I saw the previews as I saw them a few months ago.
I checked again and inside the .cache folder the Thumbnails folder was recreated, so I deleted the one I had renamed.
game over.
Maybe it will serve as an input for those with this problem.

---

### Post by oldos2er on 2019-05-09
Old thread closed.

---

