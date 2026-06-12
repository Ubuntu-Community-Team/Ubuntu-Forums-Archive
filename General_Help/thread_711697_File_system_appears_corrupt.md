---
title: "File system appears corrupt"
date: 2008-02-29
forum: General Help
---

### Post by twin_57103 on 2008-02-29
Hi folks,

I've had my Ubuntu crash rather spectacularly and could use some help cleaning up the mess.  I believe I have  a problem with the file system.  I can boot to Windows or a Live CD, but Ubuntu does not boot.

Computer info: Dell Dimension 4700, 3.0 GHz P4, 1.5 Mb RAM, dual-boot Windows XP and Ubuntu 7.10 (installed Feisty, then upgraded to Gutsy)
2 SATA hard drives - an 80 Gb Windows drive (one partition) and one 200 Gb, 3 partitions: 100 Gb NTFS data partition, ext3 Ubuntu and swap.
Recent changes (last couple months): I added a TV card, which caused my on-board ethernet to fail - replaced it with a PCI network card (mid-January).  Replaced my failing DVD burner - installed beautifully (early February).
I have been trying to install mythtv for some time and had nothing but trouble.  I have gone through several install-purge cycles trying to get it to work.  The last attempt was perhaps a week ago.

Ubuntu was rather ill-behaved for a day or two - acting like a Windows 98 junker that has been visiting web sites of ill repute.  I'd try to open a program and nothing happened.  Brasero has been quite unstable for a while (slow to the point of crashing, try to open it and nothing happens for several minutes), but I've simply rebooted and used Windows - kept thinking I ought to do something about it, but didn't get around to it.  It seemed like it was Brasero, rather than the OS as a whole.

Last night was the first time it wouldn't boot at all.  I've been busy, so I hadn't thought much about the sluggishness other than rebooting and continuing what I was doing in Windows.  The day before I'd had trouble with Open Office loading (snail's pace, caused system instability) - again, I was busy, so I just rebooted and used Windows.  I don't remember any hard restarts (might have been one during the mythtv hassles).  I'm careful to shut down the OS properly.

See attached photo for the errors I'm getting when I try to boot.  I installed Linux Reader for Windows to be able to access the ext3 drive - the data seems OK (can also see it when booted from a live CD).  I've been through a hard drive crash in the past, so I'm pretty good about keeping backups, although I'll probably burn a new backup of the data partition for safety.

I can get around pretty well in Ubuntu, but I haven't done a lot of command-line or disk management.  It would be nice to get the system back without reinstalling, but if I need to wipe the partition and start over, I can deal with it.  Thanks for your time and help!

---

### Post by jwcgator on 2008-02-29
When that screen shows up have you tried running fsck?

---

### Post by twin_57103 on 2008-02-29
Not yet.  I wasn't certain what options to use.  As I mentioned, I'm pretty shaky when it comes to Linux command-line... :(
Can I just use fsck or should I include any other modifiers?

---

### Post by twin_57103 on 2008-02-29
After a long run through fsck (no command-line arguments), my system is back up.  When I got it back, I remembered another of the recent issues I've had - the computer detects updates, downloads then, but fails to install them.  It started with three security updates, but now I've had it with several more (recommended, non-security updates).

I had a python game (run from code) that is now corrupt and fails to run (quite a few errors in its directories during fsck).  Open office seemed to run smoothly.  Brasero started quickly, but soon froze up.  It shut down without having to force it.

I'm grateful to have my Linux back up, but it seems that there is something still going on.  Any advice on how to proceed?  I am wondering if I ought to wipe the partition and reinstall, but that's not a pleasant thought...

---

### Post by Herman on 2008-02-29
The best thing to do would be to boot your Ubuntu Live CD and open a terminal and run '[SIZE=-1][FONT=Bitstream Vera Sans Mono]sudo e2fsck -C0 -p -f -v /dev/hda2'
[/FONT][/SIZE]```
sudo e2fsck -C0 -p -f -v /dev/hda2
```Where: 'dev'hda2' is your Ubuntu file system (partition). If looking with GParted says it is something else, then please replace '/dev/hda2' with whatever you need.

That is a safe command, and should fix it and should never do any harm.

If you don't like using the command line, and your Ubuntu LiveCD is Gutsy or later, you can open Gnome Partition Editor (GParted), in your Ubuntu Live CD and right-click on the partition and click 'Check', and confirm that by clicking 'Apply' and 'Apply' again in the confirmation screen.
That will run 'e2fsck -f -y -v' for you but you should make a backup first as you can lose data with that command because of the -y option. It used to have the -p option, I don't know why they changed it to -y.  It's a more powerful medicine though, and will either kill it or cure it.

Regards, Herman :)

EDIT: Oops, too late, I see you've already fixed your file system. Good!

---

### Post by twin_57103 on 2008-02-29
Herman - thanks for the pointers.  I'm going to call it a night, but will look at this more tomorrow.

---

### Post by twin_57103 on 2008-03-01
Ugh - I said I was going to go to bed!

...I tried installing a couple programs (Gparted since I didn't have it, and black-box, a simple game from the universe repositories).  They won't install either.  I tried Gparted from the command line, and got this:

karin@karin-desktop:~$ sudo apt-get install gparted
[sudo] password for karin:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmpich1.0c2 lirc pwgen mysql-client libdc1394-13 libxml-libxml-common-perl
  libnet-daemon-perl libgtk1.2 libglib1.2 libswfdec0.3
  libxml-namespacesupport-perl libfame-0.9 python-mysqldb fftw2 php5
  libdbi-perl libpvm3 libdbd-mysql-perl mysql-server-5.0 mysql-client-5.0
  gcc-3.4-base libavformat1d libplrpc-perl dvdauthor expect libxml-libxml-perl
  mysql-server libxml-sax-perl libswscale1d ffmpeg transcode ntp tcl8.4
  libcdaudio1 libxml-simple-perl libgtk1.2-common mjpegtools php5-mysql
  libg2c0 libimlib2 libapache2-mod-php5 liblame0 php5-common
Use 'apt-get autoremove' to remove them.
Suggested packages:
  xfsprogs reiser4progs jfsutils ntfsprogs
The following NEW packages will be installed:
  gparted
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
Need to get 343kB of archives.
After unpacking 1954kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main gparted 0.3.3-2ubuntu6.1 [343kB]
Fetched 343kB in 3s (90.9kB/s)  
E: Sub-process /usr/bin/dpkg exited unexpectedly

Using the -f switch:
karin@karin-desktop:~$ sudo apt-get -f install gparted
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


I looked at the link, but found it a little confusing.  Can you offer any advice?

---

### Post by Herman on 2008-03-01
> the computer detects updates, downloads then, but fails to install them. It started with three security updates, but now I've had it with several more (recommended, non-security updates).
 Referring to this link,  [What to do when apt-get fails]("http://distrocenter.linux.com/article.pl?sid=05/10/12/1952217&tid=106")
 (read that first), try 'sudo apt-get check' and 'sudo apt-get -f install' or 'sudo apt-get -f remove' and see if either of those will fix it for you.
>  I had a python game (run from code) that is now corrupt and fails to run (quite a few errors in its directories during fsck). Open office seemed to run smoothly. Brasero started quickly, but soon froze up. It shut down without having to force it. What options did you run with your fsck? If you run an fsck with the -y option, it may move some of your files to the lost+found directory. They can be removed from there and placed back into your system, but it takes some knowledge and patience and may not be 100% successful. 
[quote]```
sudo ls -la /lost+found/
```

---

### Post by twin_57103 on 2008-03-01
I'll work on the installation problem tomorrow.  Here is the output from the lost & found folder:
karin@karin-desktop:~$ sudo ls -la /lost+found
[sudo] password for karin:
total 2492
drwx------  7 root  root  16384 2007-06-13 16:26 .
drwxr-xr-x 21 root  root   4096 2007-10-22 07:08 ..
drwxr-xr-x  2 karin karin  4096 2007-06-25 09:39 #2917889
drwxr-xr-x  2 karin karin  4096 2007-06-25 09:39 #2917890
drwxr-xr-x  5 karin karin  4096 2007-06-25 09:39 #2917891
-r--r--r--  1 karin karin    94 2007-06-25 09:39 #2917895
drwxr-xr-x  3 karin karin  4096 2007-06-25 09:39 #2917896
-rw-r--r--  1 karin karin   212 2007-08-13 21:12 #2918301
-rw-r--r--  1 karin karin   319 2007-08-13 21:12 #2918302
-rw-r--r--  1 karin karin  4773 2007-08-13 21:12 #2918303
-rw-r--r--  1 karin karin  4573 2007-08-13 21:12 #2918308
-rw-r--r--  1 karin karin  3105 2007-08-13 21:12 #2918309
-rw-r--r--  1 karin karin  4581 2007-08-13 21:12 #2918310
-rw-r--r--  1 karin karin   433 2007-08-13 21:12 #2918338
-rw-r--r--  1 karin karin  1428 2007-08-13 21:12 #2918339
-rw-r--r--  1 karin karin  2292 2007-08-13 21:12 #2918340
-rw-r--r--  1 karin karin  2160 2007-08-13 21:12 #2918341
-rw-r--r--  1 karin karin  3517 2007-08-13 21:12 #2918342
-rw-r--r--  1 karin karin  1799 2007-08-13 21:12 #2918343
-rw-r--r--  1 karin karin 10931 2007-08-13 21:12 #2918344
-rw-r--r--  1 karin karin  1971 2007-08-13 21:12 #2918345
-rw-r--r--  1 karin karin  4185 2007-08-13 21:12 #2918346
-rw-r--r--  1 karin karin  4170 2007-08-13 21:12 #2918347
-rw-r--r--  1 karin karin  2442 2007-08-13 21:12 #2918348
-rw-r--r--  1 karin karin  2738 2007-08-13 21:12 #2918349
-rw-r--r--  1 karin karin  1388 2007-08-13 21:12 #2918350
-rw-r--r--  1 karin karin  4207 2007-08-13 21:12 #2918351
-rw-r--r--  1 karin karin  3332 2007-08-13 21:12 #2918352
-rw-r--r--  1 karin karin  4637 2007-08-13 21:12 #2918353
-rw-r--r--  1 karin karin  3635 2007-08-13 21:12 #2918360
-rw-r--r--  1 karin karin   547 2007-08-13 21:12 #2918361
-rw-r--r--  1 karin karin  1727 2007-08-13 21:12 #2918362
-rw-r--r--  1 karin karin  1617 2007-08-13 21:12 #2918363
-rw-r--r--  1 karin karin  1468 2007-08-13 21:12 #2918364
-rw-r--r--  1 karin karin  2420 2007-08-13 21:12 #2918365
-rw-r--r--  1 karin karin  2933 2007-08-13 21:12 #2918366
-rw-r--r--  1 karin karin   584 2007-08-13 21:12 #2918367
-rw-r--r--  1 karin karin  1422 2007-08-13 21:12 #2918368
-rw-r--r--  1 karin karin  3751 2007-08-13 21:12 #2918369
-rw-r--r--  1 karin karin  2930 2007-08-13 21:12 #2918370
-rw-r--r--  1 karin karin  3751 2007-08-13 21:12 #2918371
-rw-r--r--  1 karin karin  3246 2007-08-13 21:12 #2918372
-rw-r--r--  1 karin karin   586 2007-08-13 21:12 #2918373
-rw-r--r--  1 karin karin  5450 2007-08-13 21:12 #2918374
-rw-r--r--  1 karin karin  9521 2007-08-13 21:12 #2918375
-rw-r--r--  1 karin karin  5851 2007-08-13 21:12 #2918376
-rw-r--r--  1 karin karin  1956 2007-08-13 21:12 #2918377
-rw-r--r--  1 karin karin   466 2007-08-13 21:12 #2918378
-rw-r--r--  1 karin karin  4555 2007-08-13 21:12 #2918379
-rw-r--r--  1 karin karin  7977 2007-08-13 21:12 #2918380
-rw-r--r--  1 karin karin  4292 2007-08-13 21:12 #2918381
-rw-r--r--  1 karin karin  1931 2007-08-13 21:12 #2918382
-rw-r--r--  1 karin karin   491 2007-08-13 21:12 #2918383
-rw-r--r--  1 karin karin  2044 2007-08-13 21:12 #2918384
-rw-r--r--  1 karin karin  7243 2007-08-13 21:12 #2918385
-rw-r--r--  1 karin karin   559 2007-08-13 21:12 #2918386
-rw-r--r--  1 root  root  46695 2007-10-15 05:55 #4441307
-rw-r--r--  1 root  root  49118 2007-10-15 05:55 #4441308
-rw-r--r--  1 root  root  48403 2007-10-15 05:55 #4441309
-rw-r--r--  1 root  root  47603 2007-10-15 05:55 #4441310
-rw-r--r--  1 root  root  48300 2007-10-15 05:55 #4441311
-rw-r--r--  1 root  root  52608 2007-10-15 05:55 #4441312
-rw-r--r--  1 root  root  47484 2007-10-15 05:55 #4441313
-rw-r--r--  1 root  root  46795 2007-10-15 05:55 #4441314
-rw-r--r--  1 root  root  46841 2007-10-15 05:55 #4441315
-rw-r--r--  1 root  root  46693 2007-10-15 05:55 #4441316
-rw-r--r--  1 root  root  47482 2007-10-15 05:55 #4441317
-rw-r--r--  1 root  root  46724 2007-10-15 05:55 #4441319
-rw-r--r--  1 root  root  46753 2007-10-15 05:55 #4441320
-rw-r--r--  1 root  root  51285 2007-10-15 05:55 #4441321
-rw-r--r--  1 root  root  47199 2007-10-15 05:55 #4441322
-rw-r--r--  1 root  root  46376 2007-10-15 05:55 #4441323
-rw-r--r--  1 root  root  46504 2007-10-15 05:55 #4441324
-rw-r--r--  1 root  root  51052 2007-10-15 05:55 #4441325
-rw-r--r--  1 root  root  46921 2007-10-15 05:55 #4441326
-rw-r--r--  1 root  root  56128 2007-10-15 05:55 #4441327
-rw-r--r--  1 root  root  47998 2007-10-15 05:55 #4441328
-rw-r--r--  1 root  root  47573 2007-10-15 05:55 #4441329
-rw-r--r--  1 root  root  44828 2007-10-15 05:55 #4441330
-rw-r--r--  1 root  root  47440 2007-10-15 05:55 #4441332
-rw-r--r--  1 root  root  44865 2007-10-15 05:55 #4441333
drwxr-xr-x  2 root  root   4096 2008-02-05 17:59 #4604626
-rw-r--r--  1 root  root    895 2008-02-04 14:26 #4605657
-rw-r--r--  1 root  root   4872 2004-11-20 14:16 #4605658
-rw-r--r--  1 root  root    246 2004-11-20 14:16 #4605659
-rw-r--r--  1 root  root    293 2004-11-20 14:16 #4605660
-rw-r--r--  1 root  root    242 2004-11-20 14:16 #4605661
-rw-r--r--  1 root  root    279 2004-11-20 14:16 #4605662
-rw-r--r--  1 root  root    247 2004-11-20 14:16 #4605663
-rw-r--r--  1 root  root    298 2004-11-20 14:16 #4605664
-rw-r--r--  1 root  root   2326 2004-11-20 14:16 #4605665
-rw-r--r--  1 root  root   1385 2004-11-20 14:16 #4605666
-rw-r--r--  1 root  root   2414 2004-11-20 14:16 #4605667
-rw-r--r--  1 root  root   1463 2004-11-20 14:16 #4605668
-rw-r--r--  1 root  root   2160 2004-11-20 14:16 #4605669
-rw-r--r--  1 root  root    216 2004-11-20 14:16 #4605670
-rw-r--r--  1 root  root    284 2004-11-20 14:16 #4605671
-rw-r--r--  1 root  root    233 2004-11-20 14:16 #4605672
-rw-r--r--  1 root  root    277 2004-11-20 14:16 #4605673
-rw-r--r--  1 root  root    205 2004-11-20 14:16 #4605674
-rw-r--r--  1 root  root    265 2004-11-20 14:16 #4605675
-rw-r--r--  1 root  root    246 2004-11-20 14:16 #4605676
-rw-r--r--  1 root  root    296 2004-11-20 14:16 #4605677
-rw-r--r--  1 root  root    246 2004-11-20 14:16 #4605678
-rw-r--r--  1 root  root    304 2004-11-20 14:16 #4605679
-rw-r--r--  1 root  root    148 2004-11-20 14:16 #4605680
-rw-r--r--  1 root  root    195 2004-11-20 14:16 #4605681
-rw-r--r--  1 root  root    308 2004-11-20 14:16 #4605682
-rw-r--r--  1 root  root    356 2004-11-20 14:16 #4605683
-rw-r--r--  1 root  root    251 2004-11-20 14:16 #4605684
-rw-r--r--  1 root  root    308 2004-11-20 14:16 #4605685
-rw-r--r--  1 root  root    268 2004-11-20 14:16 #4605686
-rw-r--r--  1 root  root    322 2004-11-20 14:16 #4605687
-rw-r--r--  1 root  root    247 2004-11-20 14:16 #4605688
-rw-r--r--  1 root  root    305 2004-11-20 14:16 #4605689
-rw-r--r--  1 root  root    235 2004-11-20 14:16 #4605690
-rw-r--r--  1 root  root    314 2004-11-20 14:16 #4605691
-rw-r--r--  1 root  root    242 2004-11-20 14:16 #4605692
-rw-r--r--  1 root  root    285 2004-11-20 14:16 #4605693
-rw-r--r--  1 root  root    251 2004-11-20 14:16 #4605694
-rw-r--r--  1 root  root    313 2004-11-20 14:16 #4605695
-rw-r--r--  1 root  root    246 2004-11-20 14:16 #4605696
-rw-r--r--  1 root  root    304 2004-11-20 14:16 #4605697
-rw-r--r--  1 root  root   1038 2004-11-20 14:16 #4605698
-rw-r--r--  1 root  root    315 2004-11-20 14:16 #4605699
-rw-r--r--  1 root  root    214 2004-11-20 14:16 #4605700
-rw-r--r--  1 root  root    272 2004-11-20 14:16 #4605701
-rw-r--r--  1 root  root    225 2004-11-20 14:16 #4605702
-rw-r--r--  1 root  root    272 2004-11-20 14:16 #4605703
-rw-r--r--  1 root  root    167 2004-11-20 14:16 #4605704
-rw-r--r--  1 root  root    202 2004-11-20 14:16 #4605705
-rw-r--r--  1 root  root    163 2004-11-20 14:16 #4605706
-rw-r--r--  1 root  root    232 2004-11-20 14:16 #4605707
-rw-r--r--  1 root  root    238 2004-11-20 14:16 #4605708
-rw-r--r--  1 root  root    290 2004-11-20 14:16 #4605709
-rw-r--r--  1 root  root    236 2004-11-20 14:16 #4605710
-rw-r--r--  1 root  root    282 2004-11-20 14:16 #4605711
-rw-r--r--  1 root  root    225 2004-11-20 14:16 #4605712
-rw-r--r--  1 root  root    242 2004-11-20 14:16 #4605713
-rw-r--r--  1 root  root    305 2004-11-20 14:16 #4605714
-rw-r--r--  1 root  root    272 2004-11-20 14:16 #4605715
-rw-r--r--  1 root  root    243 2004-11-20 14:16 #4605716
-rw-r--r--  1 root  root    290 2004-11-20 14:16 #4605717
-rw-r--r--  1 root  root    219 2004-11-20 14:16 #4605718
-rw-r--r--  1 root  root    284 2004-11-20 14:16 #4605719
-rw-r--r--  1 root  root    221 2004-11-20 14:16 #4605720
-rw-r--r--  1 root  root    260 2004-11-20 14:16 #4605721
-rw-r--r--  1 root  root    220 2004-11-20 14:16 #4605722
-rw-r--r--  1 root  root    262 2004-11-20 14:16 #4605723
-rw-r--r--  1 root  root    249 2004-11-20 14:16 #4605724
-rw-r--r--  1 root  root    279 2004-11-20 14:16 #4605725
-rw-r--r--  1 root  root    217 2004-11-20 14:16 #4605726
-rw-r--r--  1 root  root    280 2004-11-20 14:16 #4605727
-rw-r--r--  1 root  root    223 2004-11-20 14:16 #4605728
-rw-r--r--  1 root  root    280 2004-11-20 14:16 #4605729
-rw-r--r--  1 root  root  11977 2004-11-20 14:16 #4605730
-rw-r--r--  1 root  root   8898 2004-11-20 14:16 #4605731
-rw-r--r--  1 root  root    274 2004-11-20 14:16 #4605732
-rw-r--r--  1 root  root    307 2004-11-20 14:16 #4605733
-rw-r--r--  1 root  root    309 2004-11-20 14:16 #4605734
-rw-r--r--  1 root  root    355 2004-11-20 14:16 #4605735
-rw-r--r--  1 root  root    286 2004-11-20 14:16 #4605736
-rw-r--r--  1 root  root    323 2004-11-20 14:16 #4605737
-rw-r--r--  1 root  root    268 2004-11-20 14:16 #4605738
-rw-r--r--  1 root  root    316 2004-11-20 14:16 #4605739
-rw-r--r--  1 root  root    276 2004-11-20 14:16 #4605740
-rw-r--r--  1 root  root    306 2004-11-20 14:16 #4605741
-rw-r--r--  1 root  root    172 2004-11-20 14:16 #4605742
-rw-r--r--  1 root  root    235 2004-11-20 14:16 #4605743
-rw-r--r--  1 root  root    249 2004-11-20 14:16 #4605744
-rw-r--r--  1 root  root    297 2004-11-20 14:16 #4605745
-rw-r--r--  1 root  root    243 2004-11-20 14:16 #4605746
-rw-r--r--  1 root  root    258 2004-11-20 14:16 #4605747
-rw-r--r--  1 root  root    237 2004-11-20 14:16 #4605748
-rw-r--r--  1 root  root    284 2004-11-20 14:16 #4605749
-rw-r--r--  1 root  root    251 2004-11-20 14:16 #4605750
-rw-r--r--  1 root  root    295 2004-11-20 14:16 #4605751
-rw-r--r--  1 root  root    249 2004-11-20 14:16 #4605752
-rw-r--r--  1 root  root    289 2004-11-20 14:16 #4605753
-rw-r--r--  1 root  root    188 2004-11-20 14:16 #4605754
-rw-r--r--  1 root  root    242 2004-11-20 14:16 #4605755
-rw-r--r--  1 root  root    198 2004-11-20 14:16 #4605756
-rw-r--r--  1 root  root    261 2004-11-20 14:16 #4605757
-rw-r--r--  1 root  root    198 2004-11-20 14:16 #4605758
-rw-r--r--  1 root  root    253 2004-11-20 14:16 #4605759
-rw-r--r--  1 root  root    191 2004-11-20 14:16 #4605760
-rw-r--r--  1 root  root    256 2004-11-20 14:16 #4605761
-rw-r--r--  1 root  root    193 2004-11-20 14:16 #4605762
-rw-r--r--  1 root  root    239 2004-11-20 14:16 #4605763
-rw-r--r--  1 root  root    189 2004-11-20 14:16 #4605764
-rw-r--r--  1 root  root    258 2004-11-20 14:16 #4605765
-rw-r--r--  1 root  root    186 2004-11-20 14:16 #4605766
-rw-r--r--  1 root  root    253 2004-11-20 14:16 #4605767
-rw-r--r--  1 root  root    185 2004-11-20 14:16 #4605768
-rw-r--r--  1 root  root    258 2004-11-20 14:16 #4605769
-rw-r--r--  1 root  root    173 2004-11-20 14:16 #4605770
-rw-r--r--  1 root  root    233 2004-11-20 14:16 #4605771
-rw-r--r--  1 root  root    254 2004-11-20 14:16 #4605772
-rw-r--r--  1 root  root    303 2004-11-20 14:16 #4605773
-rw-r--r--  1 root  root    244 2004-11-20 14:16 #4605774
-rw-r--r--  1 root  root    287 2004-11-20 14:16 #4605775
-rw-r--r--  1 root  root    267 2004-11-20 14:16 #4605776
-rw-r--r--  1 root  root    315 2004-11-20 14:16 #4605777
-rw-r--r--  1 root  root    172 2004-11-20 14:16 #4605778
-rw-r--r--  1 root  root    233 2004-11-20 14:16 #4605779
-rw-r--r--  1 root  root    258 2004-11-20 14:16 #4605780
-rw-r--r--  1 root  root    312 2004-11-20 14:16 #4605781
-rw-r--r--  1 root  root    263 2004-11-20 14:16 #4605782
-rw-r--r--  1 root  root    318 2004-11-20 14:16 #4605783
-rw-r--r--  1 root  root    242 2004-11-20 14:16 #4605784
-rw-r--r--  1 root  root    275 2004-11-20 14:16 #4605785
-rw-r--r--  1 root  root    248 2004-11-20 14:16 #4605851
-rw-r--r--  1 root  root    310 2004-11-20 14:16 #4605852
-rw-r--r--  1 root  root    221 2004-11-20 14:16 #4605853
-rw-r--r--  1 root  root    297 2004-11-20 14:16 #4605854
-rw-r--r--  1 root  root    285 2004-11-20 14:16 #4605855
-rw-r--r--  1 root  root    326 2004-11-20 14:16 #4605856
-rw-r--r--  1 root  root    264 2004-11-20 14:16 #4605857
-rw-r--r--  1 root  root    322 2004-11-20 14:16 #4605858
-rw-r--r--  1 root  root    219 2004-11-20 14:16 #4605859
-rw-r--r--  1 root  root    261 2004-11-20 14:16 #4605860
-rw-r--r--  1 root  root    251 2004-11-20 14:16 #4605861
-rw-r--r--  1 root  root    295 2004-11-20 14:16 #4605862
-rw-r--r--  1 root  root    229 2004-11-20 14:16 #4605863
-rw-r--r--  1 root  root    273 2004-11-20 14:16 #4605864
-rw-r--r--  1 root  root    242 2004-11-20 14:16 #4605865
-rw-r--r--  1 root  root    319 2004-11-20 14:16 #4605866
-rw-r--r--  1 root  root    245 2004-11-20 14:16 #4605867
-rw-r--r--  1 root  root    291 2004-11-20 14:16 #4605868
-rw-r--r--  1 root  root    164 2004-11-20 14:16 #4605869
-rw-r--r--  1 root  root    234 2004-11-20 14:16 #4605870
-rw-r--r--  1 root  root    236 2004-11-20 14:16 #4605871
-rw-r--r--  1 root  root    280 2004-11-20 14:16 #4605872
-rw-r--r--  1 root  root    236 2004-11-20 14:16 #4605873
-rw-r--r--  1 root  root    280 2004-11-20 14:16 #4605874
-rw-r--r--  1 root  root    228 2004-11-20 14:16 #4605875
-rw-r--r--  1 root  root    315 2004-11-20 14:16 #4605876
-rw-r--r--  1 root  root    261 2004-11-20 14:16 #4605877
-rw-r--r--  1 root  root    339 2004-11-20 14:16 #4605878
-rw-r--r--  1 root  root   1398 2004-11-24 10:55 #4784752
-rw-r--r--  1 root  root    435 2007-10-09 09:05 #4784753
-rw-r--r--  1 root  root  11567 2007-10-09 09:05 #4784754
-rw-r--r--  1 root  root    793 2007-10-09 09:05 #4784755
-rw-r--r--  1 root  root   1004 2007-09-25 22:19 #4899361
-rw-r--r--  1 root  root    453 2007-09-25 22:19 #4899362
-rw-r--r--  1 root  root    125 2007-09-25 22:19 #4899363
-rw-r--r--  1 root  root     85 2007-09-25 22:19 #4899364
-rw-r--r--  1 root  root    165 2007-09-25 22:19 #4899365
-rw-r--r--  1 root  root    181 2007-09-25 22:19 #4899366
-rw-r--r--  1 root  root    193 2007-09-25 22:19 #4899367
-rw-r--r--  1 root  root    269 2007-09-25 22:19 #4899368
-rw-r--r--  1 root  root    465 2007-09-25 22:19 #4899369
-rw-r--r--  1 root  root    181 2007-09-25 22:19 #4899370
-rw-r--r--  1 root  root    217 2007-09-25 22:19 #4899371
-rw-r--r--  1 root  root    261 2007-09-25 22:19 #4899372
-rw-r--r--  1 root  root     93 2007-09-25 22:19 #4899373
-rw-r--r--  1 root  root    125 2007-09-25 22:19 #4899374
-rw-r--r--  1 root  root     65 2007-09-25 22:19 #4899375
-rw-r--r--  1 root  root    129 2007-09-25 22:19 #4899376
-rw-r--r--  1 root  root     77 2007-09-25 22:19 #4899377
-rw-r--r--  1 root  root    485 2007-09-25 22:19 #4899378
-rw-r--r--  1 root  root    125 2007-09-25 22:19 #4899379
-rw-r--r--  1 root  root    121 2007-09-25 22:19 #4899380
-rw-r--r--  1 root  root     77 2007-09-25 22:19 #4899381
-rw-r--r--  1 root  root    437 2007-09-25 22:19 #4899382
-rw-r--r--  1 root  root   1016 2007-09-25 22:19 #4899383
-rw-r--r--  1 root  root    976 2007-09-25 22:19 #4899384
-rw-r--r--  1 root  root    461 2007-09-25 22:19 #4899385
-rw-r--r--  1 root  root    437 2007-09-25 22:19 #4899386
-rw-r--r--  1 root  root    129 2007-09-25 22:19 #4899387
-rw-r--r--  1 root  root   1208 2007-09-25 22:19 #4899388
-rw-r--r--  1 root  root    101 2007-09-25 22:19 #4899389
-rw-r--r--  1 root  root     77 2007-09-25 22:19 #4899390
-rw-r--r--  1 root  root     97 2007-09-25 22:19 #4899391
-rw-r--r--  1 root  root     97 2007-09-25 22:19 #4899392
-rw-r--r--  1 root  root   1236 2007-09-25 22:19 #4899393
-rw-r--r--  1 root  root    201 2007-09-25 22:19 #4899394
-rw-r--r--  1 root  root     65 2007-09-25 22:19 #4899395
-rw-r--r--  1 root  root   1300 2007-09-25 22:19 #4899396
-rw-r--r--  1 root  root   1116 2007-09-25 22:19 #4899397
-rw-r--r--  1 root  root    617 2007-09-25 22:19 #4899398
-rw-r--r--  1 root  root     65 2007-09-25 22:19 #4899399
-rw-r--r--  1 root  root    453 2007-09-25 22:19 #4899400
-rw-r--r--  1 root  root    205 2007-09-25 22:19 #4899401
-rw-r--r--  1 root  root   1236 2007-09-25 22:19 #4899402
-rw-r--r--  1 root  root     97 2007-09-25 22:19 #4899403
-rw-r--r--  1 root  root     97 2007-09-25 22:19 #4899404
-rw-r--r--  1 root  root    261 2007-09-25 22:19 #4899405
-rw-r--r--  1 root  root    393 2007-09-25 22:19 #4899406
-rw-r--r--  1 root  root    133 2007-09-25 22:19 #4899407
-rw-r--r--  1 root  root    261 2007-09-25 22:19 #4899408
-rw-r--r--  1 root  root    381 2007-09-25 22:19 #4899409
-rw-r--r--  1 root  root     65 2007-09-25 22:19 #4899410
-rw-r--r--  1 root  root   1052 2007-09-25 22:19 #4899411
-rw-r--r--  1 root  root     97 2007-09-25 22:19 #4899412
-rw-r--r--  1 root  root     85 2007-09-25 22:19 #4899413
-rw-r--r--  1 root  root    385 2007-09-25 22:19 #4899414
-rw-r--r--  1 root  root   1044 2007-09-25 22:19 #4899415
-rw-r--r--  1 root  root   1040 2007-09-25 22:19 #4899416
-rw-r--r--  1 root  root   1048 2007-09-25 22:19 #4899417
-rw-r--r--  1 root  root   1040 2007-09-25 22:19 #4899418
-rw-r--r--  1 root  root   1040 2007-09-25 22:19 #4899419
-rw-r--r--  1 root  root   1040 2007-09-25 22:19 #4899420
-rw-r--r--  1 root  root   1040 2007-09-25 22:19 #4899421
-rw-r--r--  1 root  root   1040 2007-09-25 22:19 #4899422
-rw-r--r--  1 root  root   1040 2007-09-25 22:19 #4899423
-rw-r--r--  1 root  root   1044 2007-09-25 22:19 #4899424
-rw-r--r--  1 root  root   1040 2007-09-25 22:19 #4899425
-rw-r--r--  1 root  root   4821 2007-09-25 22:19 #4899426
-rw-r--r--  1 root  root   4733 2007-09-25 22:19 #4899427
-rw-r--r--  1 root  root   4765 2007-09-25 22:19 #4899428


That little python game isn't a problem - I can download it again - but my concern is that those weren't the only files that were lost.  Several were from /usr/share/gnome/help/about-ubuntu, /usr/share/gnome/help/evince/, usr/share/doc/libjscj-java (and a bunch of other java files).  I took photos of a fair number of screens, although not all..

---

### Post by Herman on 2008-03-01
:cry: Oh, ouch! That doesn't look good I'm afraid. It will be a lot of work to restore all those and your system might not work the way it should.
> I've been through a hard drive crash in the past, so I'm pretty good about keeping backups, although I'll probably burn a new backup of the data partition for safety.That's good.>  I can get around pretty well in Ubuntu, but I haven't done a lot of command-line or disk management. It would be nice to get the system back without reinstalling, but if I need to wipe the partition and start over, I can deal with it.To be honest, it will be quicker for you to re-install, that only takes about half an hour. 
You should make a backup of your all software packages in /var/cache/apt/archives and copy all the packages you want before you delete your old operating system and copy all those packages to some media or another partition. Then when you have your new operating system, paste all the software packages into your new empty /var/cache/apt/archives again.
Then when you're ready to install your old software, just re-install it as normal, (I use the apt-get command but you may use Synaptic), you will be able to install the packages again but it will be a lot quicker because you won't need to download most of them, they'll already be there waiting.

I imagine you already know how to backup and restore most of your other files, like email and firefox bookmarks and that sort of thing. [Back Up and Restore]("http://users.bigpond.net.au/hermanzone/p13.htm").

Just in case you're interested, here is my collection of links about how to rescue file from the lost+found, [Recovering files from lost+found]("http://users.bigpond.net.au/hermanzone/p10.htm#Recovering_files_from_lostfound"). You might not need to do that unless you have files that are important that you forgot to back up or haven't had time to yet. It is possible to recover files from the lost+found, but it will be some work. It might be fun to try it and see how you go. You might learn how to help someone else in that situation who didn't make a backup and who has important (maybe valuable)  files to recover. 

Regards, Herman :)

---

### Post by twin_57103 on 2008-03-01
Herman - thanks again.  I use exclusively web mail, so that isn't a problem.  I've got DSL, so downloading isn't a big deal either.  I'll probably look at the lost & found if only for my own education - I'm a Windows whiz and decent with hardware, but I'm still a newbie when it comes to Linux (and trying to learn!).

I'm going to pick up some dual-layer DVD's later today so I can do a proper backup of the data partition - the only DVD's I had were very old and failed to burn with Nero - probably too old for the burner.  I had the hard drive of a brand new computer fail and at that time, I didn't recognize the symptoms, and I lost a lot of data.

What, if anything, should I do to prepare for reinstalling?  Can I just use the Ubuntu installer or should I download a disk for gparted (I believe it works that way).  Additionally, I'm wondering if I ought to use Mythbuntu to make the TV card setup easier.  I didn't care for what it did to my system when I had it on there before, but I would like to be able to use the card from Linux as well as Windows.  I'll probably post that as a separate question on the multimedia forums.

One more question - any idea what might have caused this?  I don't remember any hard restarts and I'm a little astounded that the operating system that is supposedly so stable has crashed so impressively.

Thanks again for all the help!!!!!

---

### Post by Herman on 2008-03-01
> I'll probably look at the lost & found if only for my own education - I'm a Windows whiz and decent with hardware, but I'm still a newbie when it comes to Linux (and trying to learn!). It would be a good opportunity to learn something. I'm curious about how to restore data from the lost+found myself. It was difficult to find good information on it,I spent some time goggling and reading to find those few links on the subject.
> I'm going to pick up some dual-layer DVD's later today so I can do a proper backup of the data partition - the only DVD's I had were very old and failed to burn with Nero - probably too old for the burner. I had the hard drive of a brand new computer fail and at that time, I didn't recognize the symptoms, and I lost a lot of data.You'll thank yourself years from now when you have a little spare time to fill and you go browsing through your backup DVDs and find old photos or documents. I enjoy doing that once in a while, and I sometimes find gems of forgotten information or work that I'm happy to get back again. CDs and DVDs are really the best way to keep data stored in the long run. :)
> any idea what might have caused this? I don't remember any hard restarts and I'm a little astounded that the operating system that is supposedly so stable has crashed so impressively.
 I have no idea really, fortunately for all of us, this type of thing seems to be a rare occurrence, if it happened more often it would be easier to find good information all about how to recover data from the lost+found.
There is a list of things that can cause file system problems, hard shut-downs would be top of the list, followed by faulty power supply units, bad blocks in the hard disk, faulty IDE cabling, kernel bugs, ...

You could try running some tests on various hardware items and then monitoring them for a while. Maybe it's just a freak occurrence and after you re-install you'll never have another problem again ever. (Hopefully). If there is some problem you can do something about it would be nice to be able to find it promptly and fix it. [Check On Your Hard Disks With Smartmontools]("http://users.bigpond.net.au/hermanzone/p20.html#Check_On_Your_Hard_Disks_With"). [System Health Check]("http://www.users.bigpond.net.au/hermanzone/p1.htm#System_Health_Check").  [memtest86+]("http://users.bigpond.net.au/hermanzone/p15.htm#Memtest86"). [                        Running a check for bad blocks on your hard disk]("http://users.bigpond.net.au/hermanzone/p10.htm#bad_blocks_check").
> What, if anything, should I do to prepare for reinstalling? Can I just use the Ubuntu installer or should I download a disk for gparted (I believe it works that way). Additionally, I'm wondering if I ought to use Mythbuntu to make the TV card setup easier. I didn't care for what it did to my system when I had it on there before, but I would like to be able to use the card from Linux as well as Windows. I'll probably post that as a separate question on the multimedia forums.I don't know much about Mythbuntu or TV cards. 
You should be able to use the installer to just format the Ubuntu partition again with a new file system. If you want you can use Gnome Partition Editor (GParted).
After you re-install just try running some extra file sysem checks from the LiveCD to monitor the situation and try to catcfh problems while they are still small, and to try to see what's going on and see if you can find out if the problem is related to anything.
The command 'sudo e2fsck -C0 -p -f -v /dev/hda2' should provide some useful feedback. If you try running it frequently you may notice for example that some small file system problem was repaired and possibly you could try to link it to some event or  condition.
As time goes on and no  more problems seem to be happening you can relax more and more.
It's still always wise to make regular backups though. Anything can happen to anyone's hard disk or the file systems in it at any time.

Regards, Herman :)

---

### Post by twin_57103 on 2008-03-01
The problem is the hard drive.  I'm sitting here thinking "this isn't happening - not again."  Of all the things I didn't want to find, this was pretty high on the list.  I've had data access errors while trying to back up files on the NTFS partition (from Windows).

This is the second nearly-new SATA drive I've had fail within the last 4 years (other one was only a month old).  There's nothing irreplaceable on the drive, but it's definitely something I didn't need right now.  At least last time I learned the lesson about backing up my data.

Hopefully I can find the paperwork and get warranty service on it (drive is only about a year old).  Thanks for the help getting it partially functional - I'll try to update when I know more.

---

### Post by Herman on 2008-03-02
I'm sorry to read that your hard drive seems to be having such bad problems. 
Really it's amazing the job they are able to do and how inexpensive they are for all the technology and precision they involve.

I hope you can get warranty on it. Did you take a look at the hard dirve with smartmontools? If the hard drive supports S.M.A.R.T. you can install smartmontools in Ubuntu and possibly learn a little about went wrong.
```
apt-get install smartmontools
``` You can do that in the Ubuntu Live CD too, but the installed software will be lost on reboot, of course.
Knoppix and System Rescue CD have smartmontools in them already.
It might be interesting and not only that, it might even improve your chances of a successful warranty claim if you have your information together.

Regards, Herman :)

---

### Post by twin_57103 on 2008-03-02
Herman - thanks for the ideas.  I'm still working on data recovery.  I've copied off most of my data partition to the primary hard drive and I'm burning it to DVDs before I go any further.  The corruption there was pretty minor, nothing that can't be replaced or that I didn't have already backed up.

I have the manufacturer's "Data Lifeguard Tools" disk and I also have a copy of Knoppix.  I still can't install anything on my Ubuntu installation, so it will be a live CD either way.  It's a Western Digital that was purchased last June - I stand a pretty good chance of warranty service since it's only about 6 months old.  I'll see what I can do once I get all the data onto DVDs.

---

### Post by twin_57103 on 2008-03-03
OK, I'm fumbling my way through smartmontools.  I've tried 

```
ubuntu@ubuntu:~$ sudo smartctl sdb2
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Smartctl open device: sdb2 failed: No such file or directory

```

And...
```
ubuntu@ubuntu:~$ sudo smartctl -l selftest /dev/sdb
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)
_of_first_error
# 1  Short offline       Completed without error       00%      5969       
# 2  Short captive       Completed without error       00%         0       

```

```
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sdb
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar SE (Serial ATA) family
Device Model:     WDC WD2000JS-22MHB0
Serial Number:    WD-WCANK8929481
Firmware Version: 02.01C03
User Capacity:    200,049,647,616 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Mar  4 00:12:49 2008 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 (6780) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  80) minutes.
Conveyance self-test routine
recommended polling time:        (   6) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       651
  3 Spin_Up_Time            0x0003   185   181   021    Pre-fail  Always       -       5750
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2633
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       5989
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   253   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       66
190 Temperature_Celsius     0x0022   041   025   045    Old_age   Always   FAILING_NOW 59
194 Temperature_Celsius     0x0022   091   075   000    Old_age   Always       -       59
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   198   000    Old_age   Always       -       14
198 Offline_Uncorrectable   0x0010   200   198   000    Old_age   Offline      -       14
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       3

SMART Error Log Version: 1
ATA Error Count: 1814 (device log contains only the most recent five errors)
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 1814 occurred at disk power-on lifetime: 5979 hours (249 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 47 0d 5f e0  Error: UNC 8 sectors at LBA = 0x005f0d47 = 6229319

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 47 0d 5f 00 00   1d+08:50:31.795  READ DMA EXT
  25 00 08 3f 0d 5f 00 00   1d+08:50:31.795  READ DMA EXT
  25 00 08 37 0d 5f 00 00   1d+08:50:31.795  READ DMA EXT
  25 00 08 2f 0d 5f 00 00   1d+08:50:31.795  READ DMA EXT
  25 00 08 27 0d 5f 00 00   1d+08:50:31.795  READ DMA EXT

Error 1813 occurred at disk power-on lifetime: 5979 hours (249 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 80 cf 0c 5f e0  Error: UNC 128 sectors at LBA = 0x005f0ccf = 6229199

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 80 cf 0c 5f 00 00   1d+08:50:29.902  READ DMA EXT
  25 00 80 4f 0c 5f 00 00   1d+08:50:29.901  READ DMA EXT
  25 00 80 cf 0b 5f 00 00   1d+08:50:29.900  READ DMA EXT
  25 00 80 4f 0b 5f 00 00   1d+08:50:29.899  READ DMA EXT
  25 00 80 cf 0a 5f 00 00   1d+08:50:29.898  READ DMA EXT

Error 1812 occurred at disk power-on lifetime: 5979 hours (249 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 47 a2 5e e0  Error: UNC 8 sectors at LBA = 0x005ea247 = 6201927

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 47 a2 5e 00 00   1d+08:50:27.511  READ DMA EXT
  25 00 08 3f a2 5e 00 00   1d+08:50:27.511  READ DMA EXT
  25 00 08 37 a2 5e 00 00   1d+08:50:27.511  READ DMA EXT
  25 00 08 2f a2 5e 00 00   1d+08:50:27.511  READ DMA EXT
  25 00 08 27 a2 5e 00 00   1d+08:50:27.511  READ DMA EXT

Error 1811 occurred at disk power-on lifetime: 5979 hours (249 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 80 07 a2 5e e0  Error: UNC 128 sectors at LBA = 0x005ea207 = 6201863

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 80 07 a2 5e 00 00   1d+08:50:25.689  READ DMA EXT
  25 00 80 87 a1 5e 00 00   1d+08:50:25.688  READ DMA EXT
  25 00 80 07 a1 5e 00 00   1d+08:50:25.687  READ DMA EXT
  25 00 80 87 a0 5e 00 00   1d+08:50:25.685  READ DMA EXT
  25 00 80 07 a0 5e 00 00   1d+08:50:25.684  READ DMA EXT

Error 1810 occurred at disk power-on lifetime: 5979 hours (249 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 7f 19 5e e0  Error: UNC 8 sectors at LBA = 0x005e197f = 6166911

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 7f 19 5e 00 00   1d+08:50:23.457  READ DMA EXT
  25 00 08 77 19 5e 00 00   1d+08:50:23.457  READ DMA EXT
  25 00 08 6f 19 5e 00 00   1d+08:50:23.457  READ DMA EXT
  25 00 08 67 19 5e 00 00   1d+08:50:23.456  READ DMA EXT
  25 00 08 5f 19 5e 00 00   1d+08:50:23.456  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      5969         -
# 2  Short captive       Completed without error       00%         0         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


```

Any help you can give me interpreting this would be appreciated.  It looks like I've got temperature issues, in which case I don't have much of a chance of warranty replacement :(

My Ubuntu installation has gotten so bad that I can't even access the terminal.:(  If I want Linux, it has to be off a disk

Thanks again for all the help!

---

### Post by twin_57103 on 2008-03-03
I attached another scan that  I got from a Windows program (SpeedFan).

Here's some output from an online counterpart to SpeedFan ([www.hddstatus.com]("www.hddstatus.com")):
> Almost every EIDE or SATA hard disk includes S.M.A.R.T. data. That information is collected by the drive itself and contains data that the manufacturer considered relevant to check reliability. The data is made up of several attributes that have a current value, a worst one, a threshold, some raw data, and some flags. Basically, when any attribute's current value is below its threshold, the hard disk is considered unreliable and likely to fail. By using several techniques, this report tries to give a wider range of info, basing its analysis on advanced comparisons with normal values based on real hard disks and on expert-like checks. The final results are not to be taken as an absolute truth, but they are a very good approach to what a professional would say about your hard disk status.
Your hard disk is a WDC WD2000JS-22MHB0 with firmware 02.01C03.
The average temperature for this hard disk is 46C (MIN=29C MAX=66C) and yours is 59C.
Your hard disk's S.M.A.R.T. attributes are now being analyzed and a full report about the reliability, health and status of your hard disk is generated:
Your hard disk is not below any attribute threshold. This is good.
Your hard disk was never below any attribute threshold. This is good.
Your hard disk is now being compared to real data used to define normal values for your specific hard disk model. This way, the analysis can automatically use proper operating ranges. The images give you an idea of how each attribute is within such range. Current and raw values are shown for easier reference for experienced users. There are 1742 hard disk models in the current archive.

	  	Attribute	 		Current	 	Raw	 	Overall
10		Raw Read Error Rate		200		651 		Very good
0		Spin Up Time			185		5750 		Watch
Warning: Spin Up Time is below the average limits (187-253).
0		Start/Stop Count		98		2633 		Watch
Warning: Start/Stop Count is below the average limits (99-100).
10		Reallocated Sector Count	200		 0 		Very good
10		Seek Error Rate			200		0 		Very good
5		Power On Hours Count		92		5990 		Good
10		Spin Retry Count		 100		0 		Very good
10		Calibration Retry Count		100		0 		Very good
10		Power Cycle Count		100		66 		Very good
3		Unknown attribute 190		  41		59 		Normal
10		Reallocated Event Count		200		0 		Very good
10		Current Pending Sector		 200		14 		Very good
10		Offline Uncorrectable Sector Count  200		14 		Very good
10		Ultra DMA CRC Error Rate	200		0 		Very good
10		Write Error Rate		200		3 		Very good

NOTE: not all warnings are reflected on fitness and performance overall values as relevancy is based upon the settings from the hard disk manufacturer who is the best entity deputed to define such relationships.

NOTE : your hard disk Spin Up Time attribute current value (185) is below the normal range (187 - 253) reported for your specific hard disk model. Recently purchased hard disks that were not yet power cycled many times might experience a low value here and it wouldn't be a problem as, after some time, the value should raise towards better ones. If, on the other side, your hard disk is not that new and it was powered on several times this might mean its mechanic is getting old. Usually this attribute is not so relevant by itself, but it might reinforce some other deduction when looking at the global picture.

NOTE : your hard disk has 14 pending sectors. Those are sectors that couldn't be properly read and that the hard disk logic is waiting for a write operation to try to remap to a spare sector (if available). According to the Reallocated Sector Count attribute, your hard disk seems to have available spare sectors. A simple disk surface scan won't be enough to force the remap operation. You need a read/write surface scan to remap the sector. The best option should be a tool that knows about what should be read from that sector so that it has some option to apply the best fix to the missing data.

NOTE : your hard disk has 14 offline uncorrectable sectors. Those are sectors that an offline scanning found as unreadable. Offline scanning is a process that can be automatically started by the hard disk logic when a long enough idle period is detected or that can be forced by some tool. Those unreadable sectors are identified and the hard disk logic is waiting for a write command that will overwrite them to try to remap them to spare sectors (if available). According to the Reallocated Sector Count attribute, your hard disk seems to have available spare sectors. A simple disk surface scan won't be enough to force the remap operation. You need a read/write surface scan to remap the sector. The best option should be a tool that knows about what should be read from that sector so that it has some option to apply the best fix to the missing data.

The overall fitness for this drive is 89%.
The overall performance for this drive is 100%.


---

### Post by Herman on 2008-03-06
:) Hello twin_57103,
Sorry for keeping you waiting so long.
Thanks for posting your smartmontools output, that looks really interesting.

It looks to me as if there's not very much wrong with your hard drive except that it's getting a little too hot.

If you clicked on the link to my [Check On Your Hard Disks With Smartmontools]("http://users.bigpond.net.au/hermanzone/p20.html#Check_On_Your_Hard_Disks_With"). article you would have found the best explanation I could come up with about how to interpret the output from smartmontools and other links that lead to the best sites I could find for explaining what the output means.

The heat in a hard drive (and in many other things) comes mainly from the bearing, and a failing bearing will generate more heat because of the extra friction than a bearing that's healthy.
So which came first I wonder, the chicken or the egg?
If you mounted your hard drive in the normal way in your Desktop's case with the normal amount of air circulation it should live for a normal age for a hard drive. It seems logical to me to think there might be a problem developing in the bearing, and that's probably what's generating the extra heat.
The spin-up time isn't too bad but it's a little on the slow side too.
I'm not really a hard drive expert, so take my opinions with a grain of salt. I'm just someone else who's also learning stuff. 
I have some experience with truck wheel bearings (tractor-trailers and road trains). :lolflag:

If you think it could be the other way around, and the excess heat is coming from somewhere else, just try to think of ways you can improve the cooling air circulation past your hard drive and see if the problem goes away.

The output from smartmontools is a good place to start but it doesn't tell us exact details. It does give us a good indication to start from. 
The best people to talk to now that you have somewhere to start from would be the experts at Western Digital.

I went to Western Digital's website and read the [WD Promise]("http://www.wdc.com/en/products/wdpromise.asp"). It certainly looks like you have a good quality hard drive, they really are concerned about quality control by the looks of things, and care about their customers.

Then I found Service and Support which asks you to verify the status of the drive by running their[ Data Lifeguard Diagnostics]("http://support.wdc.com/download/"). Probably that will read the same data as you read with smartmontools but it will be interpreted by Western Digital's own software in a more specialized way.

Then you would follow whatever procedures they have in place to determine if you have a warranty claim or not.
It would still be worth a try, Western Digital is a good brand, actually, after having just had a look around and shining a light into some of my computer cases, all my new hard drives and a few older ones are made by Western Digital too. I'll be bookmarking Western Digital's site now myself and reading through it to see what more I can learn there.

All the best, and thanks for keeping in touch, it's interesting,

Regards, Herman :)

---

### Post by twin_57103 on 2008-03-06
Hi Herman,
Glad to hear from you.  I've been thinking I should get in touch with WD, just hadn't gotten around to it.  With Windows running, it hasn't been as bad as if that had been my only operating system. 

Thanks for the link for more info on smartmontools.  I'll see what I can do with it.  I've got WD's data lifeguard tools installed.  It found some bad sectors, but that was about it.  Thanks too for the thoughts about hard drives in general - it's quite helpful.

I've only seen the temperature warning once - the one I posted.  The other scans I've done haven't turned that up.  I know my system is a running a little warm, but I didn't think it was enough to be concerned about.  I keep it in a cubby in my desk (which is intended for a computer), but it doesn't help airflow.

I'm going to see what I can do about working with WD, but I'm also working on (hopefully) replacing the computer.  It has been such a lemon (someone called it the lemon tree) and I think it's time.  I'm hoping to build a replacement, then scrap this one for parts.  I've already got friends calling dibs on parts!

I'll update this thread once I know more.  Thanks a million for all the help!

---

### Post by Herman on 2008-03-06
> Thanks a million for all the help!:) Okay,  I'm interested in this subject.  

I found out that if you paste the serial number of your WD hard disk without the 'WD' in front of it, eg: WCANK8929481 in  [Western Digital's Warranty check]("http://websupport.wdc.com/warranty/serialinput.asp?custtype=end&requesttype=warranty&lang=en") it turns out you are good 'till 04/03/2008, and it says you're still possibly covered. Since we're already past March the 4th, I guess maybe they mean the 3rd of April.

It could be that your hard drive is okay, but there's a chance that your hard drive bearing isn't getting air that's cool enough to carry away the normal bearing heat. 
I'm not sure because I don't know what your PC and cubby look like, but maybe try looking at the position of air intake vents in your computer case and the location of the power supply and case fans which would be exhausting the hot air out. Maybe you just need to cut a hole or two in your computer desk's cubby and/or make some kind of ducting to direct the hot air out and guide cool air into your PC case. Even an old plastic bag and some duct tape might enough to do the trick.

I found this while researching for my smartmotools article,
> **231. Drive Temperature**
Hard disk drive temperature. The raw value of this attribute shows built-in heat sensor registrations (in degrees centigrade).

Studies have shown that lowering disk temperatures by as little as 5°C significantly reduces failure rates, though this is less of an issue for the latest generation of fluid-drive
bearing drives. 
One of the simplest and least expensive steps you can take to ensure disk reliability is to add a cooling fan that blows cooling air directly onto or past the system's
disks.Here in the part of Australia where I live, temperatures outside can easily reach 46 or 47 degrees centigrade in summer but I try to keep my computer room cooler than that with air conditioning. 
I'm not always successful. My dog has learned how to open the door whenever she wants, (she likes the cool air too). It's kind of handy when I'm carrying something and have both hands full, she'll open the door for me on command. What I haven't managed to train her to do yet is close the door again, which is not so good if she opens it when I'm not there. :lolflag:

Regards, Herman :)

---

### Post by twin_57103 on 2008-03-07
Hi Herman,

The US convention would put that date as April 3, although I had hoped the warranty period would be longer - I hadn't done the warranty check, but I had been on their web site and seen 3 years.

I emailed WD asking about it last night.  I'm hoping for a reply sometime today.  I rent a basement and it's winter here (this is a cold climate, highs sub-zero Celsius all winter, can be as low as -20°C with lows even worse), so the environment tends to be pretty cool.  If necessary , I"ll move the computer out of the cubby before cutting holes in the desk.

Thanks again,
twin_57103

---

### Post by Herman on 2008-03-07
I have seven Western Digital hard drives, two are quite old ones, but five of them are fairly new. I completed the registration form at the WD website for my five newer drives, they're all still under warranty.
By default, the warranty starts from the date of manufacture, but when we register our hard drives, the warranty is measured from the purchase date. (If you still have the receipt to prove it). So you could be covered for a lot longer.

Regards, Herman :)

---

### Post by twin_57103 on 2008-03-11
I finally heard back from Western Digital (they promise 24-hour response time but it was 3-4 days).  There is a simple online option to update my warranty by scanning and uploading the original receipt.

I got some Windows and our-software-only snobbishness (we don't support *nix operating systems - I didn't ask you to-just your hard drive!).  In order to let their software see the entire drive, I installed a true[ ext2 driver for Windows]("http://www.fs-driver.org/") since it didn't seem like I'd get anywhere using a native linux utility.

I ran a few more scans last night and again found some bad sectors, but that was about it.  I'll email them again, hopefully this evening, and update once I hear back.

---

### Post by twin_57103 on 2008-03-20
Sorry I haven't updated in a while.  In the end, I decided I was having so much trouble with this entire computer that it is time for a new one.  I am splurging but I should have a much better computer for it.  Here's what I'm working on for a build:

Motherboard: ASUS M2N-SLI Deluxe
Processor: AMD Phenom quad-core (2.2 GHz)
Power Supply: 700W Coolmax Green Power
RAM: 4 Gb PC6400 (2x2 Gb; Super-Talent)
Drives: 2x320 Gb hard drives (Hitachi), 2 Lite-on Lightscribe DVD burners
Operating systems: Windows Vista Home Premium and Ubuntu

I haven't yet decided on a video card, but I'm leaning toward the NVIDIA GeForce 8600's.  I posted [an inquiry]("http://ubuntuforums.org/showthread.php?t=729590") about that choice on the hardware forums, but haven't yet heard back.

I'm still going to try to get the failing drive replaced on warranty, but I am traveling this week and didn't want to deal with it until I get back.  When I updated the warranty, I only got a year's warranty (I'd expected three), but it will be enough anyway.  Notice that I avoided WD for the drives in the new build :)

---

### Post by Herman on 2008-03-20
Wow! NICE hardware! :)  :)  :)

Thanks for the update, and enjoy your journey, where-ever you go.

I'll keep in mind the at least some of the staff at Western Digital don't seem Linux friendly. There are a lot of companies that are still like that, it's cheaper for a company to train staff in only one operating system. I am discovering that actually, some staff are Linux friendly themselves when they aren't on company time. That will change as Windows dies out and Linux takes over the majority of the PC market. It is surely happening as we speak, although it will take time.

Did you know there is a nice Ubuntu Linux Hardware Compatibility Site by our fellow Ubuntu user samb0057?
Here is the link, [UbuntuHCL.org]("http://www.ubuntuhcl.org/") 
If Ubuntu users will join up to UbuntuHCL, we'll be able to help each other make the right hardware choices.

Regards, Herman :)

---

### Post by twin_57103 on 2008-03-20
Herman,

I think the chief danger when putting together the new machine will be drool...the friend who's helping me with it is pretty jealous.  It's more computer than I need, but I want this one to last longer than the last one (the one that is failing is less than 4 years old).

I got an automated feedback survey from WD, which I used as an opportunity to make my case on the Linux/ext3 issue.  I didn't try particularly hard with the email support.  They were basically pasting in a few links, and it sounds like I should be able to send it back for replacement.

I'll definitely check the hardware compatibility link.  I still need a video card for the new machine - it's the last choice I need to make.  I was grateful for some very knowledgeable advice from the staff at a local computer store (one of the few *true *computer stores left).

Thanks again for all the help - I'll try to update once I get the new machine set up and once I know how the warranty return comes out for the old hard drive.
twin_57103

---

### Post by Alex_Perry on 2008-03-24
I just wanted to add something to this thread. After seeing a few other related threads, I thought it would be wise to add my experience in case this is not hardware related, but a software bug that should be corrected.

I find it interesting that this thread would come up at around the same time the issue happened to me. The computer froze while my wife was using it, and upon rebooting it, /home/alex was gone, with all the file contents moved to /home/lost+found. All the files seem to be intact, albeit most files and directories renamed to the number of the corresponding inode it was stored in. This occurred on an 80gb Seagate Barracuda, one of two installed. One holds /home/, the other contains everything else.

I have no intention of repairing the filesystem since I have no idea what happened, and I'll be using this as an opportunity to upgrade as well. At first, I thought it was a hardware failure, however seeing this occur to others in a similar fashion and around the same time, it makes me wonder. I have not run smartmontools since I'll be replacing the drive with a 320gb Western Digital (5-yr warranty) shortly.

I have since burned all of the contents of /home/lost+found to DVD (roughly 30gb). None of the files seem to be corrupted, but this assumption is based only on selecting random files and verifying they were okay before burning them.

All of this aside, the system can still boot up fine and run under root, as thats how in posting this now. I'm only using this as a solution until my next day off work when I can purchase the new drive.

The other thread that caught my interest: [http://ubuntuforums.org/showthread.php?t=728361&highlight=lost+found+fsck](http://ubuntuforums.org/showthread.php?t=728361&highlight=lost+found+fsck)

---

### Post by Herman on 2008-03-24
:) Hello Alex_Perry,
Thanks for contributing your opinion. :)
From your story there is no reason to think that yours is a hardware failure, but a file system failure.
I don't know why computers freeze up, maybe there are several different reasons or causes for that happening.
There are different kinds of freeze-ups too. Sometimes the CPU is just busy, and things will return to normal if we give it a few minutes.
Other times the desktop seems frozen, or we loose the use of the mouse or keyboard or sometimes both.
You're right, that's a software issue that should be fixed, most often it has something to do with hardware support ('drivers').
Sometimes it's possible to get a mouse or a keyboard working again by unplugging it, them plugging it back in again. Other times, we need to reboot somehow.
Rebooting can be a problem.

Since hard discs are slow, and the rest of the computer is fast, Linux doesn't write to the hard disk continuously, but in bursts, storing information in a memory cache so the rest of the computer can keep going while it's waiting on the hard disk to keep up. Sometimes the information can be changed before it even gets to the hard disk.
If the hard disk happens to be somewhere in the middle of something when the  power is cut somehow, like if big main switch is pushed, the file system is in disarray and doesn't have time to finish what it's doing, (Trying to put all the files in thier proper places and record where they went).
That's the main reason for most file system failures.
I'm not sure if I described it exactly right, but something like that anyway.

When your computer freezes when you're running Linux, there are quite a few things you can do if your operating system freezes up  to either get things back to normal or reboot gently and aviod file system damage, I made a list of all the ways I can think of so far, here in this link, [Proper techniques (in the event of a frozen system ) to prevent filesystem damage]("http://users.bigpond.net.au/hermanzone/p10.htm#to_prevent_filesystem_damage")

Regards, Herman :)

---

### Post by twin_57103 on 2008-03-24
Alex,

Thanks for the thoughts.  I've gone at this from multiple angles and I am having continual errors on boots - I'm afraid to reboot.  The Windows drive doesn't seem to be affected, but I am even getting errors on Windows boots, probably from the data partition.

That old Dell was a lemon from day one and I didn't want to deal with it anymore.  As you've seen earlier in the thread, I used this as an excuse to replace the entire system.  I've gotten the new one assembled and will be installing the operating systems over the next few days.  We're going to cannibalize the old one for parts for at least 5 other computers :)  I'm hoping to get the 200 Gb drive replaced on warranty and convert it to an external drive, mostly for backup purposes (the new system has eSATA).

Here's a question for anyone reading:
What are your thoughts about how to set up the hard drives?  My thought had been to put Windows on one drive and partition the other for Ubuntu and an NTFS data partition.  I posted that in the installation forums and they recommended putting both operating systems on one drive and using the other solely as a data drive. Right now, the reason my old system is still operational is because Windows *wasn't* on the drive that failed.  What are your thoughts about this approach?

---

### Post by Alex_Perry on 2008-03-25
Herman,

Thank you for that! I do understand the basic principles of how everything works, however I though it was weird that absolutely every file under /home/alex was dumped into lost+found. I'm talking gigs of music and family photos, files that weren't even being accessed. With that being the case, in addition to the reading I have done, that's why I'm now leaning towards the filesystem going bad and not a hardware failure. 

That being said, what would cause this? It seems that in the past few weeks, I am not the only one who had this happen. A quick forum search led me to several recent threads describing the exact same thing occur to other users. It is/was an ext3 partition.

I should have included this originally, I did a few of those tweaks in the 'improve ext3 performance' in the tips section of the forum such as dir_index, however that was a few years ago (This drive hasn't been repartitioned/formatted in two years, maybe more).

No matter what happened, I'm making this an opportunity make a few changes. I'm going to install a single 320gb drive instead of the current dual 80gb setup I have now, and make the /home partition take up the majority. I'm also considering trying out openSuse as there have been numerous quirks come up over the years I have been using Kubuntu and want to try something new. Still deciding on that, though. However, I digress. I don't want to change the topic here.

---

### Post by twin_57103 on 2008-03-29
Here's another update...I'm still using both computers, so I haven't sent the hard drive back.  I installed Vista with [a few minor glitches]("http://ubuntuforums.org/search.php?searchid=38555920"), but I've been completely unable to install Ubuntu.  It seems like the computer is too new for Linux!  I've [posted this separately]("http://ubuntuforums.org/showthread.php?p=4611695#post4611695"), hoping for some assistance.  I may need to wait for 8.04 (the beta live CD will at least load).  I'll update once I know more; hopefully I can do something about the bad hard drive soon...

---

### Post by twin_57103 on 2008-04-06
Another update...I got the hard drive in the mail to WD.  I will update once I know what comes of it and whether they will replace the drive.  I installed 8.04 beta on my new machine because none of the stable versions would install, even using the alternate CD.

So far, the only software-related trouble I've had was having to reinstall the proprietary video driver after an update.  I am having consistent sleep/resume problems (fans restart, but OS does not resume, keyboard and mouse are unresponsive) that occur in both Linux and Windows, still occurring after installing Vista SP1 and updating the BIOS.  I am still looking for options, as I don't want to have to shut down the computer every time I want to step away, but I also don't want to leave everything running and sucking energy constantly.

I also found out that Super Grub is a useful tool for undoing a dual-boot - the drive that failed on my old machine was where Grub was located, so I had to restore the Windows MBR in order to be able to boot the computer without that hard drive (the data on it was toast, anyway).  Other than a rather juvenile/unprofessional text sad face over restoring Windows, it was very easy and quick (small download, pretty straightforward).

I'll update once I hear back about the replacement!

---

### Post by twin_57103 on 2008-04-29
Here's a conclusion for this saga: I got the drive replaced on warranty.  Since I've already junked the computer it came from, I've gotten an external enclosure for it and plan on using it as a backup drive (ironic, isn't it?).  I didn't get any technical information back from WD - the only thing that came with the replacement drive was the packing slip.

I'll probably avoid Western Digital hard drives in the future as they seem to ignore non-Windows operating systems (I've looked at their drives in stores and they give system requirements in terms of Windows only).  At least I got an extra hard drive out of the mess!

Enduring computer lessons from this mess:
   1: Hard drive crashes happen, so be sure to back up your data!  I've had two bad crashes, and both drives were less than a year old.
  2: don't ignore funky behavior, especially on a Linux system; it may be a sign of something very bad.
  3: SMART hard drive monitoring is a very good thing (and built into almost all modern hard drives).

Thanks to everyone who helped with this, especially Herman, who was a lifesaver!

---

