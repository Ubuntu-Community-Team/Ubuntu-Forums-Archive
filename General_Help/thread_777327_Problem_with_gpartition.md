---
title: "Problem with gpartition"
date: 2008-05-01
forum: General Help
---

### Post by Hamstermerc on 2008-05-01
Hey so now i've decided that Ubuntu is definitely for me i want to start moving all my files from windows (music, videos, general files and stuff) into a partition in Ubuntu so that they're all very easy to access. 

I've installed Ubuntu using the prototype dual boot installer from here: [https://wiki.ubuntu.com/install.exe/Prototype](https://wiki.ubuntu.com/install.exe/Prototype)

I don't know if its simple lack of knowledge or if its just not possible to do but I can't seem to edit my hardrive into partitions. When i installed Ubuntu it appears that 10GB was set aside in windows for Ubuntu to hold its stuff.

In Gpartition i cant use any of the edit options. I can only look at the hardrive.

Any help would be much appreciated. Hopefully the info i've given helps you help me :)

Cheers

---

### Post by elvinatom on 2008-05-01
Well, do you want to keep Windows as well on you harddrive or will you convert your PC to a Linux box?

---

### Post by mikewhatever on 2008-05-01
I may be wrong, but doesn't that kind of installer create a virtual disk within the Windows partition and installs Ubuntu there? If that's the case, you should not need to resize your partitions.
Anyhow, the reason you can't change your partition now is because it's mounted, in other words, used by Windows. If you need to resize it, get GParted Live cd.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Hamstermerc on 2008-05-01
Well for now at least i want to hold on to windows until i can fully trust myself with linux. also theres a couple of things i still need to let go of with windows. Would like a partition for windows and a seperate one for linux

---

### Post by Hamstermerc on 2008-05-01
> **mikewhatever said:**
> I may be wrong, but doesn't that kind of installer create a virtual disk within the Windows partition and installs Ubuntu there? If that's the case, you should not need to resize your partitions.
Anyhow, the reason you can't change your partition now is because it's mounted, in other words, used by Windows. If you need to resize it, get GParted Live cd.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
So would i be able to keep my current Ubuntu preferences etc or would i have to reinstall everything?

---

### Post by elvinatom on 2008-05-01
I would suggest you shrink you Windows partition and add a root and a swap partition to have a "clean" hdd setup. The alternate Ubuntu CD does that quite nicely. Every task involving your hdd/files should be a walk in the park after that.
No offense, but it just seems a bit sloppy running linux of NTFS. Could run nicely though, what do I know? But I certainly wouldn't consider that setup myself under any circumstances.

---

### Post by Hamstermerc on 2008-05-01
> **elvinatom said:**
> I would suggest you shrink you Windows partition and add a root and a swap partition to have a "clean" hdd setup. The alternate Ubuntu CD does that quite nicely. Every task involving your hdd/files should be a walk in the park after that.
No offense, but it just seems a bit sloppy running linux of NTFS. Could run nicely though, what do I know? But I certainly wouldn't consider that setup myself under any circumstances.
In my defense i have had no prior knowledge of Linux until installing it and in its own little way it feels very safe and easy to remove so its a nice beginners way in. It seems to run just as well but i take your point. It is a bit sloppy and doesn't feel quite as solid

---

### Post by elvinatom on 2008-05-01
I really didn't mean to criticize you, sorry if it came across that way. In fact I'm excited about new people joining the Linux world. As to your questions and concerns:
I would suggest running Windows independently on its own partition and the same for Linux because if something goes wrong, and trust me that happens oh so easily, then Windows is still there - untouched by anything. So even if you manage to mess up the bootloader, it's always easy to restore you windows-partition. Running Windows and Linux of the same partition means no physical barrier - I would think about that before you put your money on your 1-partition solution.

I don't know much about your setup anyways, but it seems that an NTFS folder is used as the root of Linux. There could be a cross-mounting issue when attempting to get you windows-files transfered into Linux. If you created separate partitions that problem would be gone - and if later you recite to get rid of Linux: delete Linux partitions - stretch your NTFS partition - boot to recovery mode form Windows CD and in the prompt type fdisk /mbr, then grub is gone and Master Boot Record is ready to boot Windows again.

---

### Post by mikewhatever on 2008-05-01
Hamstermerc, I don't see a compelling reason to move your Ubuntu installation to a dedicated partition. According to this [FAQ]("http://wubi.sourceforge.net/faq.php"), files should be available to you from the Windows partition, and there is nothing wrong with running Ubuntu from NTFS, don't let this prejudice affect you.
The above mentioned site has a lot more info, also on your original question, so have a closer look.

---

### Post by elvinatom on 2008-05-01
I looked at it and stand corrected.

---

### Post by Hamstermerc on 2008-05-01
Well thanks very much to both of you :) I'm thinking of trying a partition install just to further my own knowledge but at least i can be safe in the knowledge that my current installation works fine and isn't dangerous etc. Once again, thankyou for making my Linux experience much more relaxed and groovy :)

---

### Post by elvinatom on 2008-05-01
Awesome - I hope you're a keeper!

---

### Post by abenrob on 2008-05-01
So can we hop back to the original question? I too am trying to use GParted, and it will show me the sized of my partitions, but won't allow me to resize anything. (I'm trying to increase my NFTS from 4.3-10GB, as I need some space on the XP side for some software for work (which is windows only software...)
was the consensus there that the GParted live CD will allow resizing of the partitions?
Thanks.

---

### Post by elvinatom on 2008-05-01
I'm not too sure about that, but I believe that you need some extra packages to create/manipulate certain types of partitions under parted. "ntfsprogs" maybe? Make sure the partition that you want to resize is not mounted.

---

### Post by -Zeus- on 2008-05-01
> **elvinatom said:**
> I'm not too sure about that, but I believe that you need some extra packages to create/manipulate certain types of partitions under parted. "ntfsprogs" maybe? Make sure the partition that you want to resize is not mounted.

try "ntfs-3g"

---

### Post by abenrob on 2008-05-07
Trial and error saves the day...
GParted live CD did an excellent job of shrinking my ext3, and growing my NFTS, with data on both. No data lost, and full functionality on both sides of the partition.

---

