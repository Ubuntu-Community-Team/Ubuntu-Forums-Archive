---
title: "Dual Boot problem Ubuntu 12.04"
date: 2013-01-26
forum: General Help
---

### Post by Alterzeus on 2013-01-26
I have installed ubuntu 12.04 on dual boot with vista.
For about three months it worked ok.Today I chose Ubuntu 
from the Boot menu and I get a magenta screen with nothing running
How can I fix this problem?I hope not again format.
Any help it would be very usefull

---

### Post by alarme on 2013-01-26
You can try to edit the grub2 line that starts Ubuntu
To do this, highlight the boot menu line and press "e" to edit, then remove the --quiet parameter.  This way, maybe you can see what is happening at boot time.

---

### Post by oldfred on 2013-01-26
+1 on alarme suggestion.

May be video? What video chip?

---

### Post by Alterzeus on 2013-01-26
It doesn't start Grub.It starts windows boot management buddy..
And then it gives me two options to start Windows and Vista and then it start Ubuntu and I get a magenta screen

I don't know about the video chip you say my friend.

It is a lenovo g530 laptop

Intel Pentium Dual-Core T3400 (2.16GHz, 1MB L2 cache, 667MHz FSB)
Microsoft Genuine Windows Vista Home Premium (w/ SP1)
15.4-inch glossy 16:10 display (1280x800)
Intel Graphics Media Accelerator 4500MHD
3GB DDR2 667MHz RAM
250GB 5400RPM HDD
SuperMulti DVD+/-RW Optical Drive
Broadcom WiFi (802.11b/g), 10/100 Ethernet, Modem
6-Cell 11.1V 53WHr Battery
Limited 1-year standard parts and labor warranty
Dimensions: 14.1 x 10.1 x 1.45
Weight: 5lbs 13.9oz

Thank you for your responses

---

### Post by oldfred on 2013-01-26
Intel only has one driver and it usually works.

You can try this:
       if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot instead of nomodeset as shown how below.

    
       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Alterzeus on 2013-01-27
Sorry I can't understand what should I do...
Just to mention :my Ubuntu worked fine so far..And I haven't done 
any changes in my lappc.

I have only access through Windows Vista where in program files there is a directory that says ubuntu and there are some other dirctories one of them says boot.Is there a file on boot where i should make my changes?

Unfortunatelly I cant'see the files I had in Ubunut installation 
and I need them

If I use Wubi to reinstall ubuntu will I loose the files I have saved?

Thanks for the replies!

---

### Post by oldfred on 2013-01-27
Wubi is a whole different animal. It is just a file inside the Windows NTFS partition and uses the Windows boot loader. So a Windows chkdsk can moved the root.disk file.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

            From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

    
       Missing root.disk
[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
[http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted](http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted)

   How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

---

### Post by Alterzeus on 2013-01-30
No luck at all!
I have tried all these links.

Nothing. I still can't login into Ubuntu except with an external usb stick preinstalled wubi with which I can't access the previous linux partitions.

I ve seen on the net that if I try to reinstall Ubuntu all files are wiped out.

So in order to get my data from the Ubuntu partition I am trying the following :

2 DiskInternals Linux Reader
1 Explore2fs

AND I HAVE NO RESULTS!!!
I JUST CAN'T FIND ANY LINUX PARTITION AND DATA

Could somebody please tell me what should exactly do?

Thanks again for the responses..

---

### Post by Mark Phelps on 2013-01-30
There is no Linux partition -- so you won't find one.  Wubi installs to a virtual filesystem INSIDE a Windows partition.

Don't use Wubi, but what I've read might work, is the following:
1) Copy the root.disk file off to another drive
2) Uninstall Wubi -- from inside Windows
3) Reinstall Wubi -- from inside Windows
4) Copy the saved root.disk file over the new one.

---

### Post by Alterzeus on 2013-01-31
But If I uninstall Wubi I ll lose all the data I have in Ubuntu

or not?

Do you know where are the files I have in Ubuntu?

---

### Post by Mark Phelps on 2013-01-31
Everything inside the Wubi install is contained in the single root.disk file.  IF you copy that off somewhere, you don't lose anything.

But ... as I have not actually tried this approach, I don't know if it will work.

However, if you simply reinstall, I believe it will be completely overwritten and you will lose everything you have.

---

### Post by Alterzeus on 2013-02-05
I am sorry how that can be possible. 

I can't unsderstand so by using Wubi there is no quarantee

for the file system?

How can Ubuntu offer such a solution as stable

I have lost many files!!

I am really dissapointed...

---

### Post by oldfred on 2013-02-05
wubi relies on Windows. :)
Which is why it is only suggested as a longer term test over liveCD. Even the developer of wubi suggests a full partitioned install if you like Ubuntu.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Missing root.disk
[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
[http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted](http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted)

   How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

   [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

    
       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by Alterzeus on 2013-02-06
I have done some progress.

I used ext2explore through Windows and I was able to see the folders and files of the root.disk whixh is about 17,3GB.

But the problem I have is that I can't find my files.

in the home folder I find some users I have created and my name as an adminstrator.

In which file are my files located?

---

### Post by oldfred on 2013-02-06
It it should be just like a full install. All user files & configurations are in /home and then the user name you created. If you created more than one user then each user may have separate files. The configuration files and files for some programs may be hidden. Hidden files all start with . as first character.

Probably better to use the liveCD as then you will be sure to see files correctly.

---

### Post by Alterzeus on 2013-02-07
I ve used the LiveCD through USB. But when with the new installation I go to the ubuntu file that is inside the windows partition and i find the root.disk I can't open it.
It says that could not display. The file is of an unknown type.
How that can happen.Why I can't open the file?

---

### Post by oldfred on 2013-02-07
Did you try the ways to open file in post #7?

Did you run fsck on wubi? Example is sda1, change to your partition.

       [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

---

