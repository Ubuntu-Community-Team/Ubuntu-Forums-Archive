---
title: "How do I Change where Ubuntu is Installed"
date: 2012-10-28
forum: General Help
---

### Post by balkrish999 on 2012-10-28
I currently have Ubuntu installed on my D Drive via Wubi  and Windows on my C Drive


How do i Keep Wubi, my boot options, everything.

but Simply change it from the D Drive to the C Drive?

I have Copied the Whole ubuntu folder on the D Drive 

So what do i do? 

Thank You

---

### Post by offgridguy on 2012-10-28
Is there a specific reason you want to do this ??

---

### Post by balkrish999 on 2012-10-28
> **offgridguy said:**
> Is there a specific reason you want to do this ??


Yes there is a reason. Otherwise why would i do it?

I want to Put another OS on that Partion and Do not want to make a new one.

---

### Post by jerrrys on 2012-10-28
This what your looking for

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=move+migrate+wubi+to+a+partition&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=move+migrate+wubi+to+a+partition&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by offgridguy on 2012-10-28
Thank you for the clarification,  just curious what OS are you planning to install?

---

### Post by balkrish999 on 2012-10-28
> **offgridguy said:**
> Thank you for the clarification,  just curious what OS are you planning to install?

Im Bored. 

I Currently have 

Windows XP ---- C
Windows 7  ---- W 
Ubuntu     ---- D     (Via Wubi)

I am thinking of doing a the all mighty Quadriple Boot and adding Windows 8 

- The Problem is i cant install windows 8 since there is no other partion (I have a Hidden one for System Safety) 


I want to get rid of the Ubuntu from the D drive and move it to the W Drive again via Wubi 

So I get : My Goal :) 

Windows XP  ----   C
Windows 7   ----   W
Ubuntu      ----   W  (via Wubi on W7 Drive)  
Windows 8   ----   D 


So yeah, Thats why i wanted to know how to change the ubuntu location 


However I am now thinking of simply backing up the whole Ubunut folder containing the Root Disk.  Completely Un installing Ubuntu
Then Install W8 and THEN Reinstall Ubuntu and hopefully restore the original Backup.  


Any, Tips, Help or Advice would be Helpful!

---

### Post by flint5 on 2012-10-28
If you have enough space on D drive, you don't need  to remove your Ubuntu installation.
There is a way to resize your D partition with GParted, but i must warn you, it is possible that you may lost some file/or not. Its always good to make some Backups. 
If you want to try, there is a link: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Run GParted from older Ubuntu LiveCD.

---

### Post by bcbc on 2012-10-28
Move the \ubuntu folder to the C: drive.
When you boot Ubuntu, you'll see the menu, but it won't boot - because even though it found the Ubuntu install, the grub.cfg is pointing to the partition associated with D:.

So, hit 'c' to get to a grub prompt. Then enter:
```
search -s -f -n /ubuntu/disks/root.disk
probe --set=diskuuid -u $root
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=UUID=$diskuuid loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```


Once you've booted, run:
```
sudo update-grub
```
Or else you'll have to manually boot next time.

Explanation of grub prompt commands:
1. Find the partition with the file /ubuntu/disks/root.disk and set it as root
2. Save the UUID of the partition that is root
3. loop mount the root.disk
4. set the loop device as root
5,6,7  load kernel and initrd from the loop device and boot

---

### Post by Mark Phelps on 2012-10-28
BEFORE you do that, go over to a windows 8 forum (eightforums.com) and ask if you can do what you want -- WITHOUT forcing an upgrade to Win7.  I've read that it will automatically upgrade Win7, effectively disabling Win7.  You should check on the Win8 forums to confirm that.

---

### Post by balkrish999 on 2012-10-29
> **Mark Phelps said:**
> BEFORE you do that, go over to a windows 8 forum (eightforums.com) and ask if you can do what you want -- WITHOUT forcing an upgrade to Win7.  I've read that it will automatically upgrade Win7, effectively disabling Win7.  You should check on the Win8 forums to confirm that.

I have backed up everything, but no it is not a upgrade, it will be a Dual Boot on a Separate Partion.

---

### Post by balkrish999 on 2012-10-29
> **bcbc said:**
> Move the \ubuntu folder to the C: drive.
When you boot Ubuntu, you'll see the menu, but it won't boot - because even though it found the U
4. set the loop device as root
5,6,7  load kernel and initrd from the loop device and boot


Thanks for that will try it, I forgot to mention my Grub is the Old verison and im running the old 10.04 Ubuntu?  Will those Commands Still work?

---

### Post by balkrish999 on 2012-10-29
I Moved the Ubuntu Folder - CUT it and pasted it on the other drive 

When i rebooted PC and clicked on Ubuntu 

I got this Error 

[http://www.google.co.uk/imgres?um=1&hl=en&sa=N&biw=1366&bih=671&tbm=isch&tbnid=4zhNMVfD61ETmM:&imgrefurl=http://social.technet.microsoft.com/wiki/contents/articles/12268.pxe-boot-error-0xc000000f-while-installing-sccm-2012-task-sequence-en-us.aspx&docid=jqIsdoKYEFYxGM&imgurl=http://social.technet.microsoft.com/wiki/cfs-file.ashx/__key/communityserver-wikis-components-files/00-00-00-00-05/6835.sccm.jpg&w=550&h=314&ei=MU6OUPPVCMbG0QWXp4HYDQ&zoom=1&iact=hc&vpx=444&vpy=304&dur=4389&hovh=170&hovw=297&tx=82&ty=116&sig=101029696722851297320&page=1&tbnh=127&tbnw=217&start=0&ndsp=22&ved=1t:429,r:6,s:0,i:87](http://www.google.co.uk/imgres?um=1&hl=en&sa=N&biw=1366&bih=671&tbm=isch&tbnid=4zhNMVfD61ETmM:&imgrefurl=http://social.technet.microsoft.com/wiki/contents/articles/12268.pxe-boot-error-0xc000000f-while-installing-sccm-2012-task-sequence-en-us.aspx&docid=jqIsdoKYEFYxGM&imgurl=http://social.technet.microsoft.com/wiki/cfs-file.ashx/__key/communityserver-wikis-components-files/00-00-00-00-05/6835.sccm.jpg&w=550&h=314&ei=MU6OUPPVCMbG0QWXp4HYDQ&zoom=1&iact=hc&vpx=444&vpy=304&dur=4389&hovh=170&hovw=297&tx=82&ty=116&sig=101029696722851297320&page=1&tbnh=127&tbnw=217&start=0&ndsp=22&ved=1t:429,r:6,s:0,i:87)


 Windows Boot Manger Error
   
  File: \ubuntu\winboot\wubildr.mbr
   
  Status:  0xc000000f
  Info 
  The selected enrty could not be loaded because the application is missing or corrupt
  
---------------------------------------------
Any Help?

Thank You

---

### Post by dino99 on 2012-10-29
nothing better than a real install

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by balkrish999 on 2012-10-29
> **dino99 said:**
> nothing better than a real install

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

No - i still want to use Wubi

---

### Post by bcbc on 2012-10-29
> **balkrish999 said:**
> I Moved the Ubuntu Folder - CUT it and pasted it on the other drive 

Windows Boot Manger Error
   
  File: \ubuntu\winboot\wubildr.mbr
   
  Status:  0xc000000f
  Info 
  The selected enrty could not be loaded because the application is missing or corrupt
  
---------------------------------------------
Any Help?

Thank You
Sorry forgot about that. You need to change the boot manager entry to point to the C: drive. Here's an example (but I'm changing my C: to F: )
```
Microsoft Windows [Version 6.2.8400]
(c) 2012 Microsoft Corporation. All rights reserved.

C:\Windows\system32>bcdedit

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
integrityservices       Enable
default                 {current}
resumeobject            {1632d04d-ac71-11e1-a566-934e06acdba5}
displayorder            {current}
                        {1632d058-ac71-11e1-a566-934e06acdba5}
toolsdisplayorder       {memdiag}
timeout                 10

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 8
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {1632d04f-ac71-11e1-a566-934e06acdba5}
integrityservices       Enable
recoveryenabled         Yes
allowedinmemorysettings 0x15000075
osdevice                partition=C:
systemroot              \Windows
resumeobject            {1632d04d-ac71-11e1-a566-934e06acdba5}
nx                      OptIn
bootmenupolicy          Standard

Real-mode Boot Sector
---------------------
identifier              {1632d058-ac71-11e1-a566-934e06acdba5}
device                  partition=C:
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu

C:\Windows\system32>bcdedit /set {1632d058-ac71-11e1-a566-934e06acdba5} device partition=F:
The operation completed successfully.

```

---

