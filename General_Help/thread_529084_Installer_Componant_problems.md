---
title: "Installer Componant problems?"
date: 2007-08-18
forum: General Help
---

### Post by blake589t on 2007-08-18
I really need help...after the installer finishes, and the system reboots, i chose wubi ubuntu, and it starts the final install.  For some reason, it shows a loader and then it stops and says that it "cant load installer components from cd" then i just abort the install and try booting again.  This time, when I chose wubi ubuntu, it said there was a problem with the iso and that i had to reinstall wubi...so i went back to windows and reinstalled it and the whole thing starts all over again.  How do I get it to work???

---

### Post by blake589t on 2007-08-18
Oh, almost forgot...if you wanted to know, im using windows vista premium build 6.06 on and HP Pavilion laptop dv9030us...if you needed to know

---

### Post by Patrick793 on 2007-08-18
When I installed, on Windows Vista, it went fine... Did somehow the ISO get deleted?

---

### Post by ago on 2007-08-19
Can you check the size of the virtual disk files in c:\wubi\disks? If one of them is 0, reinstall using 4GB

---

### Post by blake589t on 2007-08-19
wellz, actually i installed it on drive D, (yes, i have two hard drives) and also the iso... i heard that it downloads itself, or u can download it from the website and slip it into the wubi file made on the hard drive...well, while its installing i slipped the alternate iso into the wubi file and so the installer skipped the download...but then when the installer finished, i went back to the file and the iso had dissappeared...is that supposed to happen?  I tried both ways of getting the iso, and either way it goes wrong...so yah.

---

### Post by ago on 2007-08-19
Upon installation the iso is moved to c:\wubi\install. Upon uninstallation to c:\wubi-save. If you installed on D:, then it will be d:\wubi\install and d:\wubi-save.

---

### Post by blake589t on 2007-08-20
Hmmm... something tells me its something with ubuntu, because very rarely, kubuntu will install successfully. But lyk kubuntu installs maybe 1% of the times...and every single time besides the extremely few times it does install, it ends up telling me "!! Load installer componants from cd" and then, it ends up going to the ubuntu install list thingamagig, and i end up aborting the install.  The times it DID install was when i set it for 6 gig virtual hd...i wanted more space so i reinstalled it with 8 gig virtual hd, and that's when it stopped working so yah (BTW, i only tried installing kubuntu once in 6 gig and it worked...ubuntu had the same above problem when i used 6 gig)

---

### Post by ago on 2007-08-20
You have to press alt+f2, then

nano /var/log/syslog

look for errors at the end of the file

---

### Post by hh93 on 2007-08-22
Hi Blake,

The exact same thing happenned to me tooo...
tried to uninstall and reinstall more than 5 times, until i set up the installation size to 4GB as ago recommended, then it progressed smoothly. Do give this thread a read [http://ubuntuforums.org/archive/index.php/t-422427.html](http://ubuntuforums.org/archive/index.php/t-422427.html) .If you need space beyond 4Gb afterward, you may want to move Wubi Ubuntu to a real partition.

Good luck!

hh93

---

### Post by ago on 2007-08-22
Yep, if you have a 64 bit machines that is a confirmed bug, but it's not easy for me to fix that since I do not have a 64 bit machine (donations welcome) ;P

A workaround is to select 4GB and then generate the image file BEFORE rebooting using any other program that can create a large enough file.

---

### Post by blake589t on 2007-08-26
Wellz, I looked around, and as it seems there are other ppl with the same problem.  I pressed alt+f4, and looked at the log, and on the bottom, it said something about the cd image, error type 1, which I think means it cant access the cd image.  Below it, it said that it couldnt access the cd image, What do I do???

---

### Post by hh93 on 2007-08-26
Just curious, did you reinstall with 4GB?

---

### Post by blake589t on 2007-08-26
Well...no, that's because im definitely not running 64 bit.  Im using Windows Vista Premium 32 bit

---

### Post by hh93 on 2007-08-26
Are going to try?
See if it install?

---

### Post by blake589t on 2007-08-26
well, 4 gig is way too small, I used to use 6 gig, but that was too small, so i reinstalled with 8 gig.  Kubuntu installed successfully one or two times in both 6 gig and 8 gig.  Ubuntu didnt work on either.  I was looking around windows, and i found a file with logs from the windows experience index, and it said I have the componants needed for a 64 bit machine, even a 64 bit proccessor, but I just dont have a 64 bit Operating System...could that still affect it???

---

### Post by tuxcantfly on 2007-08-26
> well, 4 gig is way too small, I used to use 6 gig, but that was too small, so i reinstalled with 8 gig. Kubuntu installed successfully one or two times in both 6 gig and 8 gig. Ubuntu didnt work on either. I was looking around windows, and i found a file with logs from the windows experience index, and it said I have the componants needed for a 64 bit machine, even a 64 bit proccessor, but I just dont have a 64 bit Operating System...could that still affect it???

Use a 32-bit operating system. There's no point to using a 64-bit operating system unless you have over 4 GB of ram, and 64-bit operating systems have plenty of software/driver compatibility issues.

---

### Post by tuxcantfly on 2007-08-26
> well, 4 gig is way too small, I used to use 6 gig, but that was too small, so i reinstalled with 8 gig. Kubuntu installed successfully one or two times in both 6 gig and 8 gig. Ubuntu didnt work on either. I was looking around windows, and i found a file with logs from the windows experience index, and it said I have the componants needed for a 64 bit machine, even a 64 bit proccessor, but I just dont have a 64 bit Operating System...could that still affect it???

Oh wait never mind, I misread that post, ignore my previous one, no, the fact that your Windows is 32-bit not 64-bit shouldn't affect the Ubuntu install. However what I find strange is that kubuntu installed but Ubuntu didn't; were you using the standard alternate i386 isos in both cases, or did you pre-download an iso for one of them? You might want to try Ubuntu again and let it download the iso on its own.

---

### Post by blake589t on 2007-08-27
Well, I was proved wrong...ubuntu duz install when the hdd image is 4 gig...but now how do I do it with an 8 gig image???  I really dont want to have to stick with only 4gigs.  for you, I always let wubi download it, i never tried downloading it separate...but now what do i do to make the 8 gig work with ubuntu???

---

### Post by hh93 on 2007-08-27
> **blake589t said:**
> Well, I was proved wrong...ubuntu duz install when the hdd image is 4 gig...but now how do I do it with an 8 gig image???  I really dont want to have to stick with only 4gigs.  for you, I always let wubi download it, i never tried downloading it separate...but now what do i do to make the 8 gig work with ubuntu???

Are you interested in moving ubuntu to a real partition? That's one way to allocate more space to it.

---

### Post by tuxcantfly on 2007-08-27
> Well, I was proved wrong...ubuntu duz install when the hdd image is 4 gig...but now how do I do it with an 8 gig image??? I really dont want to have to stick with only 4gigs. for you, I always let wubi download it, i never tried downloading it separate...but now what do i do to make the 8 gig work with ubuntu???

See LVPM in my sig - it can resize the disks or transfer the install to a real partition

---

### Post by blake589t on 2007-08-28
See, I would, but I dont want windows to be destroyed...I want to keep both Operating Systems there.  Also, partitioning will crush all the data on my hard drive...I dont want to lose any data at all!!!  That's why I used wubi to use a virtual hd in linux...

---

### Post by hh93 on 2007-08-28
> **blake589t said:**
> See, I would, but I dont want windows to be destroyed...I want to keep both Operating Systems there.  Also, partitioning will crush all the data on my hard drive...I dont want to lose any data at all!!!  That's why I used wubi to use a virtual hd in linux...

Understood...

Do you know what the file system is? NTFS or FAT32?
For FAT32 the max file size is 4GB, migrating to a real partition perhaps the only option for more space; For NTFS, you can try Tuxcantfly LVPM to resize the virtual disk: both home and root ([http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html))

Best of Luck!

---

### Post by blake589t on 2007-08-28
Are you sure none of my data will be lost?!  that is the biggest thing i cant lose...also, what happens to the ubuntu partition?  I dont want to lose my settings, now after i got comfortable with it...it's also ntfs, btw

---

### Post by hh93 on 2007-08-28
> **blake589t said:**
> Are you sure none of my data will be lost?!  that is the biggest thing i cant lose...also, what happens to the ubuntu partition?  I dont want to lose my settings, now after i got comfortable with it...it's also ntfs, btw

No data should be lost from resizing home/system; though, nothing is guaranteed. 

You do regularly backup your data don't you? 

Resizing does not create a new partition for ubuntu; it creates a new file. As an Ilustration, the process of resizing home disk involves 2 steps: first, LVPM generates a file 'new.virtual.disk' the size you desired, and copy all data from home.virtual.disk to it; second, you manually rename it as home.virtual.disk

The second step was actually done inside microsoft windows; go into c:\wubi\disks, move your original home.virtual.disk to some other folder as backup, and rename new.virtual.disk as home.vitual.disk, then boot into ubuntu.

Below are some screenshot from my earlier attemp to resize my home.virtual.disk from 200MB to 500MB

To get comfortable with the process, perhaps try to resize your home disk initially.

Good Luck!
PS : 
-You can check changes to disks with Sytem-->Administration-->System Monitor and choose file system's tab. 
-only requires LVPM ([http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821))

---

### Post by blake589t on 2007-08-30
no, actually i just want to move files from the virtual hd, to my D: hard drive without overwriting any files; just adding files to the hard drive...how do i do that?  I ran LVPM, and right when it said that it was formatting the drive, i hit cancel, and i looked, and there were some new files there, so i thought maybe it did put them there, but i went back to windows, and the files werent there.  I can back to linux, and poof!  they were gone...how do i put the linux files onto the D drive without destroying anything???

---

### Post by hh93 on 2007-08-30
> **blake589t said:**
> no, actually i just want to move files from the virtual hd, to my D: hard drive without overwriting any files; just adding files to the hard drive...how do i do that?  I ran LVPM, and right when it said that it was formatting the drive, i hit cancel, and i looked, and there were some new files there, so i thought maybe it did put them there, but i went back to windows, and the files werent there.  I can back to linux, and poof!  they were gone...how do i put the linux files onto the D drive without destroying anything???

Ahhh.... copying individual files to other drive.
The simplest way is to use file browser, but with root priviledge.
This will allow copying files from wubi to host drive (c:\ ). Follow these steps; they only require 1 terminal command.
- launch terminal
- type sudo nautilus, wait till a file browser windows opens up
- navigate into your source folder inside home or file sytem, right click on the 'file' and choose copy
- navigate into filesystem\media\host (this represents your c drive), right click and choose paste; the file should be dropped there.
- Reboot into windows and look for the file in c:\ (double click My Computer then choose c:\), you should see the file there. If you want the files in d:\ you can easily copy and paste them inside windows. Otherwise, you can do it within ubuntu; but that requires additional step to mount the D drive.

Let me know if this helps

---

### Post by blake589t on 2007-09-03
so what files do i copy?

---

### Post by hh93 on 2007-09-04
> **blake589t said:**
> so what files do i copy?

Anyfiles basically...
try some text file for a starter.

---

