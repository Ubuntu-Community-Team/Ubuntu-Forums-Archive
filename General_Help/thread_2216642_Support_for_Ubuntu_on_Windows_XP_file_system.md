---
title: "Support for Ubuntu on Windows XP file system?"
date: 2014-04-13
forum: General Help
---

### Post by Owen Thomas on 2014-04-13
Hello people.

I currently lack the money I need to upgrade my Windows OS to 8 (or whatever) and have decided instead to stick exclusively to the Ubuntu 12.04 OS installed as a dual boot option. Hence, my questions for you are: have I made a good decision? Can I expect a later version (I was thinking 13.04) of Ubuntu to run over the Windows XP file system? For how long can I expect this?

Thanks in advance of your considered answer,

  Owen.

---

### Post by carl4926 on 2014-04-13
If you still have space allocated to where XP was. I would consider backing up all you need. And when the latest LTS 14.04 is released in just a short time now, you could install that and use your entire HDD

---

### Post by sudodus on 2014-04-13
I think and hope you have made a good decision :-)

There are many people around there, who are ready to help you. It makes it easier to give relevant advice, if you let us know

A. about your computer hardware

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

B. about your current Ubuntu installation

Please mount all partitions possible to mount and run the following commands (and post the output in a reply)

```

sudo parted -l
df -h

```

But until I have more details I can give this preliminary answer:

I expect future versions of Ubuntu to be able to read the file systems of Windows (including NTFS and FAT32).

Your current version of Ubuntu 12.04 has long time support, LTS, until April 2017. But do not install 13.04, it has already passed end of life. It might be a good idea to wait and upgrade to the next LTS version, 14.04, when the first point release is released, maybe in August this year (Ubuntu 14.04.1)

---

### Post by 3rdalbum on 2014-04-13
Hi

1. 12.04 is a good release of Ubuntu. It is, however, getting rather old. The new version coming out in a few days, 14.04, is also good and has newer software and more features. If you are happy with 12.04 there is no need to upgrade until 2017.

2. I don't understand what you mean about Ubuntu running over a Windows filesystem. You can't install Ubuntu onto a Windows filesystem, you would need to format it to ext4 which would erase all the files within that filesystem.

Can you please clarify what you mean?

Don't bother with 13.04, it is no longer supported. Stick with 12.04 or go to 14.04.

---

### Post by Owen Thomas on 2014-04-13
Thanks for the replies.

FYI, I'm hosting my Ubuntu on a Dell Inspiron 6400 bought circa 2006. The system settings in Ubuntu tell me the following: Memory: 992.5 MiB, CPU: Genuine Intel® CPU T2300 @ 1.66GHz × 2, Graphics: Intel® 945GM x86/MMX/SSE2, OS Type: 32-bit, Disk: 89.1 GB.

I might be mistaken, but as I understand things, I installed Ubuntu to create a virtual disk on the Windows XP FAT32 file system. My concerns are that now that XP support has discontinued, will Ubuntu similarly disendorse support on the XP FAT32 file system? I'm considering installing Ubuntu to run over its own physical file system, but everything's running fine, and I'd rather not rock an apple cart if I can avoid it.

Hence, amongst my concerns is this question: will the FAT32 file system expose Ubuntu to compromise? I think that Ubuntu, fielding data exchange between the disk and the outside world, will sufficiently guard my data even if it remains on FAT32. However, if I have concluded wrongly, I will consider removing windows completely and installing Ubuntu.

Thanks again and further considered advice would be well received,

  Owen.

---

### Post by sudodus on 2014-04-13
The reason why I asked for the output of those commands (in post #3) was to find out what kind installation it is. From your explanation, I guess that it is a wubi installation. Does wubi ring a bell? Otherwise the output of those commands will tell.

Wubi will not be developed further, because it does not work with the new Windows version. So if you have a wubi install, I recommend that you migrate it to a normal dual boot installation. See this link

[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

### Post by Owen Thomas on 2014-04-13
The word "wubi" does ring a bell... I'll follow the lead you've given me and get back soonish.

Thanks,

  Owen.

---

### Post by Owen Thomas on 2014-04-15
Thanks for this info.

From the information people have given in this thread, I understand that new releases of Ubuntu will not be bundled by the wubi installer because Windows 8 doesn't like the wubi installer. However, I think, perhaps, there may be others who would like a wubi install for Windows XP for at least the next few releases. Although I am only speaking for myself, the wubi install allowed me to not have to worry about partitioning my disk - it simply created a virtual file system as a flat file under the XP FAT32 file system. I actually liked that.

The path of least resistence for me in the medium term is to leave XP on my machine and not create a separate partition. It would help things for me if I could keep installing new releases of Ubuntu using the wubi installer. If a similar request to mine had been put aside before, some indication of the reasons for why this was the outcome would be great.

Thanks,

  Owen.

---

### Post by craig10x on 2014-04-15
I'd forget about the wubi idea as it won't be available in newer releases...can't you just back up whatever data you need to save on an external drive (like a usb flash drive for example) and then clean install ubuntu 14.04 when it goes final on thursday this week? Download it when it's available later in the week and burn the image to a dvd disc and have the iso's installer wipe out your windows install and replace with ubuntu...

---

### Post by Owen Thomas on 2014-04-15
Oh well. I suppose I can partition my drive or whipe out XP when I feel that I have to. Still, I feel that having to contemplate burning DVD's might be enough merely to go out and buy Windows 8.

I first installed Ubuntu from a DVD copy a friend bought from the Ubuntu org. I hope perhaps that I can still do this.

  Owen.

---

### Post by craig10x on 2014-04-16
Why buy a dvd copy of ubuntu when you can burn your own? At the end of the week, 14.04 final will be up on the mirrors...you can just download it and burn it as an iso image on a dvd...then boot into the dvd's live session and install ubuntu...have the auto installer replace XP with Ubuntu...takes about 25 minutes or less to install and you are good to go!

No point in getting involved with wubi, since newer versions of ubuntu no longer support it...i used wubi many years ago and quickly found out that an actual real install is far superior...

If you feel you must (and don't have XP restore discs) then you can always do that first before you install ubuntu but once you start using it, i don't think you will be missing windows much at all ;)

I played with Windows 8 for a while on my friend's laptop and have to say Ubuntu with unity is a LOT nicer desktop to use...so unless you have some windows programs you absolutely cannot live without, Ubuntu would be the best way to go...

---

