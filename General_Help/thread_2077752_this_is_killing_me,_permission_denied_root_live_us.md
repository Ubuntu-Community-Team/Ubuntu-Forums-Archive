---
title: "this is killing me, permission denied root live usb ubuntu one"
date: 2012-10-29
forum: General Help
---

### Post by sdowney717 on 2012-10-29
I decided on a pc to clone a drive using dd
I sincerely desire to save some files off this drive FIRST
HOWEVER, I can not upload files to ubuntu one since they are owned by root???

I booted to a 12.10 usb drive and I cant do a thing with it moving any files.
I also tried google drive and it refuses to upload accept any PDF.

I thought this usb drive also had some kind of persistence file where is that? I set to 1gb on creation.

---

### Post by Vaphell on 2012-10-29
what kind of files?
**ls -l** output would be nice

---

### Post by sdowney717 on 2012-10-29
Owned by root.
running off a flash drive
have no idea how to open terminal to that 60gb drive

all files owned by root
permission denied on copying files anywhere
very frustrated, I really hate this right now. I tried hugedrive which is broken as is google drive for pdf. I was able to upload other types of files to google drive, not PDF

---

### Post by sdowney717 on 2012-10-29
> ubuntu@ubuntu:~$ ls
Desktop    Downloads  Pictures  Templates   Videos
Documents  Music      Public    Ubuntu One
ubuntu@ubuntu:~$ 

of course I don not know how to get to the other drive in terminal window
this is what I get.
I quess I will have to reboot off the original drive to do this as the LIVE USB wont let me do anything

---

### Post by snowpine on 2012-10-29
You can launch the file manager as root with:

```
gksu nautilus
```

Then you can copy the files to your /home folder and right-click to change permissions to your user.

---

### Post by sdowney717 on 2012-10-29
solved it the only sure way I know. Remove drive from computer.
Put drive into usb adapter
load drive on another PC
copy whatever files I wish.

These files I copy are all owned by root for some reason the entire drive is root.

from my pc this is the ls -l for those files

```
scott@scott-P5QC:~$ cd weird
scott@scott-P5QC:~/weird$ ls -l
total 231328
-rw-r--r--  1 root root  1028581 Sep 30  2008 01691_ridingtherocks_1280x1024.jpg
-rw-r--r--  1 root root    25049 Aug 28  2007 1_121034Y501.jpg
-rw-r--r--  1 root root     9055 Aug 28  2007 1_Baby_Tux-1280x1024.jpg
-rw-r--r--  1 root root     1729 Sep  6  2007 1_Baby_Tux-1280x1024.jpg.msf
-rw-r--r--  1 root root     1729 Sep  6  2007 1_eternalubuntu.jpg.msf
-rw-r--r--  1 root root   334017 Aug 28  2007 1_Firefox_wallpaper.png
-rw-r--r--  1 root root     1731 Sep  6  2007 1_Firefox_wallpaper.png.msf
-rw-r--r--  1 root root    18774 Aug 28  2007 1_linux-tux-born-2-frag-XP.jpg
-rw-r--r--  1 root root     1729 Sep  6  2007 1_linux-tux-born-2-frag-XP.jpg.msf
-rw-r--r--  1 root root     6639 Aug 28  2007 1_pengiun.jpeg
-rw-r--r--  1 root root     1729 Sep  6  2007 1_pengiun.jpeg.msf
-rw-r--r--  1 root root    91759 Aug 28  2007 1_ubuntuvista117_1280x1024.png
-rw-r--r--  1 root root     1532 Sep  6  2007 1_ubuntuvista117_1280x1024.png.msf
-rw-r--r--  1 root root    10305 Oct 21  2007 3d.tar.gz
-rw-r--r--  1 root root    25664 Aug 13  2008 _44920723_enceladus.jpg
-rw-r--r--  1 root root     4459 May  4  2008 alcohol burning
-rw-r--r--  1 root root      593 Aug  2  2007 assets.csv
-rw-r--r--  1 root root     1350 Jun 20  2008 AutoHotkey.ahk
-rw-r--r--  1 root root      111 Oct 18  2008 battery
-rw-r--r--  1 root root     9278 Apr 12  2008 battery stuff
-rw-r--r--  1 root root   374674 Dec  4  2007 BEN400.ZIP
-rw-------  1 root root  1196111 Sep 14  2008 BFLC_English.pdf
-rw-r--r--  1 root root      603 Mar  1  2009 bluemanppakey
-rw-r--r--  1 root root      564 Jul  6  2009 boat foam board floatation
-rw-r--r--  1 root root     1074 May  3  2008 boat fuel gph examples
-rw-r--r--  1 root root     1726 May 10  2008 boat oil filters
-rw-r--r--  1 root root    49947 Jan  3  2008 bookmarks-2008-01-03.html
-rw-r--r--  1 root root    69297 Dec 30  2007 bookstoreindex.html
-rw-r--r--  1 root root    71098 Dec 30  2007 bookstoreindexpage
-rw-r--r--  1 root root      140 Feb 10  2009 brasero.toc
-rw-------  1 root root   801131 Dec 19  2007 C1458401.pdf
-rw-r--r--  1 root root     1244 May 26  2009 car pain
-rw-r--r--  1 root root  6263466 Oct 10  2007 ca_setup.exe
-rw-r--r--  1 root root      383 Jun 22  2009 cellulose bag insulation
-rw-r--r--  1 root root 25296896 Jul 25  2007 CETrial11.exe
-rwxr-xr-x  1 root root    27814 Jun 22  2008 compiz-chec
drwxr-xr-x  2 root root     4096 Oct 29 10:55 contour fuse panel
drwxr-xr-x  6 root root     4096 Oct 29 10:59 converted mp3 files128
drwxr-xr-x  2 root root     4096 Oct 29 10:59 convertit
drwxr-xr-x  2 root root     4096 Oct 29 10:59 corel hack
-rw-r--r--  1 root root    75975 May  5  2006 data1.hdr
-rw-r--r--  1 root root       29 Dec 18  2007 david number
-rw-r--r--  1 root root      347 Jan 15  2008 daytradingrules
-rw-r--r--  1 root root     1016 Jan 15  2008 daytrading rules
-rw-r--r--  1 root root    13766 Apr 21  2008 download.htm
-rw-r--r--  1 root root     6425 Sep  6  2008 dr787t discs
-rw-r--r--  1 root root     1115 Sep  6  2007 Drafts.msf
-rw-r--r--  1 root root    54859 May 20  2008 Draper-Flying_Fish.jpg
-rw-r--r--  1 root root 12579549 Nov 27  2006 dsm320_manual_170.pdf
-rw-r--r--  1 root root     7437 Oct  2  2008 edited videos.xml
-rw-r--r--  1 root root    25664 Aug 13  2008 enceladus.jpg
-rw-r--r--  1 root root      693 Apr  6  2008 ENG_F3_3258_assy_diag_Rev_A.pdf
-rw-r--r--  1 root root   459544 Mar 12  2004 engine32.cab
-rw-------  1 root root   255970 Jan  2  2009 FANMedia.pdf
-rw-r--r--  1 root root   641460 Dec 16  2008 Firefox_wallpaper.png
-rw-r--r--  1 root root 23531520 Sep  6  2008 firstvideo
-rw-r--r--  1 root root    45653 Sep  6  2008 firstvideo.idx
-rw-r--r--  1 root root     1432 Sep  6  2008 firstvideo.qs
-rw-r--r--  1 root root    28105 Sep  6  2008 firstvideo.stat
-rw-r--r--  1 root root   213602 Sep  6  2008 firstvideo.stat.fake
-rw-r--r--  1 root root    14537 Oct 13  2007 flvplayer.swf
-rw-r--r--  1 root root    25616 Oct 31  2008 flyback_0.4.0.tar.gz
drwxr-xr-x  2 root root     4096 Oct 29 10:59 fonts
-rw-r--r--  1 root root    60793 Apr 13  2008 gecko466naskrecki.jpg
-rw-r--r--  1 root root    44980 Jul  9  2008 geckot3RJvT
-rw-r--r--  1 root root      305 Oct 18  2007 glxgears
-rw-r--r--  1 root root    18030 Jun  5  2008 gore.jpg
-rw-r--r--  1 root root     9431 Mar 18  2009 HAMPTON.svg
-rw-r--r--  1 root root     9357 Mar 17  2009 hampton, Va.svg
-rw-r--r--  1 root root    15194 Apr 16  2009 handprint poem.odt
-rw-r--r--  1 root root       38 Jul 29  2008 Henry ubuntu user login
-rw-r--r--  1 root root      139 Nov 21  2008 hpscanjet4600
-rw-r--r--  1 root root       55 Jun 20  2009 hydrocool pressures goodman heat pump
-rw-r--r--  1 root root    36395 Sep 30  2007 hynix.odt
-rw-------  1 root root    39852 Aug 18  2007 hyperkorea.ZIP
-rw-------  1 root root    73728 Aug 18  2007 HyperlinkProjectExample.exe
-rw-r--r--  1 root root     1502 Sep  6  2007 Inbox.msf
-rw-r--r--  1 root root      751 Aug 20  2008 intel xorg
-rw-r--r--  1 root root     3403 Oct  8  2007 internet TV
-rw-r--r--  1 root root    63794 Aug  3  2008 k2.jpg
-rw-r--r--  1 root root    23888 Aug 28  2007 kittens-1024x768.jpg
-rw-r--r--  1 root root      491 May  5  2006 layout.bin
-rw-------  1 root root  8727739 Sep 18  2007 lbwpmm.EM21ZMR.pdf
-rw-r--r--  1 root root    93696 Mar 19  2001 LCDTEST.exe
-rw-r--r--  1 root root       30 Oct 22  2008 lg return
-rw-r--r--  1 root root   783227 Aug 23  2007 libGL.so.1
-rw-r--r--  1 root root    17676 Apr  8  2008 liblaunchpad-integration1_0.1.18_i386.deb
-rw-------  1 root root    40960 Sep 19  2007 linksys2102-sunrocket.cfg
-rw-r--r--  1 root root   330880 Jul 21  2008 linux sucks windows.png
-rw-r--r--  1 root root     9284 Feb  7  2009 lord day
-rw-r--r--  1 root root   204719 Oct 15  2008 lt.gif
-rw-r--r--  1 root root     3666 Dec 16  2008 message1
dr-xr-xr-x  2 root root     4096 Oct 29 10:56 midisongs
-rw-r--r--  1 root root     1211 Nov 13  2007 monitor sleep
drwxr-xr-x  2 root root     4096 Oct 29 10:54 motherboards
-rw-------  1 root root       25 Sep  6  2007 msgFilterRules.dat
drwxr-xr-x 17 root root     4096 Oct 29 10:56 Music
-rwxrwxrwx  1 root root  3719168 Jul 30  2007 mysql-connector-odbc-3.51.17-win32.msi
-rw-r--r--  1 root root    36844 Oct  4  2008 myth log file.tar.gz
-rw-r--r--  1 root root   118666 Jan 30  2008 nautilus-debug-log.txt
-rw-r--r--  1 root root        0 Jul 12  2009 New File
drwxr-xr-x  3 root root     4096 Oct 29 10:54 np242
-rw-r--r--  1 root root      262 Jan  3  2008 Ntest.CFG
-rw-r--r--  1 root root   591552 Mar 19  2001 Ntest.exe
-rwxrwxrwx  1 root root   553727 Nov  6  2007 ocean.jpg
-rw-r--r--  1 root root  1542373 Dec 10  2008 ocean.png
-rw-r--r--  1 root root     7880 Mar 18  2009 OLDGLORY.svg
-rw-r-----  1 root root  1359471 Oct 25  2008 out.jpeg
-rw-r-----  1 root root   911725 Oct 28  2008 out.png
-rw-r-----  1 root root   503200 Jan 16  2008 out.pnm
-rw-r--r--  1 root root    84817 Nov  8  2007 Oxbow_sunrise_XP_1002_1_900.jpg
drwxr-xr-x  2 root root     4096 Oct 29 11:01 pdf files
-rw-r--r--  1 root root    11322 Aug 28  2007 penguin2.jpg
drwxr-xr-x  7 root root     4096 Oct 29 11:01 Pictures
drwxr-xr-x  4 root root     4096 Oct 29 11:06 Pkware
-rw-r--r--  1 root root    55240 Oct 13  2007 player.swf
-rw-r--r--  1 root root      326 Aug 25  2007 playlist
-rw-r--r--  1 root root       61 Sep  6  2007 popstate.dat
-rw-r--r--  1 root root      533 Aug 14  2008 power scan dish network
drwxrwxrwx  2 root root     4096 Oct 29 10:56 RCA Remotes
-rw-r--r--  1 root root      343 Jul 20  2008 REALbasic License
-rw-r--r--  1 root root   148480 Dec 14  2007 ResDll.dll
-rw-------  1 root root  2572865 Aug 27  2008 samsun731n.pdf
-rw-r--r--  1 root root    95242 Jul  7  2008 saturn946x710.jpg
-rw-r--r--  1 root root     1854 Mar 26  2009 savemyeep.txt
drwxr-xr-x  3 root root     4096 Oct 29 10:54 SDLand_series
-rw-r--r--  1 root root     1132 Sep  6  2007 Sent.msf
-rw-r--r--  1 root root   176760 Mar 29  2006 setup.bmp
-rw-r--r--  1 root root   116880 Mar 12  2004 setup.exe
-rw-r--r--  1 root root   449909 May  5  2006 setup.ibt
-rw-r--r--  1 root root      696 May  5  2006 setup.ini
-rw-r--r--  1 root root   193558 May  5  2006 setup.inx
-rw-r--r--  1 root root      841 Mar 29  2006 setup.iss
-rw-r--r--  1 root root    65476 Jul  3  2006 Shardee.ttf
-rw-r--r--  1 root root    14814 Aug 28  2007 sky2.jpg
-rw-r--r--  1 root root    25032 Aug 28  2007 sky.jpg
drwxr-xr-x  2 root root     4096 Oct 29 10:53 snow camera
drwx------  3 root root     4096 Oct 29 10:57 songs
dr-xr-xr-x  2 root root     4096 Oct 29 10:57 Songs
drwxr-xr-x  2 root root     4096 Oct 29 10:57 spaata.pl_files
-rw-r--r--  1 root root     3667 Sep 20  2007 spaata.pl.html
drwxr-xr-x  4 root root     4096 Oct 29 11:02 spa stuff
-rw-r--r--  1 root root    59600 Jun 27  2007 Stonehenge.jpg
-rw-r--r--  1 root root    18644 Dec  2  1997 st______.ttf
drwxr-xr-x  2 root root     4096 Oct 29 10:57 superheat
-rw-r--r--  1 root root    18550 Nov  9  2007 supervolcano.jpg
drwxr-xr-x  2 root root     4096 Oct 29 11:02 tax20089tradeking
drwxr-xr-x  2 root root     4096 Oct 29 10:53 taxact
-rw-r--r--  1 root root     1118 Sep  6  2007 Templates.msf
-rw-r--r--  1 root root  9256017 Jan 30  2008 test1AndTheSeasons_MOVbest.MP4
-rw-r--r--  1 root root  1542373 Dec 10  2008 tester.png
-rw-r--r--  1 root root   819244 Oct 25  2008 test.wav
-rw-------  1 root root   166565 Apr  3  2009 tghy
-rw-r--r--  1 root root  1087786 Jan 28  2008 THE_PROCESSION_WMV.AVI
drwxr-xr-x  4 root root     4096 Oct 29 10:58 Toshiba
-rw-r--r--  1 root root 20349618 Sep 10  2008 Track 11.wav
-rw-r--r--  1 root root     1221 Sep  6  2007 Trash.msf
-rw-r--r--  1 root root    23698 Jun 30  2008 tunguska.jpg
-rw-r--r--  1 root root      677 Oct 31  2008 unnamed.rip
-rw-r--r--  1 root root     1352 Feb 11  2008 upgrading service
-rw-r--r--  1 root root    35782 Apr  4  2009 urlfilter.ini
-rw-r--r--  1 root root      184 Aug 27  2008 usb trouble
drwxr-xr-x  2 root root     4096 Oct 29 11:03 various pdf
drwxr-xr-x  2 root root     4096 Oct 29 11:03 vl400
-rw-------  1 root root     1111 Jun 28  2009 vmware-config.pl.patch.txt
-rw-r--r--  1 root root 42729516 Nov 17  2008 voicedemocracy2.wav
-rw-r--r--  1 root root 42147884 Oct 30  2008 voiceofdemocracy2008.wav
-rw-r--r--  1 root root     3958 Jun 24  2009 voipms
-rw-r--r--  1 root root     3045 Jun 14  2009 voipvoip talk www.voipvoip.com
-rw-r--r--  1 root root    44065 Sep  6  2008 VTS_01_1.VOB.idx
drwx------  3 root root     4096 Oct 29 10:53 watchHDTV
-rw-r--r--  1 root root   133632 Jan 10  2008 WatchHDTV.exe
-rw-r--r--  1 root root    61440 Jan  7  2008 WatchHDTV Settings.exe
-rw-r--r--  1 root root      233 Dec 16  2008 weather
-rw-r--r--  1 root root    23310 Sep 19  2008 webscr.html
-rw-r--r--  1 root root 19974928 Jan 28  2008 WELCOME_BACK_WMV(2).AVI
drwxr-xr-x  2 root root     4096 Oct 29 11:04 wgt
drwxr-xr-x  2 root root     4096 Oct 29 11:04 wgt624
drwxr-xr-x  2 root root     4096 Oct 29 11:04 wgt624 firmware
-rw-r--r--  1 root root      409 Aug 10  2008 window regulator parts
-rw-r--r--  1 root root       31 Jun 19  2009 windows7rc
-rw-r--r--  1 root root    61768 Jul 10  2008 winetricks.2
-rw-r--r--  1 root root    62684 Aug 25  2008 winetricks.3
-rw-r--r--  1 root root    62684 Aug 25  2008 winetricks.4
drwxr-xr-x  2 root root     4096 Oct 29 11:04 wslam
-rw-r--r--  1 root root      392 Oct 17  2007 xgl startup change
drwxr-xr-x  2 root root     4096 Oct 29 11:06 zip files
scott@scott-P5QC:~/weird$ 

```

---

### Post by snowpine on 2012-10-29
Linux has easy and well-documented tools to change file ownership. You can choose to learn them, or not learn them, your call. Here are the top 2 google hits for "ubuntu permissions." I have used both of these sites many times in the past and can vouch for their accuracy:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by sdowney717 on 2012-10-29
thanks. But when running from Live USB, is the drive always root?
Not doing any special mount, just using the file manager presented when on LiveUSB.

---

### Post by snowpine on 2012-10-29
> **sdowney717 said:**
> thanks. But when running from Live USB, is the drive always root?
Not doing any special mount, just using the file manager presented when on LiveUSB.

No, it is bad security practice to always run as root. To modify root-owned files you need to use some type of sudo or gksu command such as 'gksu nautilus' to launch the file manager as root or 'sudo chown' to change ownership from the terminal.

---

### Post by sdowney717 on 2012-10-29
What I want to know is, when you boot up a Live USB, do the files on the hard drives show up as being owned by root?

Or do they show up as being owned by a user name?

If so, makes me wonder why they would show as owned by root.

---

### Post by snowpine on 2012-10-29
> **sdowney717 said:**
> What I want to know is, when you boot up a Live USB, do the files on the hard drives show up as being owned by root?

Or do they show up as being owned by a user name?

If so, makes me wonder why they would show as owned by root.

I don't understand the question. They are owned by who they are owned by. Booting from a Live USB does not change the ownership. (But now you know the easy tools to change the ownership if you wish.)

---

### Post by sdowney717 on 2012-10-29
Those files were on an older version of Ubuntu, something I had not used for a couple years. So why were they showing up as owned by root?
who knows, but what your saying is if I check my current driver after booting with a live USB, they wont say owned by root. I always just log in with my user name. How would all files get owned by root?

---

### Post by snowpine on 2012-10-29
It is impossible for me to tell from my computer why some files are owned by root on your computer. Hopefully the links above will be helpful in claiming ownership of these files for your current user.

---

