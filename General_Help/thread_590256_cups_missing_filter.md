---
title: "cups missing filter"
date: 2007-10-24
forum: General Help
---

### Post by vladilinsky on 2007-10-24
I have been trying to set up a printer/photocopier (canon imageRUNNER 600) in ubuntu 7.10. 

I use the codehost drivers.

it worked and still works under ubuntu 6.** (the other computers in the office) but when i try to set it up in 7.10 every thing goes good except when i try to print, after a few seconds it changes from pending to stopped. and the printer manager says it is disabled (both in cups localhost and codehost-config)
and the ubuntu printing manager says

*printer 'ir600': 'cups-missing-filter'*

the cups_error log has this error in it

[I]D [24/Oct/2007:21:03:43 +0000] Loading printer IR600...
D [24/Oct/2007:21:03:43 +0000] Discarding unused printer-state-changed event...
W [24/Oct/2007:21:03:43 +0000] DNS-SD registration of "IR600" failed with -65537
E [24/Oct/2007:21:03:43 +0000] Filter "efippd" for printer "IR600" not available: Permission denied
W [24/Oct/2007:21:03:43 +0000] DNS-SD registration of "IR600" failed with -65537
E [24/Oct/2007:21:03:43 +0000] Filter "efippd" for printer "IR600" not available: Permission denied
W [24/Oct/2007:21:03:43 +0000] DNS-SD registration of "IR600" failed with -65537
I [24/Oct/2007:21:03:43 +0000] Loading job cache file "/var/cache/cups/job.cache"...[/I]

i have tried this on two different computers with 7.10 on them nether works but all the 6 series ubuntu machines do (its a church office they have 4 computers)
when i contact code host they tell me that they have tested on ubuntu 7.10 and it works, they do not want to give me more help than that though

any clues ideas or suggestions would be great.

thanks
Vlad

---

### Post by KevinCole on 2007-10-26
I'm in the same boat.  A closer examination says "Ready: Unable to start filter "efippd" - Permission denied."  The file (and symbolic links) are all in place, and have world read/execute permissions... It was still working in 7.04 (Feisty).  Gutsy's what kills it.

---

### Post by KevinCole on 2007-10-26
See the bug report at:

[https://bugs.edge.launchpad.net/ubuntu/+source/cupsys/+bug/133818](https://bugs.edge.launchpad.net/ubuntu/+source/cupsys/+bug/133818)

I haven't fixed my problem yet, but this seems to give an idea as to the source of the trouble.

---

### Post by vladilinsky on 2007-10-28
Thanks for your replys, that bug report looks promising. I will try it as soon as im in the office again

---

### Post by vladilinsky on 2007-11-01
the command
sudo aa-complain cupsd
(which i found in the bug report) has fixed my problem. apparently its something to do with app armour and 3'rd party print drivers


thanks for your help everyone

---

### Post by carpex on 2007-11-06
> **vladilinsky said:**
> the command
sudo aa-complain cupsd
(which i found in the bug report) has fixed my problem. apparently its something to do with app armour and 3'rd party print drivers


That worked for me too using the Codehost Canon drivers. 

CP

---

### Post by dmorfe on 2007-11-06
I have a Brother HL-4040CN and it was experiencing the same CUPS-FILTER-MISSING error.

I solved it by running sudo aa-complain cupsd.

Thanks for your help.

DM

---

### Post by scottie4442 on 2007-11-26
the sudo aa-complain cupsd command also fixed our office printing issues, we use 7.10 and are now printing fine. Thanks for the help

---

### Post by rx_ubulin on 2008-04-08
Hello,

I am using Canon-ir2270 printer. Connected over LAN.

It was working fine yesterday. I configured it in the below way:

1. Downloaded the file cndrvcups-ufr2-uk_1.50-2_i386.deb
2. Run the below command:
      $ file-roller --extract-here cndrvcups-ufr2-uk_1.50-2_i386.deb
          OR
       Use Archive Manager to unzip .deb file to somewhere.
3. Now go to folder cndrvcups-ufr2-uk_1.50-2_i386
4. Unzip control.tar.gz and data.tar.gz. This will create usr and control folders.
5. Now locate ./usr/share/cups/model/CNCUPSIR2230ZK.ppd file in this case. This file need to be provided to cups.
6. Now open [http://localhost:631/](http://localhost:631/) in a we browser. This will open the cups intergace to you.
7. Click on Add Printer
8. Fill in Name:,  Location: and Description:, anything you like, then select next.
   E.g.: Name: Canon-IR22XX   Location: Somewhere   Description: Some Description
9. Now select Internet Printing Protocol (ipp) as your Device. Select next.
10. Now provide the path of your printer supporting ipp. In this case http://<*ipaddressofprinter*>/ipp. Select next.
11. Select Canon as Make. and provide the path of the file found in step 5. Select Add Printer.
12. Printer is added.
13. You can select Administration Tab for reconfiguring.

Afterwards i installed wine using apt-get.
It warned me that there are 3 packages lying redundant and suggested my below command to run:
sudo apt-get autoremove ( or something, not sure)...

After that I am not able to print anything. I get the below error in the jobs list status pane:
Printer 'Canon-Ir2270': 'cups-missing-filter'.

The wine installation may not be the problem. I was just guessing.

Please help.

---

### Post by flyinwild on 2008-04-27
Thanks for this tip. I was beginning to despair or ever getting our Brother 4040 CN ever working over the network as everything I tried even with the new drivers in Hardy still gave the "Unable to start filter "/usr/Brother/Printer/hl4040cn/cupswrapper/brlpdwrapper" error. Still not sure why it works as I have not configured app armour. But thanks anway!

---

### Post by PA_Dummy on 2008-07-09
Thanks !!

The above worked with my Samsung  SCX-4725FN

:)

---

