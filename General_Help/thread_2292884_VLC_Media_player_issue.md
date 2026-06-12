---
title: "VLC Media player issue"
date: 2015-08-31
forum: General Help
---

### Post by pancho5 on 2015-08-31
Hello!

I'm sort of a novice, but I am willing to learn more.  Okay, here is the deal.  I have a HP Laptop with Ubuntu 14.04 LTS, and VLC media player 2.1.6  installed on it that works fine.  I recently acquired a Samsung laptop, and installed VLC media player with the same OS and it doesn't work (see attachment).  What do I have to do, and, what log file should I look at that will help me resolve the problem?

Thanks in advance!

---

### Post by monkeybrain20122 on 2015-08-31
Did you install libdvdcss2?

```
sudo apt-get install libdvdread
sudo /usr/share/doc/libdvdread4/install-css.h
```

If that still doesn't work, it could be your DVD or your DVD drive

---

### Post by mc4man on 2015-08-31
In addition to above or if above doesn't fix - 
Run - 
```
sudo lshw -c disk
```
In the  *-cdrom section find the vendor. If it is **MATSHITA **then note - 
1. The dvd drive must be set to a region before it will allow access to commercial dvd's
2. The drive will only allow access to commercial dvd's  when the drive's region setting matches the dvd's region


To check if a region is set - 
```
sudo apt-get install regionset
```
Put a cd or dvd in the drive, once the drive settles - 
```
regionset
```

A drive with no region set will report this, a user is allowed 5 sets before the drive locks at the 5th set  - 
user controlled changes resets available: 5

If it's less than 5 then answer n (no) & post the regionset results

---

### Post by pancho5 on 2015-09-01
Still not working, but I provided screen dumps of su commands.  Can't make heads or tails out of it...



> **mc4man said:**
> In addition to above or if above doesn't fix - 
Run - 
```
sudo lshw -c disk
```
In the  *-cdrom section find the vendor. If it is **MATSHITA **then note - 
1. The dvd drive must be set to a region before it will allow access to commercial dvd's
2. The drive will only allow access to commercial dvd's  when the drive's region setting matches the dvd's region


To check if a region is set - 
```
sudo apt-get install regionset
```
Put a cd or dvd in the drive, once the drive settles - 
```
regionset
```

A drive with no region set will report this, a user is allowed 5 sets before the drive locks at the 5th set  - 
user controlled changes resets available: 5

If it's less than 5 then answer n (no) & post the regionset results

---

### Post by monkeybrain20122 on 2015-09-01
What if you open vlc, then from menu go to Media > Open Disc > Disc and in the box Disc device change thr entry from /dev/sr0 to /dev/dvd? You can choose from a menu by clicking the inverted triangle in the box's right border.

P.S. You need to put a disc in the dvd drive first to use regionset. But let's try something else first. You shouldn't need to set region normally (unless you have Matshita drive)

---

### Post by pancho5 on 2015-09-01
Same problem....see screen dumps!

[QUOTE=monkeybrain20122;13348462]What if you open vlc, then from menu go to Media > Open Disc > Disc and in the box Disc device change thr entry from /dev/sr0 to /dev/dvd? You can choose from a menu by clicking the inverted triangle in the box's right border.

P.S. You need to put a disc in the dvd drive first to use regionset. But let's try something else first. You shouldn't need to set region normally (unless you have Matshita drive)[/QU

---

### Post by QDR06VV9 on 2015-09-01
Have you tried with another DVD(Disk)
I have seen a few of those drives lose their lasers(Ability to Read)
Just a thought. Just a test I use to see if the optical drive works pull the one working out and swap to the non working lappy.
Kind Regards

---

### Post by pancho5 on 2015-09-01
Same problem....BTW, this Samsung laptop was given to me from my daughter while she was visiting us from LA, and before she left it had Windows 7 on it and she was watching DVD's while she was home so I know the CD/DVD player works.


> **runrickus said:**
> Have you tried with another DVD(Disk)
I have seen a few of those drives lose their lasers(Ability to Read)
Just a thought. Just a test I use to see if the optical drive works pull the one working out and swap to the non working lappy.
Kind Regards

---

### Post by QDR06VV9 on 2015-09-01
Ok what is the output of this in terminal

```
sudo apt-get install lame twolame ubuntu-restricted-extras libdvdread4
```

And this 
```
apt-cache policy libdvdread4
```

---

### Post by pancho5 on 2015-09-01
This is what shows up....


> **runrickus said:**
> Ok what is the output of this in terminal

```
sudo apt-get install lame twolame ubuntu-restricted-extras libdvdread4
```

And this 
```
apt-cache policy libdvdread4
```

---

### Post by QDR06VV9 on 2015-09-01
You can press the Tab key and it will hi-light the <ok> press enter on the keyboard and repeat if necessary, But your are agreeing to their licencing.
Tip: To copy from the terminal you can select the text with your mouse and right click <copy>
Then paste with code tags the output here in your thread.
Regards

---

### Post by pancho5 on 2015-09-01
Okay...I did that, but why are we doing this?  I tried to read another DVD and I still have the same problem.  ](*,)

> **runrickus said:**
> You can press the Tab key and it will hi-light the <ok> press enter on the keyboard and repeat if necessary, But your are agreeing to their licencing.
Tip: To copy from the terminal you can select the text with your mouse and right click <copy>
Then paste with code tags the output here in your thread.
Regards

---

### Post by mc4man on 2015-09-01
There was a typo in a previous suggestion, (post2) so make sure libdvdcss2 is installed - 
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
Then try vlc again, if it fails - 
close vlc but **leave dvd in the drive.**
run the lshw again & post the  *-cdrom  section
Looking for what the configuration: line says, for a DVD_VIDEO it should be like this - 
```
configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8 state=mounted status=ready
```
And in the *-medium  section (if there
```
configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8 state=mounted
```

---

### Post by mc4man on 2015-09-01
You should fool around with using your cursor & mouse to highlight specific text, then copy so you can paste into a reply rather than screenshots.
Basically just put your cursor at the end or beginning of whatever you want to highlight, _hold down left mouse button_  & _move cursor_ to start highlighting. Once highlighted to what you want release left mouse button & copy the highlighted text. Several ways to copy, one way is to just right click > copy. 
Then _leave whatever you copied from open_ & right click > paste in whatever window you want. (like a reply here

Once in your reply highlight the pasted text & click on the quote or code(#) icon to put that text in a box.
If desired download this very short video showing just that. 
[http://www.datafilehost.com/d/82a79742](http://www.datafilehost.com/d/82a79742)

---

### Post by pancho5 on 2015-09-02
This is what shows up:

*-cdrom
       description: DVD-RAM writer
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=nodisc


> **mc4man said:**
> There was a typo in a previous suggestion, (post2) so make sure libdvdcss2 is installed - 
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
Then try vlc again, if it fails - 
close vlc but **leave dvd in the drive.**
run the lshw again & post the  *-cdrom  section
Looking for what the configuration: line says, for a DVD_VIDEO it should be like this - 
```
configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8 state=mounted status=ready
```
And in the *-medium  section (if there
```
configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8 state=mounted
```

---

### Post by QDR06VV9 on 2015-09-02
I'm going to take for granted that you read mc4man pointing out the the typo for the libdvdcss command and that it installed with no errors.
But with a DVD loaded in my drive this is what "lshw" shows.
```
*-cdrom             description: DVD-RAM writer
             product: DVDRAM GH41N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             logical name: /media/me/DVDVIDEO
             version: MN01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /media/me/DVDVIDEO
                configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted

```
And yours dose not.
Bad Optical Drives do not let you know they are bad they just make you crazy with the lack of function.
Kind Regards

---

### Post by pancho5 on 2015-09-02
WELL, I TRIED IT AGAIN (SEE BELOW).  SO, YOU ARE SAYING I HAVE A BAD DVD PLAYER EVEN THOUGH IT WAS WORKING WITH WINDOWS 7 OS LESS THAN A WEEK AGO????



francisco@panchob:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
[sudo] password for francisco: 
--2015-09-02 17:33:35--  [http://download.videolan.org/pub/debian/stable//Packages](http://download.videolan.org/pub/debian/stable//Packages)
Resolving download.videolan.org (download.videolan.org)... 88.191.250.2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3520 (3.4K) [application/octet-stream]
Saving to: ‘/tmp/dvdcss-4sqnzA/Packages’

100%[=======================================================================================================>] 3,520       --.-K/s   in 0s      

2015-09-02 17:33:35 (233 MB/s) - ‘/tmp/dvdcss-4sqnzA/Packages’ saved [3520/3520]

--2015-09-02 17:33:35--  [http://download.videolan.org/pub/debian/stable/stable/libdvdcss2_1.2.13-0_amd64.deb](http://download.videolan.org/pub/debian/stable/stable/libdvdcss2_1.2.13-0_amd64.deb)
Resolving download.videolan.org (download.videolan.org)... 88.191.250.2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44462 (43K) [application/octet-stream]
Saving to: ‘/tmp/dvdcss-4sqnzA/libdvdcss.deb’

100%[=======================================================================================================>] 44,462       188KB/s   in 0.2s   

2015-09-02 17:33:36 (188 KB/s) - ‘/tmp/dvdcss-4sqnzA/libdvdcss.deb’ saved [44462/44462]

(Reading database ... 207944 files and directories currently installed.)
Preparing to unpack .../dvdcss-4sqnzA/libdvdcss.deb ...
Unpacking libdvdcss2 (1.2.13-0) over (1.2.13-0) ...
Setting up libdvdcss2 (1.2.13-0) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
francisco@panchob:~$ sudo lshw -c disk
  *-disk                  
       description: ATA Disk
       product: Hitachi HTS54505
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: C66G
       serial: 100410PBN40317CY12ZE
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=0009b723
  *-cdrom
       description: DVD-RAM writer
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=nodisc
francisco@panchob:~$

---

### Post by monkeybrain20122 on 2015-09-02
Did you try what I asked you to in post #5? Also try change to /dev/cdrom

---

### Post by QDR06VV9 on 2015-09-02
> **pancho5 said:**
> WELL, I TRIED IT AGAIN (SEE BELOW).  SO, YOU ARE SAYING I HAVE A BAD DVD PLAYER EVEN THOUGH IT WAS WORKING WITH WINDOWS 7 OS LESS THAN A WEEK AGO????

Please do not use uppercase when replying it is considered yelling or screaming!
I do not get paid to set here and help, But do so as a courtesy to others weather or not i have the right answer or suggestion.
I will just take this as you being frustrated, and i understand that.
To know for sure if the drive works put an Audio CD in it.

---

### Post by pancho5 on 2015-09-02
My sincere apologies...I am not upset...didn't realize uppercase letters signified that!  I will not use uppercase again...thanks for letting me know.

---

### Post by pancho5 on 2015-09-02
Yes I did...still did not work...same errors.

---

### Post by QDR06VV9 on 2015-09-02
No Worries!:D
Try the Audio CD in that drive and let us know.
Regards

---

### Post by QDR06VV9 on 2015-09-02
Sorry to hear that!
But I am out of any other Ideas to offer.
Regards

---

### Post by pancho5 on 2015-09-02
I put an Audio CD in, still doesn't work.  I screen dumped my drive for you to see.


> **runrickus said:**
> Please do not use uppercase when replying it is considered yelling or screaming!
I do not get paid to set here and help, But do so as a courtesy to others weather or not i have the right answer or suggestion.
I will just take this as you being frustrated, and i understand that.
To know for sure if the drive works put an Audio CD in it.

Thanks for your help anyway....appreciate it.

Do you think by reinstalling Ubuntu 14.04 LTS would make a difference?  Shot in the dark I would assume. :-k

---

### Post by mc4man on 2015-09-02
Try booting to a live usb >try me. Then insert a dvd & see if it shows up. 
 Doesn't matter if you can play it, ie. libdvdcss2, ect., the media has to be found & in the case of a dvd mounted before anything can access it.

---

### Post by pancho5 on 2015-09-02
Okay...I will try.

Tried booting to a live usb, inserted dvd and an audio cd, and the neither media showed up.  What I don't understand is that my daughter used the dvd for two weeks on Windows 7 before I wiped out Win 7 and put 14.04 LTS.   Doesnt make any sense...but course, computers don't make any sense anyway.

---

### Post by howefield on 2015-09-03
Taking a step back, what did the logs in your OP say ?

---

### Post by pancho5 on 2015-09-03
Well, I attempted to view the syslog files using zcat, but what should I grep for?

---

### Post by mc4man on 2015-09-03
As an aside - due you have a blu-ray disk you could try? Doesn't have to be playable, just to see if media is found
(- cd/dvd/blu-ray  drives have separate lens for cd's, dvd's & blu-ray's, cd/dvd drives have separate lens for cd's & dvd's

---

### Post by QDR06VV9 on 2015-09-03
Edit:_Sorry mc4man I was slow typing this_.
As far as I know VLC dose not keep logs.
whereis is good command to use in such a case.
```
me@me-Aspire-M3300:~$ whereis vlc
vlc:/usr/bin/vlc /usr/lib/vlc /usr/bin/X11/vlc /usr/share/vlc /usr/share/man/man1/vlc.1.gz
me@me-Aspire-M3300:~$ 

```
That tells you where things were placed from the installer.
When VLC is open you can look in the Tabs at the top Then under Tools There are Options like _**Media Information**_ and _**Messages**_ and other stuff that I can not recall off hand but those two are useful.
When VLC can read the data from you device It would have output like in the Screenshot Below.
Hope that makes sense now.

---

### Post by pancho5 on 2015-09-03
No...no blu-ray disk

---

### Post by pancho5 on 2015-09-03
Anyone else have any ideas?  [-o

---

### Post by SeijiSensei on 2015-09-04
First, look in /var/log/dmesg and see if there is an entry for the device.  Another alternative is to run the command "sudo lshw" to get a full census of the machine's hardware.  If you use "sudo lshw | more" you'll be able to page through the results. On my HP laptop I get
```

       *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GT31L
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: MR52

```

If the computer can see the drive, insert a disc, then enter the command "eject /dev/sr0".  Does the drive open?

Try removing the DVD device from the laptop, blowing out the interior with compressed air, and reinserting the drive.  Usually this is a pretty simple process of flipping a latch on the bottom of the machine.

---

### Post by pancho5 on 2015-09-04
Hello All!

Do you see anything wrong with this???   

```
panchob@Run-26:~$ sudo apt-get install regionset
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libart-2.0-2 libavresample1 libbs2b0 libgif4 libquvi-scripts libquvi7
  libvdpau1 mplayer2 python-pexpect python-renderpm python-reportlab
  python-reportlab-accel
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  regionset
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 12.5 kB of archives.
After this operation, 77.8 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe regionset amd64 0.1-3 [12.5 kB]
Fetched 12.5 kB in 0s (104 kB/s)     
Selecting previously unselected package regionset.
(Reading database ... 203879 files and directories currently installed.)
Preparing to unpack .../regionset_0.1-3_amd64.deb ...
Unpacking regionset (0.1-3) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up regionset (0.1-3) ...
panchob@Run-26:~$ sudo regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.
panchob@Run-26:~$ sudo apt-get install libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
libdvdread4 set to manually installed.
The following packages were automatically installed and are no longer required:
  libart-2.0-2 libavresample1 libbs2b0 libgif4 libquvi-scripts libquvi7
  libvdpau1 mplayer2 python-pexpect python-renderpm python-reportlab
  python-reportlab-accel
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
panchob@Run-26:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2015-09-04 13:47:19--  [http://download.videolan.org/pub/debian/stable//Packages](http://download.videolan.org/pub/debian/stable//Packages)
Resolving download.videolan.org (download.videolan.org)... 88.191.250.2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3520 (3.4K) [application/octet-stream]
Saving to: ‘/tmp/dvdcss-N2S6Zy/Packages’

100%[=======================================================================================================>] 3,520       --.-K/s   in 0s      

2015-09-04 13:47:20 (208 MB/s) - ‘/tmp/dvdcss-N2S6Zy/Packages’ saved [3520/3520]

--2015-09-04 13:47:20--  [http://download.videolan.org/pub/debian/stable/stable/libdvdcss2_1.2.13-0_amd64.deb](http://download.videolan.org/pub/debian/stable/stable/libdvdcss2_1.2.13-0_amd64.deb)
Resolving download.videolan.org (download.videolan.org)... 88.191.250.2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44462 (43K) [application/octet-stream]
Saving to: ‘/tmp/dvdcss-N2S6Zy/libdvdcss.deb’

100%[=======================================================================================================>] 44,462       174KB/s   in 0.2s   

2015-09-04 13:47:20 (174 KB/s) - ‘/tmp/dvdcss-N2S6Zy/libdvdcss.deb’ saved [44462/44462]

Selecting previously unselected package libdvdcss2.
(Reading database ... 203886 files and directories currently installed.)
Preparing to unpack .../dvdcss-N2S6Zy/libdvdcss.deb ...
Unpacking libdvdcss2 (1.2.13-0) ...
Setting up libdvdcss2 (1.2.13-0) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
panchob@Run-26:~$
```

I will try it SiejiSensi....Thanks!

Executed the /var/log/dmesg command which displays the DVD.  But, what is odd is that when execute the 'sudo lshw' command, the DVD does not show up!  I will remove the DVD device from the laptop.

  	 	 	 	   [    1.412980] ata2.00: ATAPI: TSSTcorp DVDWBD TS-LB23A, SC00, max UDMA/100  
 [    1.416647] ata2.00: configured for UDMA/100  
 [    1.423778] scsi 1:0:0:0: CD-ROM            TSSTcorp DVDWBD TS-LB23A  SC00 PQ: 0 ANSI: 5  
 [    1.444993] sr 1:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray  
 [    1.444998] cdrom: Uniform CD-ROM driver Revision: 3.20

Oh yes...entered the eject/dev/sr0 command and the drive did open.  :D

Cleaned the DVD drive with can of Dust Remover, still did not work!

---

### Post by pancho5 on 2015-10-07
Anyone have any other ideas?  I did remove the DVD/CD player and plugged it back it.  Some how its not recognizing the drivers because it doesn't mount.

---

