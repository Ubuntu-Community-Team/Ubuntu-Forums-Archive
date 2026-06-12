---
title: "DVD duplication"
date: 2005-10-17
forum: General Help
---

### Post by InsomniacUK on 2005-10-17
Are there any programs out there that can do DVD duplication? Just a straight 1:1 DVD copy? I found plenty of programs that can do CD copying, and DVD data burning, and CD image burning and DVD image burning and pretty much every disc operation you might want or need, *except* a straight forward DVD copy.

Can anyone recommend some software?

---

### Post by bluck on 2005-10-17
[QUOTE=InsomniacUK]Are there any programs out there that can do DVD duplication? Just a straight 1:1 DVD copy? I found plenty of programs that can do CD copying, and DVD data burning, and CD image burning and DVD image burning and pretty much every disc operation you might want or need, *except* a straight forward DVD copy.

Can anyone recommend some software?[/QUOTE]

thats because copying a dvd is not as straight forward as one might think.  in most cases, especially if you dont have a dual layer burner, your store-bought dvd contains more data than your writeable dvd can store.

usually, you need to rip the dvd to file, then compress the .vob files further using your favourite codec.  after that you would create an image that you can burn to disc.

having said all that,  dvdxcopy does a nice job of it :)

---

### Post by mr_manny on 2005-10-17
found following link to be a good guide:
[http://www.troubleshooters.com/linux/coasterless_dvd.htm](http://www.troubleshooters.com/linux/coasterless_dvd.htm)

---

### Post by Malphas on 2005-10-18
Are there any MPEG2 encoders that run under Linux that compare to the likes of CCE where quality is concerned?

---

### Post by bionnaki on 2005-10-18
[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)

---

### Post by manicka on 2005-10-18
[QUOTE=bionnaki][http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)[/QUOTE]

Mr Bass' how-to is for hoary and won't work in breezy

InsomniacUK, what type of DVD are you trying to duplicate?

For a pure rip of  a video dvd I use dvdbackup. it's a command line program but works brilliantly.

To make copies of an unencrypted dvd I've used k3b and nautilus (right click on the mounted disc and choose 'copy disc')

If you want to copy an encrypted dual layer dvd to a single layer then there's a variety of solutions. I prefer dvdshrink with wine, but there are native apps that do a reasonable job to.

---

### Post by maqi on 2005-10-18
[QUOTE=InsomniacUK]Are there any programs out there that can do DVD duplication? Just a straight 1:1 DVD copy? I found plenty of programs that can do CD copying, and DVD data burning, and CD image burning and DVD image burning and pretty much every disc operation you might want or need, *except* a straight forward DVD copy.[/QUOTE]

For some strange reason I thought a 1:1 copy WAS an image :rolleyes: Doh!

If you're trying to copy encrypted and/or dual layer to standard DVD+/-R then, unfortunately, the Linux world is not so easy while the Windoze world has a heap of excellent solutions which won't leave you with a 10:1 coaster to DVD ratio. The DVDshrink option under wine sounds good. 

I haven't tried it yet, but does anyone know how these sorts of apps run in vmware?

---

### Post by bionnaki on 2005-10-18
> Mr Bass' how-to is for hoary and won't work in breezy

oh...I didnt notice any difference - seems like it would be the same method, no? 

do you know of any other instructions for using dvdshrink (which rocks) via wine? thanks!

---

### Post by felipe on 2005-10-18
sudo apt-get install thoggen

it worked for me

---

### Post by manicka on 2005-10-18
[QUOTE=bionnaki] 
do you know of any other instructions for using dvdshrink (which rocks) via wine? thanks![/QUOTE]

[http://ubuntuforums.org/showthread.php?t=78611](http://ubuntuforums.org/showthread.php?t=78611)

---

### Post by alterego125 on 2005-10-19
I followed the instructions on [https://wiki.ubuntu.com/dvdshrink]("https://wiki.ubuntu.com/dvdshrink")

I've tried opening a disc in DVD shrink and get the error msg: "DVD Shrink encountered an error and cannot continue". Failed to read file "E:\" No access to memmory location. Any ideas?

So what are the native linux programs that can do the job? Is there a DVDshrink for linux or something similar?

What does one do after dvdbackup? Would one use DVD shink? Will that burn to a DVD under linux?

---

### Post by manicka on 2005-10-20
[QUOTE=alterego125]
What does one do after dvdbackup? Would one use DVD shink? Will that burn to a DVD under linux?[/QUOTE]
did you instal libdvdcss2?
did you use winecfg to autodetect your drives.
After dvdbackup you can analyse those backed up  files with dvdshrink by using the 'Open Files' button instead of 'Open disc'.
I get dvdshrink to backup to an iso image then burn it with the nautilus burn tools or k3b
You can burn the dvdbackup files to a disc if you have a dual layer burner, otherwise you need dvdshrink or some other native app.
There's lots of alternatives available for Linux (Thoggen, Xdvdshrink  I hear are quite good) but none of them do the same job as dvdshrink, so I put up with the hassles of getting it working and using it in Wine.

---

### Post by BLTicklemonster on 2005-10-26
[QUOTE=felipe]sudo apt-get install thoggen

it worked for me[/QUOTE]
Sweet. do that, then from the terminal, type thoggen, and bam. 

I think dvdshrink will work with the files it makes from what I hear. Apparently dvdshrink won't rip from a dvd in linux easily, so ripping then burning seems to be the way to go. It said it would be hours and hours, so I think I'll rip it over night, lol. 

Thanks!

---

### Post by cvmostert on 2005-10-29
I have a dvd with my marriage ceremony on it and want to copy it for my parents... the problem is that cd/dvd creator asks for a empty dvd with 46??? 4.6 GB free..

the thing is, the dvd is a 4.7 GB writable... so it should work... i have had this problem before and had to copy it in windows.

does linux read the space left on the drives different?

Thanx in advance

---

### Post by manicka on 2005-10-29
Which dvd is giving you the error message. The blank one or your marriage ceremony dvd? 

Which program are you trying to use to complete the job?

---

### Post by neuschnee on 2005-11-03
[QUOTE=Malphas]Are there any MPEG2 encoders that run under Linux that compare to the likes of CCE where quality is concerned?[/QUOTE]
No.

...and DVDShrink does not even compare to CCE (Cinema Craft Encoder). I think CCE is almost universally accepted as the #1 MPEG-2 encoder. DVDShrink works, but it's not quality. There's a reason why by 'scene rules' DVDshrinked DVDR releases are nuked. :P

A simple way to duplicate DVD's is to split the IFO's (with a program like Ifoedit for Windows). No loss in quality, but two DVD's. There are a few different guides for how to do this with Ifoedit, one is found here: [http://www.doom9.org/mpg/ifoedit-2dvdrs.htm](http://www.doom9.org/mpg/ifoedit-2dvdrs.htm). I would be surprised if Ifoedit worked poorly in WINE.. though I haven't tried it myself, yet.

---

### Post by cvmostert on 2005-11-10
[QUOTE=manicka]Which dvd is giving you the error message. The blank one or your marriage ceremony dvd? 

Which program are you trying to use to complete the job?[/QUOTE]


the blank dvd gives the error... gnomebaker tells me that i need a dvd with more free space? or  am i doing something wrong?

---

### Post by manicka on 2005-11-10
[QUOTE=cvmostert]the blank dvd gives the error... gnomebaker tells me that i need a dvd with more free space? or  am i doing something wrong?[/QUOTE]
I'd suggest installing and using k3b. I've never had much success with gnomebaker

---

### Post by cvmostert on 2005-11-10
will do, seems like the only sollution... or nerolinux, not free though! :-(

---

### Post by bionnaki on 2005-11-10
never had luck with gnomebaker either
k3b rules.

---

### Post by cvmostert on 2005-11-11
i installed nerolinux and it also tells me that the empty disk can only hold 4490MB!

now i will try k3b...

---

### Post by cvmostert on 2005-11-11
yes, k3b wants me to put in a double layer dvd! is it not possible to write 4.6 GB of data on a DVD-R disc? I am allmost certain that i have done it in win...

---

### Post by manicka on 2005-11-11
What happens if you choose 'Copy DVD' from the Tools menu in k3b?

---

### Post by cvmostert on 2005-11-11
I dont want to copy a DVD, I have the data on my hard drive... but ill try anyhow..

---

### Post by cvmostert on 2005-11-11
no, its only to copy another dvd... maby the programs needs too much space to close the session?

---

### Post by rcerreto on 2005-11-11
dvdrip, which is actually a perl front-end for transcode, delivers very good funcionalities. I'd rate it very close to dvdshrink under windows.

---

### Post by jeremy on 2005-11-12
xdvdshrink is great!
[http://dvdshrink.sourceforge.net](http://dvdshrink.sourceforge.net)

---

### Post by cvmostert on 2005-11-16
[QUOTE=manicka]What happens if you choose 'Copy DVD' from the Tools menu in k3b?[/QUOTE]


even with k3b it does not want to work... and copy dvd ... this is with another data dvd i wrote on a windows pc... does not want to work... wants me to put in a cd with more than 4490mb of space??? 

please help. could it be a hardware problem?

---

### Post by darknuala on 2005-11-16
DVDshrink gives you the option to re-author the DVD, take out some of the extra languages, extras, I don't care for menus, so thats how i do most of mine, it cuts the file size down alot.

---

### Post by dudus on 2006-02-12
[QUOTE=manicka]If you want to copy an encrypted dual layer dvd to a single layer then there's a variety of solutions. I prefer dvdshrink with wine, but there are native apps that do a reasonable job to.[/QUOTE]

I just backuped my files to hd. Could you say the name of some of these native apps as I can't use wine. is transcode an ffmpeg two of these? I just can't seem to make it work

---

