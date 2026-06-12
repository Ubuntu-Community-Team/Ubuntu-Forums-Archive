---
title: "Should I DBAN and reinstall?"
date: 2016-10-26
forum: General Help
---

### Post by daniel5800 on 2016-10-26
I installed Ubuntu on this computer about four years ago. I used it for about a year, and then I moved away. Somebody else used it for about 3 years. I recently moved back and began using this computer again. There are all kinds of problems with it. I think it may have malware, spyware, etc. On top of that, whenever I turn it off and turn it back on, I get a message saying something about a graphics card and that the system has to run in low graphics mode. When that happens, the only thing I can do is turn it off and back on for about an hour, with breaks in between, and then it finally starts up right. There are many other issues with it, too numerous to list.

Basically, what I want to do is: start from scratch. I want to use dban and wipe everything clean and install Ubuntu from a USB. What I did so far is: I downloaded dban onto the computer, then I put a USB stick in and moved it to that.

---

### Post by sudodus on 2016-10-27
Welcome to the Ubuntu Forums :-)

If you want to remove all traces of previous activity you can use DBAN, but if you are only going to use the computer yourself, it is probably enough to make a fresh installation and let it use the whole drive.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

The problems might also be caused by bad hardware, for example failing RAM (check with memtest) or failing HDD (check smart status with gnome-disks or smartctl (installed with smartmontools)).

---

### Post by bearlake on 2016-10-27
^^ what sudodus said.

How old is this computer and what are the specs?

---

### Post by kpatz on 2016-10-27
DBAN is used to securely wipe a drive if you're going to give/sell it to someone else and you don't want them getting at your old data.  If you're keeping the computer and drive, just reinstall and repartition the drive.

The issues you're seeing could be hardware or software related.  Do a fresh install and let it use the entire drive, erasing everything in the process and if you still have issues, start looking at the hardware.

---

### Post by daniel5800 on 2016-10-27
The computer is about four years old.  It's an HP Pavilion g series with a 19 inch screen. Laptop.

---

### Post by daniel5800 on 2016-10-27
I want to DBAN this computer. I am using it now, but I do not know how long I will be here for or if I will be able to take it with me if I leave. I want this thing wiped all the way clean. So, what is my next step?

---

### Post by yancek on 2016-10-27
There are a number of tutorials on using this software like the one at the link below.  If that doesn't suit you, just google it.

[https://tiptopsecurity.com/how-to-securely-wipe-your-hard-drive-with-dban-erase-your-data-for-good/](https://tiptopsecurity.com/how-to-securely-wipe-your-hard-drive-with-dban-erase-your-data-for-good/)

---

### Post by alexjpowell on 2016-10-27
Personally I'd buy a new HDD
Seeing as it's a laptop, it's probably been dropped a whole bunch of times

If you want to wipe the drive, boot into an ubuntu CD and run something like:
[FONT=courier new]scrub -p dod /dev/sda[/FONT]

---

### Post by alexjpowell on 2016-10-27
Here is me doing a similar thing on an external HDD - formatting the device and selecting it to overwrite with zeros:

[img]http://i.imgur.com/4oCcmSk.png[/img]

---

### Post by daniel5800 on 2016-10-28
I downloaded dban iso, burned it to a CD. Tried running it from start up. The blue screen comes up and everything seems fine. I go through the whole process, selecting everything. When I hit f10 to start dban, NOTHING happens! Did that a bunch of times, selecting different methods just to see if it had something to do with that. 
Also tried autonuke several times. It seems to be running, but then it says dban finished with non fatal errors. I need step-by-step help.
As a side note, I tried to download latest version of Ubuntu to a cd so that if dban was successful I could install fresh. I am not even able to download Ubuntu! I click download and nothing happens.

---

### Post by sudodus on 2016-10-28
Did you check the DBAN iso file with md5sum? If the hard disk drive is not too big, you can try to wipe it by overwriting with zeros. It should be more than good enough for your purpose (but very slow).

Try to download Ubuntu to another computer. This one might be damaged somehow, and there can be both software and hardware problems. Check the iso file with md5sum, and clone it to a USB boot drive.

-o-

Then you can try to run your problematic computer - and test the hard disk drive and RAM (memory). Only if the computer passes such tests, it is worthwhile running DBAN and install a new operating system.

---

### Post by daniel5800 on 2016-10-29
Being as though I cannot get dban to run for me successfully, now I am attempting to format the hard drive myself. But, just like everything else, I'm running into problems and I do not know what to do. I have to tell you beforehand that I do not know much about computers. I know how to press buttons though. So can somebody please just tell me exactly what to do in plain simple language. When I try to format I keep getting error messages I do not understand.
I am using the "Disks" utility to format Hitachi HTS547550A9E384 (JE3OA50A). When I press the additional partition options button and select Format/Overwrite Existing Data With Zeroes, I get the following message:

Error unmounting filesystem

Error unmounting /dev/sda1: Command-line `umount  "/dev/sda1"' exited with non-zero exit status 32: umount: /: target is busy
        (In some cases useful info about processes that
         use the device is found by lsof(8) or fuser(1).)
 (udisks-error-quark, 14)

Same thing when I try to format whatever a 3.9 GB Block device is.

Somebody please help. I tried dban. It boots right. But when I run autonuke mode it "finishes with non fatal errors." When I run it in interactive mode, after selecting all of the options, I press F10 to start it, and NOTHING happens. I believe this computer has malware/spyware, etc. on it and I just want to wipe it clean and start fresh. I cannot just trash the computer because it is all I have for now.

---

### Post by daniel5800 on 2016-10-29
Sir, I do not even know with md5sum is. I have just tried to wipe it by overwriting with zeroes but I'm getting errors with that too, which I just begun a new thread about.

---

### Post by yancek on 2016-10-29
What software are you using?  GParted is a pretty simple and useful program with a GUI and is on the Ubuntu installation media.  The "target is busy" message means you are either trying to modify partitions from an installed system or the partition(s) is/are mounted.  If you are using a DVD/flash drive, make sure you 'unmount' or verify that any partitions are unmounted.  Using GParted is explained at their site below.

[http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by wildmanne39 on 2016-10-29
Please do not post duplicates, it dilutes community effort. Threads merged

---

### Post by daniel5800 on 2016-10-29
I do not know what you mean. I am using "Disks" from Ubuntu Software. Using a DVD/flash drive for what? Please understand that you are speaking to a complete beginner.

---

### Post by daniel5800 on 2016-10-29
Sorry. I didn't really know what to do so I just started a new thread.

---

### Post by wildmanne39 on 2016-10-29
No worries, just one thread per issue is the rule.

If you do not get replies you can bump your thread every 12 hours to bring it back to the top.

---

### Post by oldos2er on 2016-10-29
> **daniel5800 said:**
> Sir, I do not even know with md5sum is. I have just tried to wipe it by overwriting with zeroes but I'm getting errors with that too, which I just begun a new thread about.

There's an explanation of md5sum [here.]("https://help.ubuntu.com/community/HowToMD5SUM") It's a way of checking the integrity of the Ubuntu ISO file you downloaded. Normally you would run an md5sum check before burning the ISO to a DVD or USB.

See also [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) and [https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto) for more info.

---

### Post by sudodus on 2016-10-29
> **daniel5800 said:**
> Being as though I cannot get dban to run for me successfully, now I am attempting to format the hard drive myself. But, just like everything else, I'm running into problems and I do not know what to do. I have to tell you beforehand that I do not know much about computers. I know how to press buttons though. So can somebody please just tell me exactly what to do in plain simple language.

If this computer is damaged, and no longer reliable, it is better to download files and create your tools in another computer. Is this possible - ***can you borrow another computer?***
> 
When I try to format I keep getting error messages I do not understand.
I am using the "Disks" utility to format Hitachi HTS547550A9E384 (JE3OA50A). When I press the additional partition options button and select Format/Overwrite Existing Data With Zeroes, I get the following message:

Error unmounting filesystem

Error unmounting /dev/sda1: Command-line `umount  "/dev/sda1"' exited with non-zero exit status 32: umount: /: target is busy
        (In some cases useful info about processes that
         use the device is found by lsof(8) or fuser(1).)
 (udisks-error-quark, 14)

Maybe you are trying to unmount the partition that your computer is booted from, like sawing the branch you are sitting on.

Or there is a bug in Disks. In that case, you can try another tool, for example ***gparted*** as suggested by *yancek* above, or ***mkusb*** according to this link,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
> 
Same thing when I try to format whatever a 3.9 GB Block device is.

This is probably a '4 GB USB pendrive'.

If you want to know better what drives there are and how they are named, please run the following command lines in a terminal window. You can copy and paste between the window of your browser at the Ubuntu Forums and your terminal window (in both directions, which reduces the risk of typing errors.

```
df
sudo lsblk -f
sudo lsblk -m
sudo parted -ls
```

Please put the output of the commands within [noparse]```
tags
```[/noparse] to make it easier to read: Click on the red button **[COLOR="#FF0000"]Go Advanced[/COLOR]**, mark the text and click on the **#** icon above the editing window (or do it manually), like this:

[noparse]```

your output line 1
line 2
line 3
...

```[/noparse]

Notice that you can mark (press the left button while moving the cursor) and paste (press the middle button or wheel to paste) from a terminal window to the editing box of Ubuntu Forums.
> 
Somebody please help. I tried dban. It boots right. But when I run autonuke mode it "finishes with non fatal errors." When I run it in interactive mode, after selecting all of the options, I press F10 to start it, and NOTHING happens. I believe this computer has malware/spyware, etc. on it and I just want to wipe it clean and start fresh. I cannot just trash the computer because it is all I have for now.

Let us take it stepwise. Please answer the questions and try to do the tasks suggested, and we will try to give stepwise replies (some suggestion or some new question) to bring the issue closer to a solution :-)

---

### Post by daniel5800 on 2016-10-29
It is possible for me to download the required tools on another computer. What you said about me maybe trying to unmount the partition that my computer is booted from makes sense, after reading the comparison you made. But I don't understand how else I would be able to do it. I am going to take a look at the other things you suggested right now.

---

### Post by daniel5800 on 2016-10-29
I just got your message, and I cannot even figure out how to reply back to  you. If you don't mind, can we please communicate via email?

---

### Post by QIII on 2016-10-29
I have snipped your email address to keep it from being picked up by web crawlers.

Please be courteous to other users.  You started the discussion here, please finish it here so that the whole community can learn.

---

### Post by daniel5800 on 2016-10-30
Sorry, Qlll. As I said, I could not figure out how to reply, and then I saw that my reply did go through. I feel like such an idiot! :) Anyway, you guys are all amazing and I really appreciate the patience and the help.

---

### Post by sudodus on 2016-10-30
I think that you had a temporary problem, because of a bug in the software that is running the Ubuntu Forums. It happens to all of us, also to me several times every week. Sometimes it is not possible to reply, sometimes there are doublets (two identical replies). There can be a confusing error message, when this happens.

Please try to communicate via this channel (your thread here at the Ubuntu Forums) even when it is frustrating and you have to wait and try again after a while :-)

-o-

You can create a boot DVD or USB drive from an iso file, when you are running another computer (with linux, Windows or even MacOS).

After that you move your boot DVD or USB drive to the problematic computer and boot from it,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

This makes it possible to unmount all partitions on the internal drive. It should also make it possible to check the hard disk drive and the RAM for hardware errors.

---

### Post by daniel5800 on 2016-10-30
What I ended up doing was: downloading Ubuntu to USB, booting from that, formatting the hard drive, which took about six hours. I still do not trust this computer, but I don't know what else to do. I know you guys are explaining a lot of different things, but it's almost like a foreign language. I am going to try to download a fresh copy of DBAN later on, and try to boot from that and see what happens. If that doesn't work, I will eventually take a hammer to this machine. I hate to have to do that though, but it is what it is. Thanks for all of the help, everybody. Peace and love.

---

### Post by mörgæs on 2016-10-31
> **daniel5800 said:**
> I still do not trust this computer, but I don't know what else to do.

There is no reason not to trust that the hard disk is clean after a format. Only thing I would recommend is checking for rootkits. Buntu has some program for that, and if they are OK you are all good to go. I use a lot of scavenged hard disks at home and don't bother using DBAN. 

Anyway, if you nevertheless want DBAN and it doesn't run, neither from USB not from CD, you could also try Killdisk.

---

### Post by daniel5800 on 2016-11-01
We can consider this thread as solved. I give up on trying to run DBAN. What I did was: formatted the hard drive, overwritting it with zeroes, using a Ubuntu USB. I then installed Ubuntu on the hard drive.

---

### Post by sudodus on 2016-11-01
Thanks for sharing your solution, or should we say work-around :-) I agree with mörgæs, that you can be sure that there is no virus hiding there.

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED. That makes it easier for other users to find your solution.

---

