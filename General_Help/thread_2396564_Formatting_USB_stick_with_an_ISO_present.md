---
title: "Formatting USB stick with an ISO present"
date: 2018-07-18
forum: General Help
---

### Post by jgwphd on 2018-07-18
I have Ubuntu 18.04 on a USB stick. It worked fine while I need it. Now, I'd like to reclaim all the space on the USB stick (just like when I bought it from the store). When I try to format the drive I get errors out of nautilus (even in supervisor mode). Is there some simple and quick utility/tool that allows me to just wipe the UBS stick clean and I don't have to deal with partitions or any other technicalities? ...I just want to get the USB drive back to when I brought it home from the store? ....just back-up storage.  

Thanks for any recommendations!

---

### Post by The Cog on 2018-07-18
gparted is probably the easiest tool to use. Select the right device (drop-down on the top left) and then menu Device -> Create partition table. You wand an msdos type partition table.

Don't do it to the wrong device!

---

### Post by strixtux on 2018-07-18
Be careful, some USB sticks can't be formatted too often. It might be better to simply remove the files by deleting them piecemeal.

---

### Post by yancek on 2018-07-18
You can use the dd command if you have a Linux OS available but the simplest method is using GParted to create a new partition table.  You don't indicate what you did to format the usb or what errors you got.  If you don't want anything saved from the usb, the method of using GParted is the simplest.

---

### Post by sudodus on 2018-07-18
> **The Cog said:**
> gparted is probably the easiest tool to use. Select the right device (drop-down on the top left) and then menu Device -> Create partition table. You wand an msdos type partition table.

Don't do it to the wrong device!

+1

Try first with **gparted**.

If still problems, you can install and use **mkusb** and select the menu option 'restore to a Standard storage device'. It will wipe the first mibibyte (which will effectively remove data, that might confuse gparted and other tools). After that it will create an MSDOS partition table and a partition with a FAT32 file system (which is a de facto standard for USB sticks).

If you want another partition structure or another file system, you can let mkusb 'wipe 1 (the first) Mibibyte', and after that use **gparted** to create what you want.

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[help.ubuntu.com/community/mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by monkeybrain20122 on 2018-07-18
> **yancek said:**
> You can use the dd command if you have a Linux OS available but the simplest method is using GParted to create a new partition table.  You don't indicate what you did to format the usb or what errors you got.  If you don't want anything saved from the usb, the method of using GParted is the simplest.

Definitely not dd if op doesn't know about gparted! 

gparted is not installed by default, so

```
sudo apt install gparted
```

---

### Post by C.S.Cameron on 2018-07-18
GParted seems to me to have trouble unmounting ISO9660 partitions.
**mkusb** always works for me in the "restore to a Standard storage device" mode.

---

### Post by jgwphd on 2018-07-18
This is just an observation so please don't get mad at me. I find it "interesting" that doing something as simple as taking an existing USB drive (and not caring what is on it) and clearing it off to an empty (new from the store) state requires "geek level skills". I was working with a friend of mine (non-geek) and in the course of our discussion I told him to grab a USB stick to back up some files but there wasn't enough space because an .iso partition was there. We tried to format it (talking over the phone) and it became obvious that formatting wouldn't work from nautilus if the USB drive had partitions (I have also run into formatting USB drive problems in the past with read/write permissions). To me this is an Ubuntu usability issue. Why the need for geek level skills to do some simple house cleaning chores such as creating a back-up USB drive from old drives (laying around your office) or restoring no longer needed drives to new from the store status (without a lot of investigative work and option choices that are meaningless to the non-geek community). There should be a simple capability that says "restore drive to new" with a single click and a warning to proceed. Using tools such as gparted by non-geek people (even with someone directing over the phone) seems risky and the wrong answer. My 2 cents.   ...and I do appreciate all the help and suggestions. Many Thanks. I bet I am not the first one to mention this situation and I feel there is likely a simple tool (like Etcher) somewhere out there and hopefully some one knows about it.    :-)

---

### Post by monkeybrain20122 on 2018-07-18
> **jgwphd said:**
> This is just an observation so please don't get mad at me. I find it "interesting" that doing something as simple as taking an existing USB drive (and not caring what is on it) and clearing it off to an empty (new from the store) state requires "geek level skills". I was working with a friend of mine (non-geek) and in the course of our discussion I told him to grab a USB stick to back up some files but there wasn't enough space because an .iso partition was there. We tried to format it (talking over the phone) and it became obvious that formatting wouldn't work from nautilus if the USB drive had partitions (I have also run into formatting USB drive problems in the past with read/write permissions). To me this is an Ubuntu usability issue. Why the need for geek level skills to do some simple house cleaning chores such as creating a back-up USB drive from old drives (laying around your office) or restoring no longer needed drives to new from the store status (without a lot of investigative work and option choices that are meaningless to the non-geek community). There should be a simple capability that says "restore drive to new" with a single click and a warning to proceed. Using tools such as gparted by non-geek people (even with someone directing over the phone) seems risky and the wrong answer. My 2 cents.   ...and I do appreciate all the help and suggestions. Many Thanks. I bet I am not the first one to mention this situation and I feel there is likely a simple tool (like Etcher) somewhere out there and hopefully some one knows about it.    :-)

Actually it is very simple. You can use the disk utility without installing gparted. Disk utility has simple one click way to reformat (though of course like all such tools you have to be careful in identifying the correct device) 

I started Ubuntu in 2010 with little experience with computers in general and using gparted to do things with usb drive was easy as a piece of cake. I had a bunch of usb drive and always creating and deleting oses with no issue. Doing partition and creating dualboots was a lot easier with Linux than with Windows for me then (I remember my brother was trying to make a dualboot between Windows 7 and XP and it was really complicated, now with UEFI and what not it is diffult no matter what you use as long as Windows is involved, multibooting with Linux distros is still a piece of cake)

But when you ask a question in a forum people would give you answers at different levels, some maybe overkill and others may not be appropriate to beginners (such as dd) So it may be confusing to new users. Personally I try to recommend solutions using software that either come installled by default or can be installed easily from repo (without ppa or downloading from somewhere) even though they may not be the best or most powerful for all possible use cases.

---

### Post by monkeybrain20122 on 2018-07-18
> **C.S.Cameron said:**
> GParted seems to me to have trouble unmounting ISO9660 partitions.
**mkusb** always works for me in the "restore to a Standard storage device" mode.

Not for me.

---

### Post by monkeybrain20122 on 2018-07-18
As an experiment I just reformated a live usb ( what you called a usb with an ISO present) with nautilus to FAT32, it went smoothly with no issue.

---

### Post by jgwphd on 2018-07-18
I have been doing this since Ubuntu 8.04. I help family and friends with Ubuntu. This has always been a problem and it seems that after all these years there should be a simple utility for non-geeks to simply handle what I would consider a routine chore. Taking non-geeks into areas (e.g. gparted, disks) where they don't even understand what they are looking at, can cause serious problems and awful recovery situations for trying to do something as simple as restoring an USB drive to a "store bought condition". I simply don't understand why it has to be this complicated. I am hoping someone can refer me to a tool that reduces the risks of a mistake (for example, have you used Etcher for creating boot-able devices? ...it's easy and most excellent). Maybe there should be an option on Nautilus says "restore to new" when a USB drive is detected ..or something like that.

BTW, With Nautilus using 18.04, I get  'error formatting volume. This  partition cannot be modified because it contains a partition table:  please reinitialize layout of the whole device". (udisks-error-quark,  11)"

---

### Post by monkeybrain20122 on 2018-07-18
> **jgwphd said:**
> I have been doing this since Ubuntu 8.04. I help family and friends with Ubuntu. This has always been a problem and it seems that after all these years there should be a simple utility for non-geeks to simply handle what I would consider a routine chore. Taking non-geeks into areas (e.g. gparted, disks) where they don't even understand what they are looking at, can cause serious problems and awful recovery situations for trying to do something as simple as restoring an USB drive to a "store bought condition". I simply don't understand why it has to be this complicated. I am hoping someone can refer me to a tool that reduces the risks of a mistake (for example, have you used Etcher for creating boot-able devices? ...it's easy and most excellent). Maybe there should be an option on Nautilus says "restore to new" when a USB drive is detected ..or something like that.


Reformat in Nautilus is "restore to new". I don't see how disk utility is "geeky", if you can make a live usb then I doubt that you would have a lot of issue using it. Gparted does a lot more than just  reformatting and I find it a lot more straight forward than the Windows tool that basically does the same thing.

Edited: never used etcher. I use [multisystem]("https://sourceforge.net/projects/multisystem/"). It can create a live usb with multiple OSes and is very easy to use.

---

### Post by jgwphd on 2018-07-18
If reformatting in Nautilus is "restore to new" then why do I get; 'error formatting volume. This   partition cannot be modified because it contains a partition table:   please reinitialize layout of the whole device". (udisks-error-quark,   11)". If nautilus knows I want "restore to new" then why is it talking about partitions and reinitialize layout of the whole device? What does that mean to a non-geek? This is where you loose the non-geeks?   ...in my mind this is an Ubuntu usability issue.  And I appreciate the discussion and thanks for your assistance.

---

### Post by monkeybrain20122 on 2018-07-18
> **jgwphd said:**
> If reformatting in Nautilus is "restore to new" then why do I get; 'error formatting volume. This   partition cannot be modified because it contains a partition table:   please reinitialize layout of the whole device". (udisks-error-quark,   11)". If nautilus knows I want "restore to new" then why is it talking about partitions and reinitialize layout of the whole device? What does that mean to a non-geek? This is where you loose the non-geeks?   ...in my mind this is an Ubuntu usability issue.  And I appreciate the discussion and thanks for your assistance.

I don't know. I just did an experiment by reformatting a live usb. No problem. How did you create your liveusb?

---

### Post by jgwphd on 2018-07-18
The USB drive was new and I put 17.04 on it awhile back using Etcher (not sure but probably using Ettcher). I am having trouble comprehending why Nautilus would even care what is on the drive if I want it "restored to new". ...Just do it.     :-)      I have it plugged in now and tried again with nautilus and got the same error. Gparted info is shown in the figure[ATTACH=CONFIG]280444[/ATTACH]

---

### Post by jgwphd on 2018-07-18
Nautilus info is attached here. Note free space is "unknown"  [ATTACH=CONFIG]280446[/ATTACH]

---

### Post by monkeybrain20122 on 2018-07-18
Interesting, I think it depends on how the liveusb is created. I have created one (ubuntu 18.04) with multisystem. Here are some screenshots. There is no issue reformatting with nautilus (actually it just invokes disk utilities) On the other hand I have created another live usb with dd and one more with the ubuntu startup disk creator and got the same errors and screenshots like yours. So it seems that the startup disk creator and etcher use dd in their backend, and this may be the cause of the problem since dd alters the structure of the usb rather than just filling it with contents and you may have to use dd to restore the usb drive (one reason that I don't recommend it) Also see [https://askubuntu.com/questions/821463/usb-not-working-after-running-dd](https://askubuntu.com/questions/821463/usb-not-working-after-running-dd)

sudodus and C.S.Cameron are the experts and they will be able to give you much better explanations. But to your point that Ubuntu lacks non geeky tools to format usb, making a usb with dd or its front ends is a geeky activity, nautilus is a non geeky option (actually it invokes disk utility) quite adequate for non geeky tasks by non geeks who I doubt would need to format a liveusb created by dd.

---

### Post by jgwphd on 2018-07-18
Monkeybrain20112, I am glad you are able to recreate the problem. One thing to note is that gparted does say it is an ISO9660. C.S.Cameron earlier in this thread said there were problems with ISO9660 "GParted seems to me to have trouble unmounting ISO9660 partition". As this discussion unfolds it seems the answer becomes steeped in jargon and dives to geeker and geeker activities to simply format a usb drive ...the instructions at ([https://askubuntu.com/questions/8214...ter-running-dd]("https://askubuntu.com/questions/821463/usb-not-working-after-running-dd")) are not something you want to send to non-geek family and friends.

Remember this is "simple format problem" and likely to occur to anyone. Consider: A non-geek at the office and a friend of his has an "old USB drive" he doesen't need and tells you, you can have it (instead of running to the store). He doesn't know what's on it, but suggests formatting it and everything will be ok (maybe he is worried about viruses if it was used on a microsoft computer) ..... and then you run into this. And if you look at the dd instructions you'll simply give up and go to the store. This in my opinion is a usability problem.

---

### Post by sudodus on 2018-07-19
mkusb was made in order to help people manage USB pendrives in a safe and easy way. Please install it and try it. I think it will solve your acute problem. There are details and links in post #5.

The long-term problem, to get such capability into the standard tools in Ubuntu may be more difficult, because the Ubuntu developers may not understand that there is a problem (for non-geeks).

---

### Post by HermanAB on 2018-07-19
Well, you can try fixing a USB device on Windows, which you will soon see will require Super Geek credentials.

On Linux, it is very easy if you know how: Zap the first bit of the disk with zeroes, then format as usual.  On Windows it is practically impossible - unless you have a virtual machine with Linux or BSD in it!

---

### Post by sudodus on 2018-07-19
> **sudodus said:**
> mkusb was made in order to help people manage USB pendrives in a safe and easy way. Please install it and try it. I think it will solve your acute problem. There are details and links in post #5.

The long-term problem, to get such capability into the standard tools in Ubuntu may be more difficult, because the Ubuntu developers may not understand that there is a problem (for non-geeks).

Sometimes there are more severe problems, for example that a USB pendrive is failing. It is suddenly read-only and you can no longer write to it. But sometimes there are other causes to the problem, so it is worthwhile to try in several ways before giving up. Maybe there is only confusion.

The following link and links from it can help analyze the problem, and if you are lucky, solve it, even when it looks like the drive is damaged beyond repair.

[Can't format my usb drive. I have already tried with mkdosfs and gparted](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

---

### Post by C.S.Cameron on 2018-07-19
> **HermanAB said:**
> Well, you can try fixing a USB device on Windows, which you will soon see will require Super Geek credentials.

I have bricked several multi-partition flash drives trying to format in Windows. I have not tried since Windows 10 has been out though. Now if I need to format anything with more than one partition I use Ubuntu, either GParted, Disks or mkusb. 

If the ISO partition is frozen in GParted, Disks can usually be used to unmount.

---

### Post by HermanAB on 2018-07-19
You can also do a 'lazy unmount' if it doesn't want come unstuck.  

For example: "umount -l /dev/sdb"

---

### Post by jgwphd on 2018-07-19
Thanks for the information. Sudodus, I was able to use mkusb to recover the USB drive free space (I think?) and reformat the usb drive with the ISO9660 partition. The drive has no markings on it and gparted and nautilus report the free space as unknown. I didn't find a storage size selection in mkusb (is that correct?). I selected restore to a standard storage device" in mkusb and gave it a name "extra-stor" Mkusb did its thing and when it was done the drive showed 2GB. How do I know that is the correct size (it's an old drive and might be)?  ...is there a storage size option somewhere or does it auto-magically figure out how much storage is available?

---

### Post by HermanAB on 2018-07-19
gparted will show you graphically what is going on.

---

### Post by sudodus on 2018-07-19
When selecting 'restore to a standard storage device', **mkusb** grabs all of the drive (except the first mibibyte) for a partition with the FAT32 file system. There is no storage size selection. If you want something more advanced, for example select the partition size(s), please use **gparted** after mkusb.

You can check the size of drive itself and the partition(s) with the following command lines,

```

sudo lsblk -f
sudo lsblk -m     # size in mibibytes, gibibytes (base 2)
sudo parted -ls   # size in megabytes, gigabytes (base 10)

```

---

### Post by jgwphd on 2018-07-19
Thanks for the information everyone!  sudokus... I like the mkusb tool and showed it to a non-geek friend of mine. But he says it's still scary/geeky.  :-) ...there is reluctance by non-geeks to use it if you don't know all the jargon and you get warning messages of clearing, overwriting, resetting, etc. jargon ...which means impending doom to the non-geeks if you proceed, microsoft has us all conditioned to PC catastrophes ..LoL.  I am not criticizing, but it would be nice if the tool had a "basic" function interface to just format any usb no matter what is on it, no questions asked (my original thread request) and then allow access to an advanced section for more sophisticated stuff. Maybe even add access to it from the Nautilus interface.   ...my 2 cents. 

BTW, I do like the ETCHER tool because it has a simple and as non-geeky as you can get interface, in my opinion.

---

### Post by sudodus on 2018-07-19
I see your point, @jgwphd.

Yes, maybe the second best alternative for non-geeks would be a separate dedicated tool with a graphical user interface for the purpose 'restore to a standard storage device', for example with the name 'format-usb'.

And the very best alternative might be to have access to it via (or built into) the file browser (Files alias nautilus in standard Ubuntu).

---

### Post by jgwphd on 2018-07-19
Again ....Many THANKS to everyone!!!!   You guys have been a great help.   :-)

---

