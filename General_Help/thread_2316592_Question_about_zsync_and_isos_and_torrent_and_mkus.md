---
title: "Question about zsync and isos and torrent and mkusb"
date: 2016-03-09
forum: General Help
---

### Post by vasa1 on 2016-03-09
I want to know more about *zsync*. 

I've looked at [https://help.ubuntu.com/community/ZsyncCdImage](https://help.ubuntu.com/community/ZsyncCdImage)

Suppose I download the torrent file for Lubuntu 16.04 beta from here: [http://cdimage.ubuntu.com/lubuntu/releases/16.04/beta-1/lubuntu-16.04-beta1-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/lubuntu/releases/16.04/beta-1/lubuntu-16.04-beta1-desktop-amd64.iso.torrent)

I can then open the torrent file using Transmission and download the *iso*.

Can I then update *that* iso using zsync? 

Or must I start off with [http://cdimage.ubuntu.com/lubuntu/releases/16.04/beta-1/lubuntu-16.04-beta1-desktop-amd64.iso.zsync?](http://cdimage.ubuntu.com/lubuntu/releases/16.04/beta-1/lubuntu-16.04-beta1-desktop-amd64.iso.zsync?)

If I must start off with lubuntu-16.04-beta1-desktop-amd64.iso.zsync, how do I download it? Can I use something like aria2c? ```
aria2c "http://cdimage.ubuntu.com/lubuntu/releases/16.04/beta-1/lubuntu-16.04-beta1-desktop-amd64.iso.zsync"
```

How do I convert lubuntu-16.04-beta1-desktop-amd64.iso.zsync into a live USB? Will mkusb handle this task?

---

### Post by howefield on 2016-03-09
> **vasa1 said:**
> Suppose I download the torrent file for Lubuntu 16.04 beta from here: [http://cdimage.ubuntu.com/lubuntu/releases/16.04/beta-1/lubuntu-16.04-beta1-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/lubuntu/releases/16.04/beta-1/lubuntu-16.04-beta1-desktop-amd64.iso.torrent)

I can then open the torrent file using Transmission and download the *iso*.

Can I then update *that* iso using zsync? 

Yes.

Navigate to the folder containg the iso and use..

```
zsync http://cdimage.ubuntu.com/lubuntu/releases/16.04/beta-1/lubuntu-16.04-beta1-desktop-amd64.iso.zsync
```

You probably want the file names to match, ie whatever the destination is make sure the source is the same.

> Or must I start off with [http://cdimage.ubuntu.com/lubuntu/releases/16.04/beta-1/lubuntu-16.04-beta1-desktop-amd64.iso.zsync?](http://cdimage.ubuntu.com/lubuntu/releases/16.04/beta-1/lubuntu-16.04-beta1-desktop-amd64.iso.zsync?)

No :)

If I must start off with lubuntu-16.04-beta1-desktop-amd64.iso.zsync, how do I download it? Can I use something like aria2c? ```
aria2c "http://cdimage.ubuntu.com/lubuntu/releases/16.04/beta-1/lubuntu-16.04-beta1-desktop-amd64.iso.zsync"
```

If you have no file to start you off, zsync will realise that and download the whole iso. 	

```
zsync http://cdimage.ubuntu.com/lubuntu/releases/16.04/beta-1/lubuntu-16.04-beta1-desktop-amd64.iso.zsync
```

will result in something like..

```
hugh@xenial-laptop:~$ mkdir Lubuntu
hugh@xenial-laptop:~$ cd Lubuntu/
hugh@xenial-laptop:~/Lubuntu$ zsync http://cdimage.ubuntu.com/lubuntu/releases/16.04/beta-1/lubuntu-16.04-beta1-desktop-amd64.iso.zsync
#################### 100.0% 0.0 kBps DONE    

No relevent local data found - I will be downloading the whole file. If that's not what you want, CTRL-C out. You should specify the local file is the old version of the file to download with -i (you might have to decompress it with gzip -d first). Or perhaps you just have no data that helps download the file
downloading from http://cdimage.ubuntu.com/lubuntu/releases/16.04/beta-1/lubuntu-16.04-beta1-desktop-amd64.iso:
-------------------- 0.0% 8.7 kBps         
-------------------- 1.5% 2776.1 kBps 5:22 ETA  ^C
hugh@xenial-laptop:~/Lubuntu$ 
```

> How do I convert lubuntu-16.04-beta1-desktop-amd64.iso.zsync into a live USB? Will mkusb handle this task?

With whatever your preferred method is for creating live media. After downloading with zsync you'll have a standard .iso file to do with as you would normally.

Another example if it helps, taking yesterdays Ubuntu daily and turning it into todays Lubuntu daily..

```
hugh@xenial-laptop:~/Xenial$ zsync http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso.zsync
#################### 100.0% 45.7 kBps DONE    

reading seed file xenial-desktop-amd64.iso: ********************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read xenial-desktop-amd64.iso. Target 60.9% complete.      **********************
downloading from http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso:
#################### 100.0% 2745.6 kBps DONE     

verifying download...checksum matches OK
used 554942464 local, fetched 356743353
hugh@xenial-laptop:~/Xenial$
```

---

### Post by sudodus on 2016-03-09
If you run zsync in the same directory as you have the iso file (matching the command line with zsync), it will download only the parts which differ from the previous version. After the update, the previous version is renamed to ...zs-old. You need not grab the zsync files, they stay on the ubuntu server.

It should not matter how you get the first version of the iso file, but it is important that the name matches what is set up for zsync (so you may need to rename it). I usually get even the first version via zsync (which may be slower than with torrent, but 'everything will be set up correctly' for the future incremental downloads).

Example: I have a directory **/media/multimed-2/test/lubuntu** for the current iso files and one-line scripts with zsync

```

$ cat getlubuntu-xenial
zsync http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-i386.iso.zsync

$ cat getlubuntu64-xenial
zsync http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso.zsync

$ cat getalternate-xenial 
zsync http://cdimage.ubuntu.com/lubuntu/daily/current/xenial-alternate-i386.iso.zsync

$ cat getlubuntu-trusty
zsync http://cdimage.ubuntu.com/lubuntu/trusty/daily-live/current/trusty-desktop-i386.iso.zsync

```

I have a script to list recent files (in this case touched within 30 days). It shows that there are 'normal' iso files and 'iso.zs-old' files.

```
$ newfiles 30
#perms    	size	date      	time 	file-name
-rwxr-xr-x	98	2016-02-16	08:14	"getlubuntu64-trusty"
-rw-------	737M	2016-02-17	08:57	"trusty-desktop-amd64.iso.zs-old"
-rw-------	737M	2016-02-17	23:16	"trusty-desktop-amd64.iso"
-rw-------	727M	2016-02-17	23:22	"trusty-desktop-i386.iso.zs-old"
-rw-------	727M	2016-02-19	15:11	"trusty-desktop-i386.iso"
-rw-------	859M	2016-02-22	16:21	"xenial-desktop-i386.iso.zs-old"
-rw-------	683M	2016-02-22	19:19	"xenial-alternate-amd64.iso.zs-old"
-rw-------	862M	2016-02-22	21:12	"xenial-desktop-amd64.iso.zs-old"
-rw-------	868M	2016-02-24	18:57	"xenial-desktop-amd64.iso"
-rw-------	867M	2016-02-24	18:59	"xenial-desktop-i386.iso"
-rwxrwxr-x	88	2016-02-24	19:42	"getalternate64-xenial"
-rw-rw-r--	117	2016-02-25	17:23	"lenovo-x131e.txt"
-rw-------	702M	2016-03-02	16:38	"xenial-alternate-i386.iso.zs-old"
-rw-------	705M	2016-03-04	16:32	"xenial-alternate-amd64.iso"
-rw-------	701M	2016-03-04	16:35	"xenial-alternate-i386.iso"
```

So as usual, I use mkusb or mkusb-nox to flash the current iso file into a pendrive.

---

### Post by ajgreeny on 2016-03-09
zsync can also be useful if you want to try several different DE versions of *ubuntu as you can point the zsync download to an input iso file, eg ubuntu-----.iso and turn it into a xubuntu-----.iso.

I have done that quite a lot in order to run the development versions in VBox and it saves a lot of download time and bandwidth.  For example in this command I point zsync to a xubuntu iso I already have by using the -i option and end with a newly downloaded lubuntu iso as the output file.  You can name the output file as you wish to make it easier to see what is what in your download folder if that helps.
```
zsync [http://cdimages.ubuntu.com/lubuntu/releases/14.04/release/lubuntu-14.04.3-desktop-i386.iso.zsync](http://cdimages.ubuntu.com/lubuntu/releases/14.04/release/lubuntu-14.04.3-desktop-i386.iso.zsync) -i ~/Downloads/ISOs/xubuntu-14.04.3-desktop-i386.iso -o ~/Downloads/ISOs/lubuntu-14.04.3-desktop-i386.iso
```

---

### Post by sudodus on 2016-03-09
Thanks for the tip, ajgreeny :-)

---

### Post by vasa1 on 2016-03-10
```
07:54 PM ~ $ cd ZSYNC/
07:55 PM ~/ZSYNC $ zsync http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso.zsync
#################### 100.0% 91.2 kBps DONE     

No relevent local data found - I will be downloading the whole file. If that's not what you want, CTRL-C out. You should specify the local file is the old version of the file to download with -i (you might have to decompress it with gzip -d first). Or perhaps you just have no data that helps download the file
downloading from http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso:
-------------------- 0.2% 6.0 kBps         ETA  
-------------------- 0.6% 4.2 kBps         ETA  
...
and some hours later (I have a slow network)
...
#################--- 87.4% 1.2 kBps         TA   
##################-- 92.0% 1.2 kBps         TA   
#################### 100.0% 97.3 kBps DONE       

verifying download...checksum matches OK
used 0 local, fetched 911212878
10:32 PM ~/ZSYNC $ 

```

And then today:```
05:25 AM ~/ZSYNC $ zsync http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso.zsync
#################### 100.0% 91.3 kBps DONE      

reading seed file xenial-desktop-amd64.iso: ****************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read xenial-desktop-amd64.iso. Target 87.0% complete.      
downloading from http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso:

#################### 100.0% 20.5 kBps DONE    A  

verifying download...checksum matches OK
used 793505792 local, fetched 119434981
05:48 AM ~/ZSYNC $ 
Now, I have two files:
05:48 AM ~/ZSYNC $ ll
total 1780804
-rw------- 1 vasa1 vasa1 912261120 Mar  9 17:25 xenial-desktop-amd64.iso
-rw------- 1 vasa1 vasa1 911212544 Mar  8 17:49 xenial-desktop-amd64.iso.zs-old
06:31 AM ~/ZSYNC $ 

```
I let mkusb do its magic and ran 16.04 from a live USB happily for a couple of hours.

Thank you everyone :)

---

### Post by howefield on 2016-03-10
Cool, don't remember ever having to try it but if a freshly zsynced iso fails to boot for whatever reason you can rename xenial-desktop-amd64.iso.zs-old by removing .zs.old and use, it is a copy of the file before you zsynced it.

You can see in the example below (where an Ubuntu daily was turned into an Lubuntu daily) that the .zs.old is 1577058204 large as it is a copy of the original Ubuntu iso that was started with, after zsyncing the next day the .zs.old file is 911212544 large - the same size as the lubuntu daily from the previous day. Hope that makes sense :)

```
hugh@xenial-laptop:~$ cd Xenial/
hugh@xenial-laptop:~/Xenial$ ls -al
total 2430020
drwxrwxr-x  2 hugh hugh       4096 Mar  9 14:11 .
drwxr-xr-x 22 hugh hugh       4096 Mar 10 07:08 ..
-rw-------  1 hugh hugh          2 Feb 21 17:06 completer.hist
-rw-------  1 hugh hugh  911212544 Mar  8 16:49 xenial-desktop-amd64.iso
-rw-------  1 hugh hugh 1577058304 Mar  8 07:08 xenial-desktop-amd64.iso.zs-old
hugh@xenial-laptop:~/Xenial$ zsync http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso.zsync
#################### 100.0% 1072.5 kBps DONE     

reading seed file xenial-desktop-amd64.iso: ****************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read xenial-desktop-amd64.iso. Target 87.0% complete.      ********************************************************
downloading from http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso:
#################### 100.0% 2313.1 kBps DONE     

verifying download...checksum matches OK
used 793505792 local, fetched 119429814
hugh@xenial-laptop:~/Xenial$ ls -al
total 1780864
drwxrwxr-x  2 hugh hugh      4096 Mar 10 07:09 .
drwxr-xr-x 22 hugh hugh      4096 Mar 10 07:08 ..
-rw-------  1 hugh hugh         2 Feb 21 17:06 completer.hist
-rw-------  1 hugh hugh 912261120 Mar  9 16:25 xenial-desktop-amd64.iso
-rw-------  1 hugh hugh 911212544 Mar  8 16:49 xenial-desktop-amd64.iso.zs-old
hugh@xenial-laptop:~/Xenial$ 
```

---

### Post by sudodus on 2016-03-10
Welcome as an iso-tester :KS

---

