---
title: "Burning problems..."
date: 2005-05-22
forum: General Help
---

### Post by Joey French on 2005-05-22
When I try to burn a DVD in Kubuntu amd 64, I get this debugging error in k3b...

Devices
-----------------------
SONY DVD RW DW-D26A JYS1 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R16; RAW/R96P; RAW/R96R]

System
-----------------------
K3b Version: 0.11.23
KDE Version: 3.4.0
QT Version:  3.3.3
Kernel:      2.6.10-5-amd64-k8

growisofs
-----------------------
Executing 'builtin_dd if=/tmp/kde-joey/k3b_image.img of=/dev/hdc obs=32k seek=0'
/dev/hdc: engaging DVD-R DAO upon user request...
/dev/hdc: reserving 1964928 blocks
/dev/hdc: "Current Write Speed" is 8.2x1385KBps.
     32768/4024141824 ( 0.0%) @0.0x, remaining 12280:36
     32768/4024141824 ( 0.0%) @0.0x, remaining 20467:40
   1277952/4024141824 ( 0.0%) @0.3x, remaining 682:02
   1277952/4024141824 ( 0.0%) @0.0x, remaining 839:26
   1277952/4024141824 ( 0.0%) @0.0x, remaining 1049:17
   1277952/4024141824 ( 0.0%) @0.0x, remaining 1206:41
   1277952/4024141824 ( 0.0%) @0.0x, remaining 1364:05
   1277952/4024141824 ( 0.0%) @0.0x, remaining 1573:56
   1277952/4024141824 ( 0.0%) @0.0x, remaining 1731:20
   1277952/4024141824 ( 0.0%) @0.0x, remaining 1888:44
   1277952/4024141824 ( 0.0%) @0.0x, remaining 2098:35
   1277952/4024141824 ( 0.0%) @0.0x, remaining 2255:59
   1277952/4024141824 ( 0.0%) @0.0x, remaining 2413:23
   2588672/4024141824 ( 0.1%) @0.3x, remaining 1294:35
   2588672/4024141824 ( 0.1%) @0.0x, remaining 1372:16
   2588672/4024141824 ( 0.1%) @0.0x, remaining 1449:57
   2588672/4024141824 ( 0.1%) @0.0x, remaining 1553:31
   2588672/4024141824 ( 0.1%) @0.0x, remaining 1631:11
   2588672/4024141824 ( 0.1%) @0.0x, remaining 1708:52
   2588672/4024141824 ( 0.1%) @0.0x, remaining 1812:26
   2588672/4024141824 ( 0.1%) @0.0x, remaining 1890:06
   2588672/4024141824 ( 0.1%) @0.0x, remaining 1967:47
   2588672/4024141824 ( 0.1%) @0.0x, remaining 2071:21
   2588672/4024141824 ( 0.1%) @0.0x, remaining 2149:02
   2588672/4024141824 ( 0.1%) @0.0x, remaining 2226:42
   2588672/4024141824 ( 0.1%) @0.0x, remaining 2330:16
   2588672/4024141824 ( 0.1%) @0.0x, remaining 2407:57
   2588672/4024141824 ( 0.1%) @0.0x, remaining 2485:37
   2588672/4024141824 ( 0.1%) @0.0x, remaining 2589:11
   2588672/4024141824 ( 0.1%) @0.0x, remaining 2666:52
   2588672/4024141824 ( 0.1%) @0.0x, remaining 2744:33
   2588672/4024141824 ( 0.1%) @0.0x, remaining 2848:07
:-( unable to WRITE@LBA=4f0h: Input/output error
:-( write failed: Input/output error
/dev/hdc: flushing cache
:-[ FLUSH CACHE failed with SK=2h/ASC=04h/ACQ=01h]: Resource temporarily unavailable
:-[ SYNCHRONOUS FLUSH CACHE failed with SK=2h/ASC=04h/ACQ=01h]: Resource temporarily unavailable

growisofs comand:
-----------------------
/usr/bin/growisofs -Z /dev/hdc=/tmp/kde-joey/k3b_image.img -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1964913 -use-the-force-luke=dao:1964913 -dvd-compat -speed=8 


Could someone explain what the problem is?

Thanks!
Joey

---

### Post by Joey French on 2005-05-22
Anyone?

---

### Post by Joey French on 2005-05-23
Hello (echo)....

---

### Post by nocturn on 2005-05-23
Do you have DMA enabled on that drive?

hdparl -I <device> 

will tell you

---

### Post by Joey French on 2005-05-23
Yes, I used the Howto and enabled DMA for my DVD drive.

---

### Post by Joey French on 2005-05-24
No one?

---

### Post by Joey French on 2005-05-28
I'm not giving up yet...

---

### Post by DutchLau on 2005-05-28
Have you tried using a different burning program, such as NeroLinux to see if it give you the same error message?

---

### Post by Joey French on 2005-05-28
Hmmm, no I haven't. Is it freeware or where can I get it? I will have to do a search and see what's up...

---

### Post by Joey French on 2005-05-28
Okay, after searching, I have found it is only available in 32 bit version so far.

So, anybody got any idea why k3b won't burn a dvd for me?

---

### Post by Joey French on 2005-05-29
Back to the top.

---

### Post by ozeroc on 2005-06-02
Have you tried different media?  I'm having the same problem myself, BTW...


Oz


I'm going to check out NeroLinux

---

### Post by tread on 2005-06-02
Try burning it at a really low speed? k3b usually does a good job of autodetection, but it can't be foolproof ..

---

### Post by osde.info on 2005-07-22
I'm having same / similar problems with a Pioneer burner

CLOSE SESSION failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable

does anyone know the solution yet ?

---

### Post by rkn on 2005-07-22
**$ growisofs -use-the-force-luke=dao -dvd-compat -Z /dev/hdX=someiso.iso -speed=**2
Where "/dev/hdx" is the burning device and "someiso.iso" is the path to the iso file.

Note:
If you are using ide-scsi emulation your device is probably /dev/sc0.
"speed" is N*1385KBps, so 2 is like 16X
You need to use "-overburn" if you are burning more than 4.7GB (4.377 real GB) 

-Bob

---

### Post by ispmarin on 2005-09-05
[QUOTE=rkn]**$ growisofs -use-the-force-luke=dao -dvd-compat -Z /dev/hdX=someiso.iso -speed=**2
Where "/dev/hdx" is the burning device and "someiso.iso" is the path to the iso file.

Note:
If you are using ide-scsi emulation your device is probably /dev/sc0.
"speed" is N*1385KBps, so 2 is like 16X
You need to use "-overburn" if you are burning more than 4.7GB (4.377 real GB) 

-Bob[/QUOTE]
 Same problem here, but with a ordinary lg recorder... no error message. But when i try to record a cd using a common user, k3b does not find any device. As root, it can burn correctly.
So...?
Sorry: I am running a athlon amd64 3000XP+, Asus A8N-SLI, hoary 5.04, with a lg recorder 16x10x40x.

---

### Post by Ferio on 2005-10-23
I've got this input/output error using K3b under GNOME in 386, it can't burn DVDs nor CDs; in fact, it can't do it using K3b, GNOMEBaker, Graveman, GCombust, NeroLINUX... I could when I was using Ubuntu 5.04, but not anymore with 5.10. Any idea anyone? It's broken 8 double layer DVDs yet, and they're not cheap...

---

### Post by vyusseem on 2005-11-28
I have exactly same problem. I can burn CDs but not DVD. I've tried to many types of media, I've tried running k3b as root, all same. 
Please someone!
This problem seems to be very frequent, and a lot of people having it. Lets fix it!
Here is my log:

K3b Version: 0.12

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-10-386
Devices
-----------------------
LG CD-ROM CRD-8520B 1.00 (/dev/hdc, ) at /media/cdrom0 [CD-ROM] [Error] [None]

DVD+R/RW DX082D 11SB (/dev/hdd, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD+R; DVD+RW] [DVD-ROM; DVD+RW; DVD+R; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96R; RAW/R16; RAW/R96R]
K3b
-----------------------
Size of filesystem calculated: 1654011

Used versions
-----------------------
mkisofs: 2.1-unofficial-iconv
growisofs: 5.21

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdd obs=32k seek=0'
/dev/hdd: "Current Write Speed" is 8.2x1385KBps.
     32768/3387414528 ( 0.0%) @0.0x, remaining 10337:28
   1540096/3387414528 ( 0.0%) @0.3x, remaining 329:46
.....
392429568/3387414528 (11.6%) @0.0x, remaining 35:14
:-( unable to WRITE@LBA=2ec80h: Input/output error
:-( write failed: Input/output error
/dev/hdd: flushing cache
:-( unable to FLUSH CACHE: Input/output error
:-( unable to SYNCHRONOUS FLUSH CACHE: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/hdd=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1654011 -dvd-compat -speed=4

---

### Post by vyusseem on 2005-11-30
^

---

### Post by boakes on 2005-11-30
I too have trouble.  I can burn cd's but can't burn DVD's.  No it's not the media or the drives.  They both work under windows with zero problems.  Yes, dma is enabled on them also.

---

### Post by locutuz on 2005-12-02
[QUOTE=Ferio]I've got this input/output error using K3b under GNOME in 386, it can't burn DVDs nor CDs; in fact, it can't do it using K3b, GNOMEBaker, Graveman, GCombust, NeroLINUX... I could when I was using Ubuntu 5.04, but not anymore with 5.10. Any idea anyone? It's broken 8 double layer DVDs yet, and they're not cheap...[/QUOTE]

Me too! Burning under 5.04 worked like a charm, after upgranding to 5.10 Gnomebaker and Graveman both can't burn CD's anymore

---

### Post by ymeyer on 2005-12-08
[QUOTE=locutuz]Me too! Burning under 5.04 worked like a charm, after upgranding to 5.10 Gnomebaker and Graveman both can't burn CD's anymore[/QUOTE]


I have the same problem. It is not related to the Gui interfaces but more generally to mkisofs used by all cited programms.
Is somebody able to burn DVD over 2 GB with breezy?

---

### Post by osde.info on 2005-12-08
are you saying you CAN burn DVDs that are less than 2G ? 

in which case it might be a file system issue !

this is also an issue in CentOS 4.2 (kernel 2.6.9-22.0.1.EL)

---

### Post by sal on 2005-12-22
yes, i am having the same problem with mkisofs. when i used 5.04 there where no prolems. no ever since 5.10 cant burn anything. i see other posters posting same problems, yet there seems to be no fix. i hope they get it worked out soon. its really getting frustrating.

---

### Post by Fridericus on 2005-12-22
I've been having problems also, but with CD burning.

I installed 5.10 a few days after it was released, but not until today did I try to burn anything.

I have tried to burn in Nautilus and K3b both have completed the burn process without any errors but when I try to read from the CD either the file is damaged or the CD-Drive can not detect a file system on the disc. I tried burning a disc in K3b and also made K3b verify the written data, this failed and K3b informed me that it could not read the ISO9660 file system.

Neither Ubuntu nor Windows XP can read two of the three discs. One is readable but the file (in this case a video file) is damaged, the video will start to play but but out after 2-3 seconds.

Very annoying, I had no problems in 5.04 (still using the same burner). :???:

---

### Post by sal on 2005-12-23
[QUOTE=Fridericus]I've been having problems also, but with CD burning.

I installed 5.10 a few days after it was released, but not until today did I try to burn anything.

I have tried to burn in Nautilus and K3b both have completed the burn process without any errors but when I try to read from the CD either the file is damaged or the CD-Drive can not detect a file system on the disc. I tried burning a disc in K3b and also made K3b verify the written data, this failed and K3b informed me that it could not read the ISO9660 file system.

Neither Ubuntu nor Windows XP can read two of the three discs. One is readable but the file (in this case a video file) is damaged, the video will start to play but but out after 2-3 seconds.

Very annoying, I had no problems in 5.04 (still using the same burner). :???:[/QUOTE]


yes, thats the crazy part, i had no problem in 5.04 ether, upgraded to 5.10, and problems ever since. i have seen a lot of threads saying it has something to do with the included version of mkisofs but i don't know what to think.

i hope they work it out though, if not in breezy hopefully in dapper.

---

### Post by maltje on 2006-01-31
same probs here.
Anyone for a solution yet?
Even with nautilus I can't get it burning.
:???:

---

### Post by snoobab on 2006-02-06
'lo all,

i have been having similar probs with burning dvd+-r on suse 10 and have eventually found the solution -- i thought that maybe it could help you out.

the error i was getting is:

:-[ CLOSE SESSION failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable

where the dvd would be written ok but not closed so it would then just be picked up as a blank disc when re-inserted ](*,) 


the problem it seems is with the version of growisofs, suse 10 ships with 5.21.4.10.8-9, which you can version 6.1 for from [DVD+RW/+R/-R[W] for Linux]("http://fy.chalmers.se/~appro/linux/DVD+RW/")

i updated my copy and my dvd isos now roast beautifully \\:D/

i hope this helps some, if not all, of you.

---

### Post by casfindad on 2006-04-17
[QUOTE=snoobab]'lo all,

i have been having similar probs with burning dvd+-r on suse 10 and have eventually found the solution -- i thought that maybe it could help you out.

the error i was getting is:

:-[ CLOSE SESSION failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable

where the dvd would be written ok but not closed so it would then just be picked up as a blank disc when re-inserted ](*,) 


the problem it seems is with the version of growisofs, suse 10 ships with 5.21.4.10.8-9, which you can version 6.1 for from [DVD+RW/+R/-R[W] for Linux]("http://fy.chalmers.se/~appro/linux/DVD+RW/")

i updated my copy and my dvd isos now roast beautifully \\:D/

i hope this helps some, if not all, of you.[/QUOTE]

snoobab, would you please post specific instructions on how you installed  dvd+rw-tools-6.1? I downloaded from [http://fy.chalmers.se/~appro/linux/DVD+RW/tools/]("http://fy.chalmers.se/~appro/linux/DVD+RW/tools/")
, and extracted, but typing "sudo ./configure" in this new directory gave me this message:
```
sudo: ./configure: command not found
```

I found some installation instructions on another page [here]("http://www.linuxfromscratch.org/blfs/view/cvs/multimedia/dvd-rw-tools.html").

These instructions are so different, from the usual
sudo ./configure
sudo make
sudo checkinstall

I use for compiling, that I'd like to find out what you did before I try this new method. Thanks!

casfindad

P.S. I'm hoping your suggestion works for me. I can't write on a dvd-rw disk that's been re-formatted, nor can I burn a video DVD that will play till the end using K3b or any other ripper/burner.

---

### Post by casfindad on 2006-04-17
Just a follow-up for snoobab,

When you updated to 6.1, did it overwrite the old version of growisofs etc.? Should I back up or move the old version before installing 6.1? Thanks.

---

### Post by sniffass on 2006-05-07
[QUOTE=casfindad]snoobab, would you please post specific instructions on how you installed  dvd+rw-tools-6.1? I downloaded from [http://fy.chalmers.se/~appro/linux/DVD+RW/tools/]("http://fy.chalmers.se/~appro/linux/DVD+RW/tools/")
, and extracted, but typing "sudo ./configure" in this new directory gave me this message:
```
sudo: ./configure: command not found
```
[/QUOTE]


You need to run "sudo apt-get install build-essential" and then run the ./configure  and other commands.

---

### Post by zasten on 2006-05-07
Lots of people with the same problem...

Me too, I've read that 5.10 (breezy) has problems with CD burning. ADMIN HELLO!!!!! 

What is the story do we have to upgrade to dapper before we can get CD burning to work?

(just noticed that this is in the 5.04 forum but it doesnt really matter)

I've tried many progs, graveman, nautilus, XCDroast, k3B all the programs can see my CDR drive but no burning session ever starts. I can post my dmesg (or any other output you can think of) but I think that this topic is being IGNORED! 

I mean the whole point of ubuntu is to have an easy install and almost no hardware issues!!!! 

This is exactly the sort of thing that turn users off, especially new users. The question becomes - Hey it works in windoze, why not in Ubuntu XXXX!?!?

As far as I know this release will stay supported for a very long time (err at least 12 months) THIS ISSUE MUST BE ADRESSED!!!

/thanks for reading my rave. Now post some suggestions! (please, or people will defect to other operating systems / distros)

---

### Post by MrMichaelWill on 2006-07-24
The problem lies in either the kernel or growisofs which is the tool that k3b and other burner applications use to write the image to the DVD. The only way I got it to work is to use 'automatix' which replaces the /etc/apt/resources.list with a better list of repositories and updates a lot of packages. Note that you can only use it if you are living in the free world. Residents of the U.S.A. cannot use it because of their local laws prohibiting certain software to be used.

[http://applications.linux.com/article.pl?sid=06/03/12/209257&tid=47](http://applications.linux.com/article.pl?sid=06/03/12/209257&tid=47)

---

