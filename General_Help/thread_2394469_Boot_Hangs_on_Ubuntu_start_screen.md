---
title: "Boot Hangs on Ubuntu start screen"
date: 2018-06-16
forum: General Help
---

### Post by 007casper on 2018-06-16
After update to 18.04 LTS ubuntu... 99% percent of the time it doesnt boot. It just hangs on the Ubuntu start screen.

I default to maintenance mode... clean memory, do package maintenance, and fsck etc... still have a hard time booting... and if it boots.... It boots without a graphic card.
Then, I tried so many different ways of booting and sometimes spending a great amount of time just to boot. It is extremely frustrating.

Please, advise. Thank you.

---

### Post by oldfred on 2018-06-17
What brand/model system?
What video card/chip?
Some need extra boot parameters to work or work well.

Have you updated UEFI/BIOS from your vendor?

---

### Post by 007casper on 2018-06-18
model - Asus Model UX501V (UX501W-DS71T) Notebook PC

memory - 16gb
processor - Intel® Core&#8482; i7-6700HQ CPU @ 2.60GHz × 8 
graphics - llvmpipe (LLVM 6.0, 256 bits) -  Graphics Coprocessor 	Nvidia GTX960M 2GB GDDR5
gnome - 3.28.1
os type - 64 bit

Have you updated UEFI/BIOS from your vendor?
no, I havent.  Updating bios is a bit scary.

I am still having same issues. It just doesnt boot regularly.  It takes forever try to boot to ubuntu. Once it does, if the screen goes to sleep, sometimes wont take the login password, which is weird. I have to shutdown and try to restart the computer, and then boot issue all over again.

I default to maintenance mode, and then boot... I can login, but no graphics card. It is extremely frustrating.

---

### Post by oldfred on 2018-06-18
You need to update UEFI.
Not sure Asus laptop procedure, but my Asus motherboard works very easily, once I knew how.

Have you installed nVidia driver from Ubuntu repository? It does not look like you have.
       If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)

---

### Post by 007casper on 2018-06-23
I uninstall the nVidia driver while back because it constantly had the fan on and it was overheating regardless. I installed the nVidia driver again following your instructions just to see if it helps.

It get an error. It won't boot at all.
Gave up waiting for suspend/resume device

Please, see the attached image
https://postimg.cc/image/u6j5mjm2v/
https://postimg.cc/image/aan6747nb/

Please, advice. Thank you.

what is the best way to update the UEFI without bricking the laptop.

Thank you.

---

### Post by oldfred on 2018-06-23
My Asus motherboard has 3 ways to update UEFI. From Windows (which I do not have), from a file in a FAT32 formatted partition (I use my ESP since it is FAT32, but have to set permissions to let me save file into it), and from a FAT32 DOS bootable flash drive.
Best to check your manual on exact procedure, or see if Asus has procedure as downloadable file, some have it separate & some include instructions in compressed download.

Did you boot to recovery mode and terminal and run the suggested `systemctl status plymouth-start.service`?

---

### Post by kazakore on 2018-06-23
A lot of manufacturers only provide .exe files a lot of the time. What they don't really tell you is that these can often be extracted as an archive to get the files you need for the other methods. May be worth bearing in mind ;)

---

### Post by 007casper on 2018-06-24
systemctl status plymouth-start.service
plymouth-start.service -Show Plymouth Boot Screen
Loaded: loaded (/lib/systemd/plymouth-start.service; static; vendor preset:enabled)
Active: inactive (dead)
Condition: start condition failed at Sun 2018-06-24 01:05:10 PDT; 1min 44s ago
ConditionKernelCommandLine=splash was not met

---

### Post by oldfred on 2018-06-24
That does not help much.
Found these:
[https://ubuntuforums.org/showthread.php?t=2374208](https://ubuntuforums.org/showthread.php?t=2374208)
[https://askubuntu.com/questions/1020353/ubuntu-hangs-at-starting-show-plymouth-boot-screen](https://askubuntu.com/questions/1020353/ubuntu-hangs-at-starting-show-plymouth-boot-screen)

---

### Post by 007casper on 2018-08-01
I still have this issue. It is really pain, and frustrating. Total waste of time. Is nvidia the issue? or just plain ubuntu?... why would it work before and just stop working after the update?

---

### Post by QIII on 2018-08-01
Hello!

One of the surest ways to encounter a significant emotional event and catastrophic failure when doing an upgrade from one release to the next is to do it without first uninstalling all proprietary drivers.  Did you have a proprietary graphics driver installed?

Sometimes removing and reinstalling the driver after the upgrade works, sometimes it does not.  You may have been left with configuration settings that are not suited to the new release.

I don't know when you did your upgrade, but if it was in the last week or so, 17.10 would have been EOL.  EOL upgrades are fraught with problems and should not be attempted using the normal methods.  This would be particularly true if you performed the upgrade after the point release to 18.04.1.  There could be any number of conditions in the state of your machine that are causing issues.

My advice would be to attempt to back up what you can of your important files and perform a complete, fresh installation of 18.04.  While many people upgrade to new releases with no problems at all, many of us simply back up files and do a fresh installation while preserving our /home directories.

Let us know if you would like to do that and need advice on how to accomplish it.

Cheers!

---

### Post by 007casper on 2018-08-01
Thank you. I think I will do a fresh install, but will be loosing six months of data. 

The point is trying to login, so I can back up the last six months. However, it doesnt seem to work.

After so many ways of trying to solve this boot issue another problem started... the login screen just wont work at all.

After so many attempts it will go back to the login screen, or just will go blank.

installing nvidia driver from the terminal didnt help the situation, and it seemed like the login screen issue became more persistent.
 
I had to create another user, and then realize I am able to login in recovery mode with low resolution GDM (in graphics mode).

Then, I tried the main user, it just wouldnt login. Login screen just loops like a twilight episode.

So, I changed the login password from the terminal... same problem persisted.

When I press Ctrl-Alt-F2, switch to text mode, and then login in the console, the system works fine (in text mode)... even my graphic card works... however, realize that I cant access my files since the user under home folder was encrypted...

I use the passphrase, and it just would not work.

The last six years, there is always an issue with nvidia, or just new dist upgrade, or both... the server upgrades arent painful like this. Ubuntu worked just fine in the older distro... Why ubuntu or nvidia just ship a prototype, and let it loose in the wild? It is just torture. Why the graphics card would work when switch to the terminal, and in recovery mode become low resolution nightmare?

Above all, the passphrase wont work. It should, it is the right passphrase.

please, advise. Thank you.

---

