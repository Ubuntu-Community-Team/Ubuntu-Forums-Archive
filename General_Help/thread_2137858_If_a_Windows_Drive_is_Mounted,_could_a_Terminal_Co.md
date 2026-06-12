---
title: "If a Windows Drive is Mounted, could a Terminal Command Affect the Drive?"
date: 2013-04-22
forum: General Help
---

### Post by ChochiWpg on 2013-04-22
Hi Everyone,

The other day I was cleaning up apps I don't use on my Linux partition.  I would delete the apps through the Ubuntu Software Centre and noticed that the app dependencies were still present on the system after the deletion was complete.  I did a Google search and found out that by performing the task 'sudo apt-get autoremove' it removes all unused packages.  I also performed a 'sudo apt-get clean' and a 'sudo apt-get autoclean' to erase old and downloaded archive files.  Everything seemed to work out well and I didn't have any issues.

Yesterday I had to boot back into my Windows partition to run a program.  I was able to boot into the partition without issue and Windows started up and I was greeted with my desktop.  However, I couldn't get a network connection, any application I clicked on said I was missing important file dependencies for that app to run.  I also got errors with Network connection not present and when I try to add one it wouldn't work.  Checked my network drivers and it says the are installed correctly and functioning.

Could a Linux Terminal Command affect a Windows drive if the drive is mounted at the time the command is run?  I am just trying to figure out why I can't get a network connection now on my Windows partition and why I get an error message on almost every application I click on?  I don't know for sure if the drive was mounted when the commands were run, they may not have been, I am just thinking of reasons as to why I am getting these errors.  The only other reason I could think of is I also ran ClamTK last week on my Windows Drive and removed A LOT of detected threats.  Maybe those threats weren't threats after all?

Any ideas would be much appreciated.  Ubuntu is running great for me and is now my go to OS.  But I still want my Windows partition to work as well which it doesn't seem to be at the moment.  At least I have access to all my files on the drive and they are working great in Ubuntu.

Thanks.

---

### Post by CatKiller on 2013-04-22
The package manager won't have touched your Windows drive, but the anti-virus would.

---

### Post by ajgreeny on 2013-04-22
None of the commands you mention would have had any effect on your Win partition or files, and it would not have mattered whether the Win partition was mounted or not, as far as I'm aware, as they will only act on your Ubuntu system, nothing else.

My suspicion is that running clamtk may be your problem, and it could be worth looking at the logs of that particular activity to see what exactly was removed, and also perhaps if there is any possibility of restoration of deleted files.  I do not have windows any more, and therefore don't run clamav or clamtk, so I'm afraid I don't know if either will allow you to restore and backup removed threats, but it must be worth a look.

---

### Post by ChochiWpg on 2013-04-22
> **CatKiller said:**
> The package manager won't have touched your Windows drive, but the anti-virus would.

> **ajgreeny said:**
> None of the commands you mention would have had any effect on your Win partition or files, and it would not have mattered whether the Win partition was mounted or not, as far as I'm aware, as they will only act on your Ubuntu system, nothing else.

My suspicion is that running clamtk may be your problem, and it could be worth looking at the logs of that particular activity to see what exactly was removed, and also perhaps if there is any possibility of restoration of deleted files.  I do not have windows any more, and therefore don't run clamav or clamtk, so I'm afraid I don't know if either will allow you to restore and backup removed threats, but it must be worth a look.

Thanks guys,

That is what I suspected.  I installed Ubuntu April 13th and ran ClamTK at that time on my Windows partition.  Found well over 1000 threats which I quarantined.  It did take a long time to scan the entire drive (over 8 hours).  Since it was my first day running Ubuntu I did some research and found out that I don't need to have ClamTK installed or antivirus installed if I am running Ubuntu.  So I removed the program and haven't looked back, I have been running Ubuntu as my daily OS since then.

Yesterday was the first time I had to boot into Windows and like I mentioned it just started giving me errors.  I booted back in just now to record the errors.

connection status: unknown
This dependency service or group failed to start

Windows Defender
App failed to initialize: 0x800106ba.  A problem caused this programs service to stop.  To start the service, restart your computer or search Help and Support for how to start service manually.

Chrome
The item chrome.exe that this shortcut refers has been changed or moved, so this shortcut will no longer work properly.

Explore.exe
A device attached to system is not functioning.

Email
The item you selected is unavailable.  It might have been moved, renamed, or removed.  Do you want to remove it from the list?

Etc Etc, just nothing seems to work.  I guess if I want to use Windows I will have to do a restore.  But in doing so I will lose my Ubuntu partition that is working so well.  Before installing Ubuntu I made a system image so I can always go back.

The strange thing is I still have access to all my Windows files when I mount the drive in Ubuntu.  So I haven't needed to go back to Windows.  Maybe I just make the switch permanent and become a full time Ubuntu user?  IDK, suggestions?

---

### Post by prodigy_ on 2013-04-22
> **ChochiWpg said:**
> Found well over 1000 threats
This means reinstall in most cases anyway.

You don't need anti-virus as much in Linux. But on Windows machines you always should install some AV before *anything* else.

---

### Post by ChochiWpg on 2013-04-22
> **prodigy_ said:**
> This means reinstall in most cases anyway.

You don't need anti-virus as much in Linux. But on Windows machines you always should install some AV before *anything* else.

I have always run an antivirus program on Windows at all times.  But I was doing some reading and it was suggested it's a good idea to boot into Linux and run ClamTK to scan your Windows partition because some antivirus programs in Windows don't find all the threats.  So I was pleasantly surprised when ClamTK found numerous threats and allowed me to quarantine.  But I guess they weren't actual threats afterall.

I guess if I plan on using Windows I will have to figure out a way to recovery the Windows partition but keep the Ubuntu partition intact.  I will have a look.

---

### Post by r.stiltskin on 2013-04-22
The first lesson to take away from this is that you shouldn't let a program like this run amok through your files.  Scan them, sure, but pay attention to what it's doing and override it when necessary.  If in doubt check it out.

The good news is that if you haven't deleted the files from quarantine you should be able to restore them.  But BE CAREFUL.  In ClamTK click on Quarantine/Maintenance.  There you can select files and RESTORE them.  But be really careful that you don't click on delete or they're gone and you'll be reinstalling Windows, and that process, depending on what kind of Windows backup media you have (if you have any), might end up destroying your Linux installation too.

---

### Post by ChochiWpg on 2013-04-22
> **r.stiltskin said:**
> The first lesson to take away from this is that you shouldn't let a program like this run amok through your files.  Scan them, sure, but pay attention to what it's doing and override it when necessary.  If in doubt check it out.

The good news is that if you haven't deleted the files from quarantine you should be able to restore them.  But BE CAREFUL.  In ClamTK click on Quarantine/Maintenance.  There you can select files and RESTORE them.  But be really careful that you don't click on delete or they're gone and you'll be reinstalling Windows, and that process, depending on what kind of Windows backup media you have (if you have any), might end up destroying your Linux installation too.

I have since removed ClamTK, but when I get home from work I will reinstall and check the quarantine section to see if what was quarantined is still there.  I have a feeling it may not be, but we will see.

On another note, prior to even installing Ubuntu, I used CloneZilla to create a system image of Windows.  At the time of the system image I only had 2 partitions on my computer.  The C:/ drive which housed the Windows Vista OS and all my data/programs and the D:/ Drive which has the Factory Image.

I stored the image on an external Harddrive and then proceeded with the Ubuntu installation.  During the Installation I chose the something else option and created a 100GB Ubuntu partition from the free space on my C:/ Drive.  I then created a '/boot' '/' , '/home' and '/swap' partitions.  I also installed GRUB on the /boot partition and have the Windows boot loader controlling the dual boot process and not GRUB.

If I was to restore the image I created, can this be restored without affecting the Ubuntu partition?  Or will the restore restore everything back to how it was prior to installing Ubuntu?

---

### Post by r.stiltskin on 2013-04-22
WAIT
Before you reinstall ClamTK:

if you reinstall ClamTK it might overwrite (erase) any quarantine data left in your system from that scan.  

I strongly urge you to try to find the quarantine file created by ClamTK and make a backup copy of that file in a different location and different name BEFORE you reinstall the program.  Then if the reinstallation obliterates the original quarantine file you can replace it with a copy of the backup.

Not sure, but maybe you can find the file in your ~/.clamtk directory.

Regarding your clonezilla image:

From Clonezilla's website:
> Limitations:

    The destination partition must be equal or larger than the source one. 
    ...

So unless you resized (shrunk) your Windows partitions down to their current size before making the image, I think that restoring it will entail wiping out your entire Linux installation.

---

### Post by ChochiWpg on 2013-04-22
> **r.stiltskin said:**
> WAIT
Before you reinstall ClamTK:

if you reinstall ClamTK it might overwrite (erase) any quarantine data left in your system from that scan.  

I strongly urge you to try to find the quarantine file created by ClamTK and make a backup copy of that file in a different location and different name BEFORE you reinstall the program.  Then if the reinstallation obliterates the original quarantine file you can replace it with a copy of the backup.

Not sure, but maybe you can find the file in your ~/.clamtk directory.

Regarding your clonezilla image:

From Clonezilla's website:


So unless you resized (shrunk) your Windows partitions down to their current size before making the image, I think that restoring it will entail wiping out your entire Linux installation.

I will see if I can find the quarantined files left by ClamTK.  Thanks.

And regarding the restoring of Windows, that is what I was afraid of.  If I can't find the quarantined files I may just leave things as is because Ubuntu is running flawlessly and I can still access all my Windows files and I have access to all the free space on my Windows drive as well.  Would rather have a functioning/secure OS with access to all my data rather than wiping what I have and restoring Windows and have to reinstall Ubuntu all over again.

Thanks for your help.

---

### Post by r.stiltskin on 2013-04-22
Next time you're setting up a dual boot, make a backup image of your Windows, then use a Windows-based partition manager such as Easeus to resize the Windows partition(s) down to free the space you want for Linux, then make another backup image of the shrunken Windows so you'll be able to restore it without destroying Linux.

---

### Post by ChochiWpg on 2013-04-23
> **r.stiltskin said:**
> Next time you're setting up a dual boot, make a backup image of your Windows, then use a Windows-based partition manager such as Easeus to resize the Windows partition(s) down to free the space you want for Linux, then make another backup image of the shrunken Windows so you'll be able to restore it without destroying Linux.

Update,

It turns out the only way I was able to fix my issue with corrupt files in Windows was to restore my system image that was saved just prior to installing Ubuntu.  It ended up wiping Ubuntu and brining back my computer to exactly how it was before the install occurred.  I had a feeling that may happen, but on the bright side all of my files/data/apps are functioning properly.  It also isn't a huge issue to reinstall Ubuntu again from the Live DVD.  This time I will partition the drive in Windows first before proceeding with the install.  Also I will not run CkamTK, I learned my lesson the hard way.  The virus checker I have been using in Windows for years is doing a fine enough job I don't know why I insisted on giving another a try.

Anyway I just wanted to say thanks for your help, you learn something new everyday.

---

