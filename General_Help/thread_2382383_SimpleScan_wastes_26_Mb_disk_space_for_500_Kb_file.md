---
title: "SimpleScan wastes 26 Mb disk space for 500 Kb files"
date: 2018-01-12
forum: General Help
---

### Post by lppoja on 2018-01-12
I have run into a strange, but a very frustrating problem.
I havenused Ubuntu and SimpleScan often and have been very satisfied. However, today, I see that SimpleScan wastes a lot of disk space.

The files that I scan are about 500 Kb per page - all one-page files. I see them in the file explorer as 500 Kb files. However, every time that I scan and save one such file, approximately 26 Mb of my disk space is lost. And I got down to zero very fast and I cannot continue my work at all.
I used BleachBit, which did not help much. Where is the space going? Emptying trash does not help either.
Also, the SimpleScan tends to crash today in a way that I have not experienced before.

I use a Ubuntu that is installed on a USB stick. Not a live usb, but an installation of my system. It is a 4 Gb disk theoretically, but the file explorer shows it as maximum 3,1 Gb, of which all has been used. (I have only installed LibreOffice Calc in addition to the original system).

---

### Post by VMC on 2018-01-12
Several folders you can check. "/tmp", "/var/tmp", also if you can install a very small program '*ncdu'* it will show exactly where space is used.
In meantime use:
```
sudo du -ah / | sort -n -r | head -n 10
```
change "/" to maybe /var". Either way, from root you'll find 10 largest space usage

---

### Post by Holger_Gehrke on 2018-01-12
'simple-scan' saves **uncompressed** images (as opposed to the final compressed 500kb files) of your pages in $HOME/.cache/simple-scan/autosaves/. The size of these depends on your chosen resolution, color depth and - of course - the size of the scanned image. For 300 dpi grayscale A4 scans you need about 2mb per  page. These get erased when you close simple-scan.

Holger

---

### Post by raleigh3 on 2018-01-12
> **lppoja said:**
> I have run into a strange, but a very frustrating problem.
I havenused Ubuntu and SimpleScan often and have been very satisfied. However, today, I see that SimpleScan wastes a lot of disk space.

The files that I scan are about 500 Kb per page - all one-page files. I see them in the file explorer as 500 Kb files. However, every time that I scan and save one such file, approximately 26 Mb of my disk space is lost. And I got down to zero very fast and I cannot continue my work at all.
I used BleachBit, which did not help much. Where is the space going? Emptying trash does not help either.
Also, the SimpleScan tends to crash today in a way that I have not experienced before.

I use a Ubuntu that is installed on a USB stick. Not a live usb, but an installation of my system. It is a 4 Gb disk theoretically, but the file explorer shows it as maximum 3,1 Gb, of which all has been used. (I have only installed LibreOffice Calc in addition to the original system).

You can install to a larger stick or install to a hard drive.

I use Xsane. It has more features than Simple Scanner.

Exiting Simple Scanner after a few scans seems like a pain.

---

### Post by lppoja on 2018-01-13
Thank you for all the helpful suggestions.
I finished my work this time by simply closing SimpleScan after 3 or 4 files, as I understood that it really did take this room, but released it after closing.
I also installed a system for future use on a larger USB stick, and will keep in mind the suggestion about Xsane.

---

### Post by raleigh3 on 2018-01-13
Glad you're good to go.

---

