---
title: "Epson 3490 Scanner"
date: 2008-06-30
forum: General Help
---

### Post by venturosa on 2008-06-30
I have an Epson Perfection 3490 scanner which I eventually got working with feisty but since the upgrade to hardy it doesn't work and I can't remember what I did before to get it working. I'm fairly new to linux so it must have been quite easy.
Any help appreciated.

---

### Post by Rhubarb on 2008-06-30
Well, I can't say exactly, but if you follow what's said here:
[http://ubuntuforums.org/showthread.php?t=627650](http://ubuntuforums.org/showthread.php?t=627650)
and here:
[http://ubuntuguide.org/wiki/Dapper#Install_the_correct_drivers:_Epson_Perfection_V200_Photo_example](http://ubuntuguide.org/wiki/Dapper#Install_the_correct_drivers:_Epson_Perfection_V200_Photo_example)

You may need to possibly download a drivers from here;
[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

I don't know how well the 3490 Epson scanner is supported in Ubuntu, so it may well be easier to get going than an Epson V200 scanner.

With any luck it may refresh your memory.

---

### Post by Wollongong on 2008-07-16
Here's what I did to get Epson perfection 3490 working on Hardy:

# step 1: need sane-utils, missing from Hardy:
sudo apt-get install sane-utils
# step 2: get the firmware file maybe from your ms-win install, or
# apparently you can get it from
#  [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)
sudo cp /windows/C/WINDOWS/system32/esfw52.bin /usr/share/sane/snapscan/epson3490_firmware.bin
# edit /etc/sane.d/snapscan.conf to refer to the above firmware:
# uncomment the "firmware" line near the top and change to this:
firmware /usr/share/sane/snapscan/epson3490_firmware.bin
# plug in the scanner and power it up
sane-find-scanner  # should find your scanner
scanimage -L 
      # should also find it, might need to power cycle scanner if problem
scanimage -T      # should run through various tests
# now you should be able to run Applications->Graphics->XSane Scanner


It was a bit more work than with earlier Ubuntus, but really worth the effort because the quality of scanning is now much better.

---

