---
title: "All went wrong trying to add uuid"
date: 2013-09-18
forum: General Help
---

### Post by huxley2 on 2013-09-18
Hi, everybody

I tried to add a uuid to fstab for my storage partition - using this guide [http://ubuntuserverhelp.com/mounting-with-fstab/](http://ubuntuserverhelp.com/mounting-with-fstab/) - so as clementine library would be able to find my music folder after start up.

I used **blkid** to find the partition uuid which worked but when I typed in **sudo vi /etc/fstab** instead of getting something that resembled to guide's screenshot all I got was [ATTACH=CONFIG]246340[/ATTACH]


From here I wasn't able to type any more cmds so I exited and opened a fresh terminal and tried again but this time recieved this response [ATTACH=CONFIG]246340[/ATTACH]
When I pressed enter the previous image returned. Can anyone help me with this conundrum? I'm new to ubuntu and have already re-installed twice due to school boy errors but I'd rather learn how to fix things this time instead of taking the slackers way out.

Thanks
Huxley

---

### Post by Lars Noodén on 2013-09-18
You should end up with something more like this, but with your own UUIDs.

```

UUID=d6a94aeb-7e04-4ddb-b7a2-0ebf59c6545a /               ext4    errors=remount-ro 0       1

UUID=08920f80-d2ed-4b1b-8210-33755a0690f0 none            swap    sw              0       0

```

Also, wear a safety belt.  Before editing any imporant files, make a backup copy.

```

sudo cp /etc/fstab /etc/fstab.orig

```

If nothing else it allows you to roll back to a known working version and undo any experiments.

---

### Post by oldfred on 2013-09-18
You have wubi or an install inside Windows. So your fstab looks different than a standard install.

 Wubi not available with 13.04
[https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html)

      
 [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by huxley2 on 2013-09-18
Thanks for the quick response, guys.

Yes, Fred, I (unkowingly) have Wubi, I originally had ubuntu on a flash drive and after a quick trial followed the install option onto my pc from there. By the looks of the link you gave it looks like wubi was never suited for mass consumption, especially by novices such as myself so maybe I should take the slackers course after all and install direct to my hdd from ubuntu.com...it's a fun learning curve, for sure.

Top tip on the back-up Lars, I even did one before my adventures but it didn't fully complete - maybe connection failed as it uploaded to ubuntu one - whatever the reason in future I'll be sure to always double check it's all gone through smoothly before doing anything techie. 

Thanks again

Huxley

---

### Post by grahammechanical on 2013-09-18
That command opens the fstab file in a text editor called Vi. At the top is a white square. That is the cursor. We can move it up and down and left to right using the arrow keys. How we save what we have edited I do not know. Personally, I would use nano

```
sudo nano /etc/fstab
```

At the bottom of the screen is advice on what key combinations to use. Ctrl+O = writeout or save. Ctrl +X = exit. It also has the white flashing square that is the cursor.

Regards.

---

### Post by huxley2 on 2013-09-18
Thanks for the info, Graham, I have much to learn but a little less now than when woke up this morning. I'll try the nano cmd next time I have a stab at it

Regards

---

### Post by oldos2er on 2013-09-19
You're trying to mount an NTFS partition, is that correct? Also I'm not sure why you're using the advice from [http://ubuntuserverhelp.com/mounting-with-fstab/](http://ubuntuserverhelp.com/mounting-with-fstab/) since that's for Ubuntu Server mounting ext4 partitions. Better advice here: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Also since Wubi uses a non-standard fstab this may complicate things further.

---

### Post by huxley2 on 2013-09-19
It's quiet clear now that I've jumped into the deep end w/o armbands and my flailing limbs whilst making a decent size splash are doing little to keep me afloat.
I'll have to look into what wubi is and why I even have it. 

I installed ubuntu onto a memory stick - my recordable discs are only 700MB and too small - via universal usb installer and then installed onto my laptop from there. Will installing via this method always result in me having wubi? Also I've stored Ubuntu in a seperate partition from windows if that makes any difference?

Thanks for everyones patience, I appreciate that this must have quickly degenerated into a annoying / frustrating thread for linux pro's. If someone could briefly clarify the wubi situation and how I can not have it, I'd consider the thread closed as my ambition for the rest far exceeds my talent..

Humbled,

Hux

---

### Post by oldfred on 2013-09-19
I thought wubi only installed from inside Windows?
 wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

      
 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

So from live installer on flash drive you should just be able to install to a partition. But you have to have unallocated space and one available primary partition. MBR(msdos) has a 4 primary partition limit, but one primary can be the extended which is a container that can hold an unlimited number of logical partitions. Windows only boots from primary partitions, but Linux works just fine from logical partitions.

Install has not really changed between desktop versions, so all these give an idea of the install process.


 Install with screen shots:
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by oldos2er on 2013-09-19
If you have Ubuntu installed in its own partition, that is *not* Wubi. 

Don't give up. I know Linux is a steep learning curve at first, but we'll figure it out.

---

### Post by huxley2 on 2013-09-19
Thanks for that Fred. I remember that I did originally install from the  usb while in Windows so today I uninstalled / installed via ubuntu and  it all seems to be wubi free. Now when I start up I get the purple  ubuntu boot menu with ubuntu being the default OS and Windows is  optional.

Thanks again to everyone for the great support / advice

P.S. Thanks Ann. I'll have another bash it it soon enough but for now my brain needs to rest and relax. In the mean time I'll call this thread solved and come back with fresh eyes down the road some.

---

### Post by huxley2 on 2013-09-20
Cracked it

I just had to configure the partition with ntfs configuration tool and after a database update, fstab recognised it immediately.

---

### Post by oldos2er on 2013-09-20
Glad you got it going!

---

### Post by huxley2 on 2013-09-20
Thanks, Ann, me too

---

