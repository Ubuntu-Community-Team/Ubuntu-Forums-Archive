---
title: "Remastersys 'loop'"
date: 2013-02-08
forum: General Help
---

### Post by Mike Green9 on 2013-02-08
Ubuntu quantel 12.10         gnome 3.6.0              Feb.2013

Hi.

I am having what appears to be an 'infinite loop' problem with remastersys. I recently downloaded & installed using the Synaptic Package Manager.

I ran it - and got a 2.7 gb ISO file. I burnt the ISO to a DVD and booted the DVD. I was so pleased to see my desktop come up on the DVD. First problem - there were 2 icons saying "Install System". In properties they had different sizes - all else was the same.

I clicked on one and the first screen came up (exactly as the original "Live CD Install"). It found free space and an internet connection. I clicked on "3rd Party Software" and "Download Updates". It displayed "Preparing To Install".

With the original "Live CD Install", the "Preparing To Install" phase usually takes 5 minutes on my system. I let it sit for 20 minutes and gave up. It allowed me to "Quit", at which point I tried clicking on the Second Install Icon. The same thing happened - I gave it 30 minutes this time. You can see the whirling icon - maybe it is waiting for something? It does listen to the mouse, as I can Quit at any time.

I read somewhere about installing "lupin-casper". Any thoughts on this?

I was so pleased when I stumbled upon remastersys. I am relatively new to Ubuntu, and desperately want a proper full backup. Any ideas would be greatly appreciated. 


Thanks,


MG...

---

### Post by sudodus on 2013-02-08
Remastersys is meant to make a distributable image of a system that you have created/tweaked. It is not meant to be a backup. For example, I don't think your personal files will be included.

If you want to backup your system, there are two principal choices:

1. A clone or an image, from which you will be able to restore your whole drive or some partitions exactly to the state when the clone/image was created. Use ***Clonezilla*** to create such a system.

2. Copying files, either of the system or only your personal data. You can use ***rsync*** or one of many GUI frontends using rsync to do it. Read the manual ```
man rsync
```

What do you want?

---

### Post by Mike Green9 on 2013-02-09
Hi.

I currently use SBackup to back up personal data 
            /etc/apt  &   /home/mg         (mg is me)

If my hard drive crashes, I would have to do a live cd restore, re-install all 40+ apps, and then use SBackup to restore my personal files/prefercences. I am trying to avoid re-installing all the apps.

I assume that remasterys is like a live CD restore, only it starts with my desktop as it is when it creates the ISO file. If this is the case, than a Live CD restore from the remastersys CD should give me what I want - even if I have to do an SBackup Restore afterwards.

It appears that it would make a proper full backup of my system. Perhaps I would build the ISO file monthly, and use SBackups in between. 

I would also like to use it to install my ubuntu system onto my laptop.

I was trying to test my theory by booting the remsaterysy CD, and doing the install from it on an old drive. The problem is that it loops on "Preparing to Install".

Has anyone else tried installing from a remastersys CD?



Thanks,

MG...

---

### Post by sudodus on 2013-02-09
Yes, it should work well like that, with one method to backup your system and another one to backup your data :-)

And it should work with remastersys. Could there be an issue with 12.10, that remastersys is not yet ready to manage this newest version of Ubuntu? And that it would work with 12.04 LTS?

I have no other idea why it does not work for you. I hope someone else who knows better about remastersys can help.
--
Until you succeed with Remastersys, you can make a system backup with Clonezilla. Particularly if you have a separate partition for massive data (for example pictures and multimedia), a compressed image by Clonezilla will be fairly small and quickly made. 

And you can backup the data partition by some other method, where you need no compression, because most of those files are already compressed. Rsync or some GUI front end running rsync is a good alternative. Sbackup is OK.

---

