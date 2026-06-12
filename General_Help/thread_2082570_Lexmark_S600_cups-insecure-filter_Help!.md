---
title: "Lexmark S600 cups-insecure-filter Help!"
date: 2012-11-09
forum: General Help
---

### Post by lJ9%3MR&gt;sa on 2012-11-09
**_*XUBUNTU 12.10*_**
I have a problem with my Lexmark Interact S605. I installed it using the DEBs from lexmark.com, but I'm having the cups-insecure-filter problem. On my dad's laptop I didn't have this problem. I tried changing permissions of ```
/usr/local/lexmark/v3/bin/printfilter
``` In my printer settings I get the following error ```
Idle - Directory "/usr/local/lexmark/v3/bin" has insecure permissions (040775/uid=0/gid=2).
``` I have also tried changing permissions of the entire folder to no avail. I also deleted the printer from the Printers menu and from the "Lexmark Printer Utility" and reinstalled all the DEBs I downloaded. I can repeat the steps if necessary.

ls -l of the file /usr/local/lexmark/v3/bin/printerfilter ```
-rwxr-xr-x 1 root root 146921 Aug 16 02:35 /usr/local/lexmark/v3/bin/printfilter

```

ls -l of the directory /usr/local/lexmark/v3/bin/ ```
-rwxr-xr-x 1 root bin  755469 Aug 16 02:35 lxhcp
-rwxrwxr-x 1 root bin  110411 Aug 16 02:35 lxusb
-rwxr-xr-x 1 root root 146921 Aug 16 02:35 printfilter

```

If my Xubuntu install being spread out on different drives causes a problem, here is my fstab. ```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=a055f3cb-4794-4349-8340-cabd30eb4ded /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=ae978e2d-129c-40de-ac24-3e44c58060b8 /home           ext4    defaults        0       2
# /tmp was on /dev/sdc1 during installation
UUID=9409a960-05f5-410e-8d7a-1586becd675c /tmp            ext4    defaults        0       2
# /usr was on /dev/sdb5 during installation
UUID=9542e939-33b8-4f0d-84e5-aa06b2abe2ba /usr            ext4    defaults        0       2
# swap was on /dev/sdc5 during installation
UUID=f387c021-a3d7-4d94-ad3d-0d20e6e7ea55 none            swap    sw              0       0

```

My uname -a info ```
Linux nathan-xubuntu 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by lJ9%3MR&gt;sa on 2012-11-10
Anyone else have this problem? I've got something confidential that I MUST print. Thank you

---

### Post by lJ9%3MR&gt;sa on 2012-11-11
I'm sad since I have no help. No one else must have this problem.... Is it in the wrong category? :(

---

### Post by lJ9%3MR&gt;sa on 2012-11-11
Since no one could help me, I finally figured it out.

Run this in terminal:
```
sudo chmod 755 /usr/local/lexmark/v3/bin
```

```
sudo chgrp root /usr/local/lexmark/v3/bin/printfilter
```

---

### Post by sternchen on 2012-11-20
Dude, I had about the same problem. 
I just had to adjust the path to /usr/local/lexmark/lxk08/bin (/printdriver).
I still get an error but now the error about permissions is gone.
So THANKS a LOT for posting how you got your problem solved ;-)

regards,
sunnysnowflake

---

### Post by sitro on 2013-01-16
same problem for me for a Lexmark S305 on xubuntu 12.10.


I just change the permission on the file :
cd /usr/local/lexmark/v3/bin/
sudo chmod 755 printfilter

and it solves.

---

### Post by wsscott on 2013-04-11
I had the same problem on using Mint 13.  Sitro's post solved it.

---

### Post by jamesfromkent on 2013-05-18
Me too, same issue with a Lexmark Pro 901. Thanks all!

---

### Post by ebotts on 2013-08-03
Any suggestions on whether to throw my Lexmark Platinum Pro905 from a rooftop, interstate bridge, or at a moving train?

I've had this problem off and on for the past four years. Any time I decide to switch Linux distros, the rotten printer throws a fit and says some file (not always the same one) has insecure permissions. Once in a while, it'll work (poorly), as it did on Debian 6, and it worked beautifully a few Ubuntu versions back. Right now I'm running Mint 15 MATE on one machine and Ubuntu Studio 13.04, and I get the same error on both: "File '/usr/local/lexmark/v3/bin/printfilter' has insecure permissions."

I've tried chown and chgrp on the file to several different users, including eric (my username), root, 700, and 750 on the Mint computer, but no luck. It was a pain trying to troubleshoot on the Ubuntu Studio computer, so I thought I'd figure it out on Mint and apply the solution to my other computer.

---

### Post by Marius_van_Heerden on 2014-05-02
Did What Sitro suggested and changed the permission on the file :
[INDENT] cd /usr/local/lexmark/v3/bin/
sudo chmod 755 printfilter

  if it does nott solve it. Try to right click on your printer and take off shared. That worked for me. 				
[/INDENT]

---

### Post by reignaldo on 2015-03-28
I have Lexmark S408 here. LinuxMint 17. Solved the error with:

[COLOR=#000000]I just change the permission on the file :[/COLOR]
[COLOR=#000000]cd /usr/local/lexmark/v3/bin/[/COLOR]
[COLOR=#000000]sudo chmod 755 printfilter[/COLOR]

---

### Post by lou_granda on 2015-03-30
[FONT=verdana]solved here too I have a Lexmark Platinum Pro 905 (2 trays) connected to **USB** on Kubuntu 14.04

this worked for me and here are steps I followed on a fesh and updated install of Kubuntu

I downloaded these from Lexmark

lexmark-inkjet-legacy-1.0-1.amd64.deb
lexmark-printer-utility-1.0-2.amd64.deb
lexmark-scan-legacy-1.1-1.amd64.deb

Right click on each >open with>QApt package installer>install package

used the lexmark printer utility to add the printer

opened printers from the hardware section of system settings

I tried to print a test page and received the "cups-insecure-filter"

then I followed **sitro**'s post which only solved for me after adding the cups restart command

cd /usr/local/lexmark/v3/bin/
sudo chmod 755 printfilter
sudo /etc/init.d/cups restart

_**Print report**_

all seems to work except for tray selection is in reverse, if I print to tray 2 it goes to tray 1 and if I print to tray 1 it goes to tray 2, I can live with that

_**Scan report**_

**Skanlite **
Found 4 devices each of which did not work for me at first, I would get a tearing image. 

Lexmark : Pro800-Pro900 Series
Lexmarklegacy_2_0_0:libusb/001/003

Lexmark : Pro800-Pro900 Series
Lexmarklegacy_2_0_0:libnet/0020006B2434

Lexmark : Pro800-Pro900 Series
Lexmarklegacy_1_0_0:libusb/001/003

Lexmark : Pro800-Pro900 Series
Lexmarklegacy_1_0_0:libnet/0020006B2434

**Xsane **
I then installed xsane from muon discover and everything works perfect and about 20x faster even at 600dpi
I went back to Skanlite for the sake of this post and it now works fine it is just slow hmm?

Anyhow I hope this helps the head scratchers out there 

side note:
I think my real problem that I had before I almost gave up trying to fix this printer problem after following all suggestions on these forums and elsewhere was I didn't follow proper procedure by using **kdesudo** and not sudo for gui applications namely dolphin which caused me problems and confusions regarding taking ownership of files. After seeing errors anytime I launched dolphin from Konsole I decided to do a fresh install. 

thanks
[/FONT]

---

