---
title: "Regaining window 7 files after installing ubuntu"
date: 2014-09-02
forum: General Help
---

### Post by nami2 on 2014-09-02
[COLOR=black]Hello to the Ubuntu Community,[/COLOR][COLOR=black]

I’m new here as you can see, so forgive me for being quite ignorant about Ubuntu and Operating Systems in general. To begin with, I’ve run into a huge problem of not being able to access windows 7 after installing Ubuntu onto a bootable flashdrive. My situation is quite complicated, from my viewpoint that is, and I’m frustrated at what to do now. The installation process I followed was from this video:

[https://www.youtube.com/watch?v=i_4Kh5kE3xA](https://www.youtube.com/watch?v=i_4Kh5kE3xA)[/COLOR][COLOR=black]

To be honest, I came across this video when I tried googling ways to customize my desktop. When I saw this video on the Ubuntu desktop, I thought it would be a neat way to enhance my desktop. At that time I had no idea it ran on Linux.  Anyways, I followed the video and since it mentioned a bootable usb option, I thought that meant Ubuntu would work on any pc. I downloaded it, plugged the Usb into my laptop and when it didn’t show up, I realized from another video that you had to hit F12 at startup.

I did this and finished the installation process. After turning off my laptop and unplugging the usb, I turned my laptop back on only to see that Ubuntu was running, and windows 7 gone. I got so confused that I tried looking up my problem, and when what I feared most popped up, that is the possibility of overwriting the hard drive, I freaked out.[/COLOR][COLOR=black]

Anyways, I re-watched the same video regarding the installation process and about 11 minutes and 30 seconds into the video, it showed the option of how to install the program. I chose the ‘something else’ option of course, and avoided the erase disk option like told. Doesn’t this mean my windows 7 drive is still around? Re-watching the video made me realize that I should of backed up my documents. This is what I regret. I wish there was a more clarifying warning as to what would happen if one isn’t literate in OS. [/COLOR][COLOR=black]

I’ve tried looking for a solution online and visited many Ubuntu related forums and support pages. This has further confused me, since I’m not familiar with the terminologies and technicalities of the terminal. When I try restarting my laptop, try hitting F12, and selecting the hardrive option, Ubuntu comes back, so does this mean it overwote windows? I hope this isn't the case. I just want to know a way to access windows again, or find a way to know if my window files are still around. I had important files on my laptop, and want to find a way to restore them. I’m scared of trying any thing in fear of completely messing up, especially on the terminal. What can I do? I have some hope of retrieving my files based of off this page:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)[/COLOR][COLOR=black]

can someone further simplify this for me? I’m a slow learner and really am afraid of messing up. I need someone to help me walk my way through this. Since Ubuntu is open source, there isn’t any real one-on-one technical support it seems. Any alternatives?

I’ve also checked out:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)[/COLOR][COLOR=black]

I think screenshots help, but since I’m quite ignorant can someone clarify any risks, tips, or things to out for? Please give me a really easy guidline if possible, I don’t want to mess up and screw things further( I’ve learned mistakes on ‘route’ can mess things up). I’m a complete beginner. Let me know what has happed when I installed Ubuntu, and how to fix this problem. Please also expalin 'partitions' if possible. I heard there is a windows partition but I truly confused as to what that means. I’m still quite perplexed at the problem itself and frustrated at the same time since my files( and others in my family) on other user logins, are gone. Thank you! I’ll post this message on other Ubuntu forums for help. Sorry for the long post![/COLOR]

---

### Post by carl4926 on 2014-09-02
From ubuntu try

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

reboot

does windows 7 appear in the menu?

If not

Go back to ubuntu and post the result of

```
sudo fdisk -l
```

---

### Post by nami2 on 2014-09-02
Hello, thank you for replying.

Here is what I have after typing sudo fdisk -l into the command prompt.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00061155

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    62500863    31249408   83  Linux
/dev/sda2        62500864    66406399     1952768   82  Linux swap / Solaris
/dev/sda3        66406400   976771071   455182336   83  Linux
-----------------:~$ 

I didn't add my computer name though. I think it would be giving of information about myself?
Anyways, does this mean everything is Linux now?

---

### Post by carl4926 on 2014-09-02
> [COLOR=#000000]Anyways, does this mean everything is Linux now?[/COLOR]It does, yes

---

### Post by nami2 on 2014-09-02
Ok, then to recover my data, should I have some professional do it, or can I do it myself? I don't mind if it takes even a week to get everything back. Any tips to increase chance of recovery? I heard if you take out your hardrive and put it in another PC and run a data recovery software it is a lot better than doing it from the same computer. Is this true? Also what are the best data recovery softwares. Let me know one that is user friendly, or guarantees the best results. pros and cons would be good. Thanks, it seems I have so many questions.

---

### Post by The Cog on 2014-09-02
> I heard if you take out your hardrive and put it in another PC and run a data recovery software it is a lot better than doing it from the same computer. Is this true? 
Absolutely. All the time you run an OS from that disk, you are possibly overwriting more of your data that it doesn't know is there. The most friendly way is to out the disk in another PC. As you are more familiar with windows, I think you should use windows based recovery software. Avoid writing to your disk at all until recovery is complete. Perhaps even make a complete image file of the disk and work on that instead, but you obviously need quite a lot of disk space for that.

I'm afraid that you are likely to have to use recovery software such as photorec. This can scan your disk and write all the files it finds to another disk. However, it loses all the filenames and folder structure - all you get is many thousands of files with numbers for names. It's painful. There may be other software that manages better than photorec, I don't know. Perhaps someone else here can help further. I don't know if a professional service would be able to do better and recover filenames etc. 

I wish I could help more. And I'd like to complement you on your original post describing the problem. It left us knowing clearly what happened, what the problem was, and what level of expertise you have which helps us pitch our replies at the right level.

---

### Post by nami2 on 2014-09-02
Thank you for the answer Cog! Your answer helps clear a lot of misunderstandings. I'll do more research on what you have stated. In the mean time more questions:  is my current situation/ position = having my window 7 drive overwritten completely? I read that **you cannot recover overwritten data**. Is this true since Ubuntu/linux replaced the drive? I'm also guessing **'partition'** means part of a hard drive. Is this correct? If so, then the different threads on this forum deal with problems of overwriting certain partitions or updating and finding out something has been replaced. So then can you recover overwritten data? I should mention that I've used my computer, restarted it a couple of times, and tried downloading software( g-parted I believe), did this by any chance lessen my chance of recovering data?

Another thing, If one is going to put the hard drive into another PC, won't it run as Ubuntu. Sorry if this seems like a stupid question, but I'm certain this is the case, just I want to make sure since I'll be using someone else's PC. Also, **will I need a external hard drive** to save my data onto? I don't have one at the moment, but should I get one twice the size of my laptop space, just in case, or does it not matter? I know I'm asking lots of questions, but I want to make the necessary precautions before attempting anything. Any other things I should know before hand? Even it seems like common knowledge, please list them...like I said I'm very slow, but I guess that makes me much more careful. Thanks.

---

### Post by nami2 on 2014-09-02
Sorry, I just noticed another matter...

when you say  *"[COLOR=#000000]Avoid writing to your disk at all until recovery is complete. Perhaps even make a complete image file of the disk and work on that instead, but you obviously need quite a lot of disk space for that."[/COLOR]*

what exactly do you mean? Can you elaborate this? Does writing to your disk mean using your computer as a whole? I mean the internet stores cookies, cache, etc. right? Also what is an image file of a disk?

I truly am, and deeply am sincere to your posts guys...thanks

---

### Post by The Cog on 2014-09-02
If you boot Linux from the disk you installed it on, then it may continue to write to its disk, overwriting more of the old data that you want to recover. So don't use that computer at all. The best bet is to install the disk as a second disk in another computer. But even then, avoid writing to it (such as running chkdisk on it, or running a utility to try and replace the partition table). You could do more harm than good. Just use tools to read the disk and save whatever they can recover elsewhere. Only after you are sure that you have recovered everything you can by just reading the disk should you try any recovery tools that write to the disk such as partition table repair (e.g. testdisk). Certainly, if you think you might take the disk to a recovery service, don't do anything that writes to the disk at all.

If you were to put it in another computer, then something like photorec can scan your disk and save all the files it finds onto the hard disk of the host computer. It will need enough disk space to store all your data that it recovers, of course. If the host computer has lots of disk space, you can take a bit-for-bit image of your disk. This image file would of course be the size of your disk - 500GB. You can then use tools on that image file to try and fix things up (treating it like a physical disk) without risk of further damaging the real disk contents. You can of course try partition repair tools on the image without risk of messing up the original physical disk any further - you may get lucky that way. 

I wish I could help more but I would have to google around for more info on data recovery, same as you.

---

### Post by nami2 on 2014-09-02
Thank you so much for that! It really helps, I mean it. I'm also doing research. I'll probably post on here after gathering more answers to my questions. After all, I don't want to be ignorant in the matter, I mean that is what lead to this. I guess I might post some threads/ webpages I've visted regarding this issue to confirm their reliability tomorrow. Some people are using different methods and such, so I don't know which option to choose. I greatly appreciate the help

---

### Post by carl4926 on 2014-09-03
There is really no substitute for a backup made before hand.

Trying to recover files from a HDD that has been formatted and overwritten is fraught with problems and disappointment.

You could look at TestDisk
[https://dl.dropboxusercontent.com/u/10573557/LXF%20Articles/LXF128.feat_testdisk.pdf](https://dl.dropboxusercontent.com/u/10573557/LXF%20Articles/LXF128.feat_testdisk.pdf)

You can make a complete backup image of your HDD as it is now from a live CD or USB of Parted Magic
[https://dl.dropboxusercontent.com/u/10573557/pmagic_2013_08_01.iso](https://dl.dropboxusercontent.com/u/10573557/pmagic_2013_08_01.iso)

I have used this method several times:
Boot to a live from RAM session 
Have a external large USB HDD attached
From the terminal in Parted Magic do: ```
ionice -c3 ddrescue /dev/sda /media/sdc1/laptop.iso
```

/dev/sda is your machine HDD
/media/sdc1 is the target partition to write the backup image
laptop.iso is an example of the name you give the .iso image

You can now mess about with the image rather than the HDD you originally damaged

---

### Post by nami2 on 2014-09-03
Carl, thank you so much for the pdf on testdisk. That really helped me understand more about the software. The second link however did not open up for me, so I cannot say anything about that. Yeah, I guess I should use a disk image to retrieve my lost files than mess with the actual hardrive. One thing, regarding the external hard drive, can I take my sister's windows 8 laptop hardrive and put it into a laptop enclosure to turn it into an external hardrive? I don't have any at the moment. But will this work? my laptop hard drive is windows 7, now turned to Ubuntu. Hahaha, not sure how this all ties together.
 I think I'll start with the backup image after talking to more people? I want more insight into this situation. Also what you said about hardrives being formatted/overwritten, I read a forum were they stated it is possible to retrieve information after the drive had been overwritten/messed around 3 times! How is that possible? Another thing, just curious, does test disk restore programs? Programs like Flash CS6 are a bunch of files right? What about browsers, like chrome, I know my mother has her bookmarks on there. Apparently, chrome had folders for bookmarks...

Anyways, thanks so much guys! I really appreciate the help, it makes me want to learn more about computers and gives me a lot of hope to fix my problem! Tomorrow, I'll report in again :)

---

### Post by carl4926 on 2014-09-04
> **nami2 said:**
> Carl, thank you so much for the pdf on testdisk. That really helped me understand more about the software. The second link however did not open up for me, so I cannot say anything about that. Yeah, I guess I should use a disk image to retrieve my lost files than mess with the actual hardrive. One thing, regarding the external hard drive, can I take my sister's windows 8 laptop hardrive and put it into a laptop enclosure to turn it into an external hardrive? I don't have any at the moment. But will this work? my laptop hard drive is windows 7, now turned to Ubuntu. Hahaha, not sure how this all ties together.
 I think I'll start with the backup image after talking to more people? I want more insight into this situation. Also what you said about hardrives being formatted/overwritten, I read a forum were they stated it is possible to retrieve information after the drive had been overwritten/messed around 3 times! How is that possible? Another thing, just curious, does test disk restore programs? Programs like Flash CS6 are a bunch of files right? What about browsers, like chrome, I know my mother has her bookmarks on there. Apparently, chrome had folders for bookmarks...

Anyways, thanks so much guys! I really appreciate the help, it makes me want to learn more about computers and gives me a lot of hope to fix my problem! Tomorrow, I'll report in again :)

The second link would actually or should actually start a download, it's a .iso of parted magic that is ready to burn to a cd or write to a usb.

IMO: Your expectations may be a little high in recovery of what was lost.

You can make a backup drive from any HDD if you have the correct parts etc...
But you might be risking life and limb to use your Sister's HDD from her laptop, unless she is happy to see it wiped.

Bookmarks in Chrome should all come back in place assuming you were also using a google login to sync it all

---

### Post by nami2 on 2014-09-06
Hey guys I'm back! So I got a 2 Tb external hard drive, and now want to start running test disk and getting stuff back now that the weekend is here. Anyways, I believe I'm more comfortable about both test disk and photorec now that I've done a lot of research....but it runs down to two things

1. Since I mostly want my files/documents back....should I just use photorec and ignore test disk( Which helps to regain partitions)? I believe all files, downloads, and programs are located in the C drive right, so I should focus my attention only on the C drive? So by using photorec, I can restore files from only the C drive to get everything back... is what I'm thinking. But I want to see if I can get some programs back like Photoshop, Flash CS6, and some other programs I've installed in the past. These would also be in the C drive? I don't know where programs and browsers would be located on a hard drive. Just making sure. Also, some one wish to tell me why one would want a partition back, would it be because it is easier to restore part of a disk and it's contents? Then should I restore the whole C drive? What about other partitions? Is it wise to ignore them? 

2.  I still do not understand the whole reasoning behind taking out a formatted disk and putting it in another pc. How does that exactly help to prevent the hard drive from being over written again? I've really tried reading into this but I get more confused every time. This is the one thing I'm most confused about. You have a corrupted, wiped, or formatted hard drive, you take it out and put it into a PC and run testdisk or third party tool on that PC....and save the files and stuff on some external hard drive? How does a different Pc make sure the disk isn't overwritten? Isn't it the same hard drive? I'd greatly appreciate some clear answers on that one. Thanks.

Yeah so after getting these answers, I'll begin the long process of getting my data back...

---

### Post by The Cog on 2014-09-07
1: I don't think there's much hope of recovering your installed programs. Photorec and such look for data files like image and document files. I don't know if they would find and recover installer files, and even if they did you probably would not be able to recognise it because all recovered file names are just numbers.

2: When an operating system boots, this involves a lot of writing back to the disk as well as reading. Log files, temporary files, memory paging and who knows what else (I don't). If you boot that linux OS from the disk that used to have windows on it, all that writing could be going on top of important data that you really want to recover. But that won't happen to secondary disks, just the boot OS's disk. An OS will generally only write to its own partition(s) but in your case that is on top of old disk space that used to contain windows+data. It's like building on top of a valuable archaeology site. You don't know how much archaeology you are going to destroy.

---

### Post by carl4926 on 2014-09-08
> **The Cog said:**
> 1: I don't think there's much hope of recovering your installed programs. Photorec and such look for data files like image and document files. I don't know if they would find and recover installer files, and even if they did you probably would not be able to recognise it because all recovered file names are just numbers.

2: When an operating system boots, this involves a lot of writing back to the disk as well as reading. Log files, temporary files, memory paging and who knows what else (I don't). If you boot that linux OS from the disk that used to have windows on it, all that writing could be going on top of important data that you really want to recover. But that won't happen to secondary disks, just the boot OS's disk. An OS will generally only write to its own partition(s) but in your case that is on top of old disk space that used to contain windows+data. It's like building on top of a valuable archaeology site. You don't know how much archaeology you are going to destroy.

I agree.

Really you should just consider starting again.
That you don't already have a external backup is surprising but not unique. Consider it a lesson to learn from.
You can work on getting files back once you have made a backup image of the messed up HDD.
Perhaps too, you could live without Windows, though it sounds like you are pretty hooked on it.

---

