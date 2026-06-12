---
title: "Error: &quot;Failed to unmount partitions&quot;"
date: 2007-06-16
forum: General Help
---

### Post by daniel_ba on 2007-06-16
Hey everyone,

I've been trying to install Ubuntu 7.04 for the last 24 hours (non-stop) on a Dell X200, and because Ubuntu doesn't recognize my cd-rom drive I tried to use Wubi which (based on my understanding) is able to offer a solution;

It downloads the .iso file flawlessly and reboots, but after selecting Ubuntu it gives this error before even the installation begins (after checking the hardware):


     migration-assistant needs to mount a partition, but cannot do so because the following mount point
     could not be unmounted:

     /dev/sda1

     Please close any applications using these mount points.
     Would you like migration-assistant to try to unmount these partitions again?
     Failed to unmount partitions

     Yes/No


Needless to say clicking on Yes doesn't work. I really like to install Ubuntu and would really appreciate any help I could get.


Cheers,
Daniel

PS I've been googling for hours trying to find people who might have the same problem, but either I'm the only one who's encountered this issue, or I'm doing some obvious thing wrong.

---

### Post by Psykid on 2007-06-16
I have the same problem. I`ve tried to install : ubuntu,xubuntu,kubuntu ..HOPELESS...

" can not unmount /dev/sda1"

plus ..when it`s booting for the first time ..i get 

Loading, please wait 
No RAID disks
una ble to mount /sys

and after a while i got my nose into console and saw that something is read only ..but can`t see it further cos it dissapears 

plus

tried also to unmount manualy 

umount /dev/sda1

and it gives: innapropiate ioctl for this device or something.

tried also with different size disks ..and different partitions.

Please anyone who knows ..help us!

thank you .

---

### Post by jmo8795 on 2007-06-25
Hi guys,

Daniel, 

I can't help with the Wubi issues, however, I may be able to help you get your CD-ROM drive detected which would allow you to perform a standard install.

I also installed Feisty recently on a Dell Latitude X200 and ran into the same issue with the CD drive not being detected (the drive is in a media base that the laptop connects to).

I was able to get it to recognize the CD drive by manually specifying the drive location during the install process as /dev/scd0.  

Steps I followed are outlined below:

1. I burned an  alternate install .iso and started the install in text mode. 
2. After the installer loads and you partition your HD, select a keyboard layout, etc...the installer tries to detect a CD drive and fails.  It then asks if you want to install a driver from a disc.  
3. Select the "No" option.  After doing so, the installer asks you if you want to manually specify a drive location.  
4. Select "Yes" and select "None" when prompted to enable additional services/drivers.  You will then see a prompt that will allow you to input a specific drive location.  
5. Input /dev/scd0 and the installer should then be able to detect the drive.  

This worked for me with the CD R/W in the media base.  I'd think this would also work for an external firewire or USB drive.

Those steps are from memory, so if they are slightly inaccurate or out of order I apologize.

Hope this helps.  Sorry I can't give any insight on Wubi but I've never configured that before.

Good luck.

---

### Post by ago on 2007-06-25
What version of wubi are you using? In which partition did you install wubi? What is your windows partition?

---

### Post by g90215 on 2007-06-30
Hi everyone,

Today i tried installing ubuntu 7.04 using Wubi 7.04.01.
I manually downloaded the alternate iso and put it in my wubi directory

I ran the Wubi installer gui in windows (xp home sp2) and everything went fine. i rebooted and began the ubuntu install. i had the invalid username error (because i chose the same username as my xp one), and even though it let me specify a different one to use with ubuntu i believe it corrupted the installation because i got the "can not unmount /dev/sda1" error.

after trying lots of things to salvage the installation i gave up and uninstalled it.
i went back to windows and tried again with the wubi installer, but i changed one thing: the user name.

after that it all installed fine. so perhaps thats something worth trying for those of you who are experiencing the same unmounting issue.

Good luck

---

### Post by ago on 2007-07-02
Can you provide me the /preseed.cfg and the /var/log/syslog file? You can copy them over to /media/host (=C:). Thx.

---

### Post by ago on 2007-07-02
I'd like to fix this, can you guys please provide me with the syslog and preseed files?

---

### Post by ago on 2007-07-04
Can you please try [http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04.217.64.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04.217.64.exe) and let me know if it works or not?

---

### Post by g90215 on 2007-07-04
are you talking about the syslog and preseed files from the failed installation? if so i must apologise because i wouldnt have those anymore...

---

### Post by ago on 2007-07-04
can you try the new build and see if it improves things?

---

### Post by g90215 on 2007-07-04
to be honest i havent got enough drive space left on my pc to handle another, but as long as it doesnt affect the test i'm happy to give it a go on my laptop?

---

### Post by ago on 2007-07-04
Yep but a different machine would not necessarily recreate the same error.

Anyway here is the latest build to try: [http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield-217.65.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield-217.65.exe)

---

### Post by g90215 on 2007-07-05
ok well how about i try the old wubi build on my laptop, and if it gives the same error i will then try the new build? (it will be no problem to recreate the process that caused the error on my pc)

---

### Post by ago on 2007-07-05
Sounds good

---

