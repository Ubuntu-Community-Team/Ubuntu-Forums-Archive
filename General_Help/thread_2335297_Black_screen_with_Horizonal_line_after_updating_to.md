---
title: "Black screen with Horizonal line after updating to 16.04"
date: 2016-08-27
forum: General Help
---

### Post by Kinshuk_Lahiri on 2016-08-27
Hello,

I was running on Ubuntu 15.10 version and today upgraded it to 16.04. My grub menu was not working earlier and I used the insmod normal in order to reach the ubuntu load screen. I have a UEFI based laptop with Hybrid cards one is Nvidia and another is intel. So now after updating it, at my screen it asked to restart the laptop and i hit the restart button and selected the Boot Options and selected Notebook Hardisk previously I also did the same to load ubuntu and as soon as I hit that button there was a black screen with a horizontal line constantly blinking and i kept the laptop in the same condition for around 15 mins but nothing changed and kept on blinking.

Please if anyone has any clue do help. Thanks

Hello,

Today upgraded ubuntu from 15.10 to 16.04 and after restarting the laptop can't see the grub menu. There is only a black screen with a line blinking and nothing is happening. Please someone help.

---

### Post by Bashing-om on 2016-08-27
Kinshuk_Lahiri; Hello;

That condition is indicative of a broken proprietary graphic's driver.
Check:
at the login screen key combo ctl+alt+F1 to gain a console interface.
Can you log into the system here with your credentials ? - username and password .
Look now to see if a driver is loaded :
Terminal command:
```

sudo lshw -C display

```
is a driver listed in the configuration line, and if so .. what ?

[INDENT][INDENT]a failure to communicate ?
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-08-27
You will find the answer in this thread.

[https://ubuntuforums.org/showthread.php?t=2335318](https://ubuntuforums.org/showthread.php?t=2335318)

It is a duplicate post from you of the same problem but with less information.

---

### Post by Kinshuk_Lahiri on 2016-08-27
Thanks for the reply. But at this point of time, I am not getting the grub menu. As it starts booting there is just a black screen with a line blinking. I searched for it and someone suggested to hold down the shift key and the grub menu will appear. But as I hold down the shift key there just appear the GRUB text and then the line blinking again. If you are facing any difficulty understanding it then do let me know I will provide screenshots so that you can get a better idea. Please help.

> **Bashing-om said:**
> Kinshuk_Lahiri; Hello;

That condition is indicative of a broken proprietary graphic's driver.
Check:
at the login screen key combo, ctl+alt+F1 to gain a console interface.
Can you log into the system here with your credentials ? - username and password .
Look now to see if a driver is loaded :
Terminal command:
```

sudo lshw -C display

```
is a driver listed in the configuration line, and if so .. what ?
[INDENT][INDENT]a failure to communicate ?
[/INDENT]
[/INDENT]


---

### Post by ajgreeny on 2016-08-27
We need to know a lot more about your machine hardware and the full situation that you are now in if we are to help you in any way.

See how to do so in much more detail at [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by Bashing-om on 2016-08-27
Kinshuk_Lahiri; Welll; 

UEFI endowed system ? Then it is the escape key that grub recognizes.
As soon as the firmware screen clears spam the escape key . - There is but a 3 second window of opportunity - 

Now does the grub boot menu appear ?

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by wildmanne39 on 2016-08-28
Please do not post duplicates, it dilutes community effort. Threads merged

---

### Post by Kinshuk_Lahiri on 2016-08-28
Hello,

Yes it is a UEFI system and is currently dual boot with Windows 10. So if I start the laptop and boot from harddisk and don't press any key then here is the screenshot of what I get. 

[http://prnt.sc/cb9iw3](http://prnt.sc/cb9iw3)

And after that you told me to hold down the esc key and it provided the same result which is [http://prnt.sc/cb9iw3](http://prnt.sc/cb9iw3) and no grub menu appeared.

As I told you that that if I hold shift key then I get the GRUB text and here is the screen shot for that. [http://prnt.sc/cb9jet](http://prnt.sc/cb9jet)

Hope it helps. I am not getting any grub menu at all. 

One more thing it is a HP laptop and to go to ubuntu I have to go to boot options and then select the harddisk other wise if I start the laptop then it loads Windows 10 directly. Please let me know if you need any more info.

> **Bashing-om said:**
> Kinshuk_Lahiri; Welll; 

UEFI endowed system ? Then it is the escape key that grub recognizes.
As soon as the firmware screen clears spam the escape key . - There is but a 3 second window of opportunity - 

Now does the grub boot menu appear ?
[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]


I have a HP laptop UEFI based which is dual boot with Ubuntu and Windows. THe specs are it has 8GB ram, Intel i 7 4th gen processor, Intel HD card and Nvidia Gefore 850m gtx. Beside that what other hardware info required please let me know. And also I have shared the situation with screenshots below and you can see it and can get better idea. Do let me know.

> **ajgreeny said:**
> We need to know a lot more about your machine hardware and the full situation that you are now in if we are to help you in any way.

See how to do so in much more detail at [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

Sorry for that. Thanks for merging the thread.

---

### Post by Bashing-om on 2016-08-28
Kinshuk_Lahiri; Ouch.

If you can not boot to the grub boot menu - then we have a problem. Try again that it is not a firmware setting that you can enable in this EFI mode to permit booting .
Else, we are looking at having to Re-install grub. The bad news here is that I have no direct experience with EFI systems thus I have no confidence in my ability to guide you in how to re-install grub .

We must have a terminal. somewhere
[INDENT][INDENT]to further the prosecution
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-08-28
I was also thinking about the same that I have to re-install grub. If I make a bootable USB and then run it on the device and then I get the terminal right and from there can you tell me what to do further and how to fix the issue. I have the ubuntu 15.04 ISO and the upgraded version is 16.04. So the 15.04 ISO will work or have to install the 16.04 ISO and make the bootable USB from that. Do let me know. 

Thanks for your help.

> **Bashing-om said:**
> Kinshuk_Lahiri; Ouch.

If you can not boot to the grub boot menu - then we have a problem. Try again that it is not a firmware setting that you can enable in this EFI mode to permit booting .
Else, we are looking at having to Re-install grub. The bad news here is that I have no direct experience with EFI systems thus I have no confidence in my ability to guide you in how to re-install grub .

We must have a terminal. somewhere[INDENT][INDENT]to further the prosecution
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-08-29
Kinshuk_Lahiri; Yuk . OK.

IF and only IF you are positive that this is a EFI system, and THAT by spamming the escape key the grub boot menu is NOT activated; then the next thing is to RE-install grub.

In preparation to re-install, let's look and make sure of our target to install to:
From that liveDVD boot to "try ubuntu" and key combo ctl+alt+t to activate a terminal.
Post pack the output of terminal command:
```

sudo parted -l 

```

and we see. Be aware I do not know that 15.04 and 16.04 remain compatible . Can not hurt to try 15.04 and see what results; so long as you have the means to burn a 16.04 live environment.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-08-29
I tried the escape key. As soon as it starts booting I hold down the esc key and nothing happened except the blinking. If you think i did it wrong, let me know I will try accordingly.

If you think that 15.04 can create some issue then do let me know, I will download 16.04 rather so that no problem can occur. Do let me know, and I will boot to the ubuntu from Pendrive as I don't have the DVD. Waiting for your reply. Thank you so much for taking out your time and helping me out.

> **Bashing-om said:**
> Kinshuk_Lahiri; Yuk . OK.

IF and only IF you are positive that this is a EFI system, and THAT by spamming the escape key the grub boot menu is NOT activated; then the next thing is to RE-install grub.

In preparation to re-install, let's look and make sure of our target to install to:
From that liveDVD boot to "try ubuntu" and key combo ctl+alt+t to activate a terminal.
Post pack the output of terminal command:
```

sudo parted -l 

```

and we see. Be aware I do not know that 15.04 and 16.04 remain compatible . Can not hurt to try 15.04 and see what results; so long as you have the means to burn a 16.04 live environment.
[INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-08-29
Kinshuk_Lahiri;

Always best to work on the install with the exact same release of the .iso .
Again. IF this is a EFI system - and we can verify from the liveUSB - it is the escape key that grub looks for. Rather than depressing and holding this escape key. one repeatedly (spams) depresses and releases the escape key to gets grub's attention.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-08-29
OK. As you said I multiple times hit the esc key repeatedly but nothing happened. The horizontal line was blinking and nothing else. So, i am downloading the ubuntu 16.04 version and will make a bootable pendrive from it and will run the command that you told earlier and will give you the ouput.

> **Bashing-om said:**
> Kinshuk_Lahiri;

Always best to work on the install with the exact same release of the .iso .
Again. IF this is a EFI system - and we can verify from the liveUSB - it is the escape key that grub looks for. Rather than depressing and holding this escape key. one repeatedly (spams) depresses and releases the escape key to gets grub's attention.
[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-08-29
Kinshuk_Lahiri; Great.

I await your advisement that you are booted 16.04 within the liveUSB 
posting the result of " sudo parted -l " .
Then we RE-install grub .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-08-30
OK. Finally I ran the command and below is the screenshot attached so that you can see the output. 

[http://prnt.sc/cby0r2](http://prnt.sc/cby0r2)

Do let me know the next step.

Thanks.

> **Bashing-om said:**
> Kinshuk_Lahiri; Great.

I await your advisement that you are booted 16.04 within the liveUSB 
posting the result of " sudo parted -l " .
Then we RE-install grub .
[INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-08-30
Kinshuk_Lahiri; OK;

Let's give this a try.
Booted up from the liveUSB in UEFI mode:
verify 1st that you are booted such :
```

ls -ld /sys/firmware/efi

```
should be similar:
" drwxr-xr-x 4 root root 0 Dec 25 23:25 /sys/firmware/efi".

Now we do a Full CHange Root, changing into the install from the liveUSB :
```

sudo mount /dev/sda6 /mnt # we mount the root partition of the install
sudo mount /dev/sda2 /mnt/boot/efi #sda2 # is the efi partition
for i in /dev /dev/pts /sys /proc /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
apt-get install --reinstall grub-efi-amd64-signed

```
#We install 'signed' for secure boot .
All done here .
Now gracefully back back out of the CHroot, so we know all files are properly closed out:
```

exit
for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
sudo umount /mnt/boot/efi #please do this. corrupted efi partitions are not nice
sudo umount /mnt
sudo reboot

```

Change in the firmware to boot the hard drive - In UEFI mode ! -

What results ? .. able now to boot to the grub boot menu ? Does the boot process continue to the GUI ?

What now remains to be fixed ?

[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-08-30
Thanks for the reply and the code. Just before I run the code just have a question in my mind. Can you tell me whether it will affect my windows partition in anyway because all my main data is there present in it and don't want to loose it and currently don't have anything to backup my data. And one more thing. I hope that in the whole process we don't need internet because in the try ubuntu version my wifi is not working somehow.

Waiting for the reply.

Thanks again.

> **Bashing-om said:**
> Kinshuk_Lahiri; OK;

Let's give this a try.
Booted up from the liveUSB in UEFI mode:
verify 1st that you are booted such :
```

ls -ld /sys/firmware/efi

```
should be similar:
" drwxr-xr-x 4 root root 0 Dec 25 23:25 /sys/firmware/efi".

Now we do a Full CHange Root, changing into the install from the liveUSB :
```

sudo mount /dev/sda6 /mnt # we mount the root partition of the install
sudo mount /dev/sda2 /mnt/boot/efi #sda2 # is the efi partition
for i in /dev /dev/pts /sys /proc /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
apt-get install --reinstall grub-efi-amd64-signed

```
#We install 'signed' for secure boot .
All done here .
Now gracefully back back out of the CHroot, so we know all files are properly closed out:
```

exit
for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
sudo umount /mnt/boot/efi #please do this. corrupted efi partitions are not nice
sudo umount /mnt
sudo reboot

```

Change in the firmware to boot the hard drive - In UEFI mode ! -

What results ? .. able now to boot to the grub boot menu ? Does the boot process continue to the GUI ?

What now remains to be fixed ?[INDENT][INDENT][INDENT]maybe yes
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-08-30
Kinshuk_Lahiril Well ..

As we are not touching any Windows partitions; all we are doing is re-adding ubuntu to the boot menu, making sure that the config files are in place - I do not expect to effect Windows in any way . 
sda2 is identified as the efi partition
sda6 is identified as ubuntu root partition.

Feel free to express any concerns, or further explanation for anything that I have failed to explain.
As I have said, I have limited experience with UEFI and my Windows days are far far behind me. However, I see no fault with my logic.

We can await review of this thread by others for a 2nd/3rd opinion; will not hurt my feelings in the least to have confirmation .

[INDENT][INDENT]flying by the seat of our pants
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-08-30
Since you have already enough experience. I am going to run the code and hope for the best. Will come back to you soon with the result.

> **Bashing-om said:**
> Kinshuk_Lahiril Well ..

As we are not touching any Windows partitions; all we are doing is re-adding ubuntu to the boot menu, making sure that the config files are in place - I do not expect to effect Windows in any way . 
sda2 is identified as the efi partition
sda6 is identified as ubuntu root partition.

Feel free to express any concerns, or further explanation for anything that I have failed to explain.
As I have said, I have limited experience with UEFI and my Windows days are far far behind me. However, I see no fault with my logic.

We can await review of this thread by others for a 2nd/3rd opinion; will not hurt my feelings in the least to have confirmation .
[INDENT][INDENT]flying by the seat of our pants
[/INDENT]
[/INDENT]


OK. So for the first command which is :
```
[COLOR=#000000][FONT=&amp]ls -ld /sys/firmware/efi[/FONT][/COLOR]
```
I tried it. And it gave me similar result as you told.

```
[COLOR=#000000][FONT=&amp]sudo mount /dev/sda6 /mnt[/FONT][/COLOR]
``` 

Tried this and it ran and there was no output for it. Then I ran this command:

```
[COLOR=#000000][FONT=&amp]sudo mount /dev/sda2 /mnt/boot/efi[/FONT][/COLOR]
```

And it gave me an error. Please check the screenshot.

[http://prnt.sc/cc6wp3](http://prnt.sc/cc6wp3). 

Please let me know what I did wrong.

Thanks

> **Bashing-om said:**
> Kinshuk_Lahiril Well ..

As we are not touching any Windows partitions; all we are doing is re-adding ubuntu to the boot menu, making sure that the config files are in place - I do not expect to effect Windows in any way . 
sda2 is identified as the efi partition
sda6 is identified as ubuntu root partition.

Feel free to express any concerns, or further explanation for anything that I have failed to explain.
As I have said, I have limited experience with UEFI and my Windows days are far far behind me. However, I see no fault with my logic.

We can await review of this thread by others for a 2nd/3rd opinion; will not hurt my feelings in the least to have confirmation .
[INDENT][INDENT]flying by the seat of our pants
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-08-30
Kinshuk_Lahiri; Humm ...

You have done nothing wrong . Maybe we need to explicitly declare  that mount point for the efi partition.
Let's run:
```

sudo mkdir /mnt/boot/efi
sudo mount /dev/sda2 /mnt/boot/efi
sudo mount /dev/sda6 /mnt
for i in /dev /dev/pts /sys /proc /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
apt-get install --reinstall grub-efi-amd64-signed

```

Does this work ?

[INDENT][INDENT]more than one path to an end
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-08-30
Ok, I tried this too and it gave me the error. Screenshot attached below.

[http://prnt.sc/cccjrm](http://prnt.sc/cccjrm)

> **Bashing-om said:**
> Kinshuk_Lahiri; Humm ...

You have done nothing wrong . Maybe we need to explicitly declare that mount point for the efi partition.
Let's run:
```

sudo mkdir /mnt/boot/efi
sudo mount /dev/sda2 /mnt/boot/efi
sudo mount /dev/sda6 /mnt
for i in /dev /dev/pts /sys /proc /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
apt-get install --reinstall grub-efi-amd64-signed

```

Does this work ?
[INDENT][INDENT]more than one path to an end
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-08-30
Kinshuk_Lahiri; Yuk !

Something strange going on here that the directory does not exist - me thinks .
Will do some homework on this to find what should exist in a EFI install .

[INDENT][INDENT]sometimes
[INDENT][INDENT][INDENT]I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-08-31
OK, Looking forward for your reply.

> **Bashing-om said:**
> Kinshuk_Lahiri; Yuk !

Something strange going on here that the directory does not exist - me thinks .
Will do some homework on this to find what should exist in a EFI install .
[INDENT][INDENT]sometimes[INDENT][INDENT][INDENT]I just do not know
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-08-31
Kinshuk_Lahiri; Morning .

I have been hard at work on this, and I do continue .
To this time I find no fault with my logic.
looking at:
[https://wiki.archlinux.org/index.php/EFI_System_Partition](https://wiki.archlinux.org/index.php/EFI_System_Partition)
> 
Warning: If dual-booting with an existing installation of Windows on a UEFI/GPT system, avoid reformatting the UEFI partition, as this includes the Windows .efi file required to boot it. In other words, use the existing partition as is and simply #Mount the partition.


[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
and we see :
> 
Different distributions' installers have different ways of identifying the ESP. For instance, some versions of Debian and Ubuntu call the ESP the "EFI boot partition" and do not show you an explicit mount point (although it will mount it behind the scenes); but a distribution like Arch or Gentoo will require you to mount it. The closest thing to a standard ESP mount point in Linux is /boot/efi

so we know we are on the right path .
Now if I can just come up with a means to mount that partition and then see what the file system contains ! I am working on that !

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-08-31
Good Morning,

Thanks for taking out time out of your busy life for me. I am really thankful to you. Do let me know, about your findings. Fingers crossed and hope for the best.

Thanks again.

> **Bashing-om said:**
> Kinshuk_Lahiri; Morning .

I have been hard at work on this, and I do continue .
To this time I find no fault with my logic.
looking at:
[https://wiki.archlinux.org/index.php/EFI_System_Partition](https://wiki.archlinux.org/index.php/EFI_System_Partition)


[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
and we see :

so we know we are on the right path .
Now if I can just come up with a means to mount that partition and then see what the file system contains ! I am working on that !
[INDENT][INDENT]it's 'buntu[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-08-31
Kinshuk_Lahiri; Hey ..

It is a learning thing for me also . And, these puzzles sure beat jig saw puzzles !

Look, indications are so far that we have a hosed up /boot/efi partition. We want to verify this as we do not want to mess up Windows'.

Return to square 1 with the troubleshooting:
post back to this thread - using code tags - rather than a screen shot.
show me:
```

sudo parted /dev/sda print

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
As code tag is much quicker and easier to work with - what I do is difficult enough as is .
and we verify the partition parameters . Then see where we go from here - again .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-08-31
You want the output of this:
```
[COLOR=#000000][FONT=&quot]sudo parted /dev/sda print[/FONT][/COLOR]
```

Do let me know.

> **Bashing-om said:**
> Kinshuk_Lahiri; Hey ..

It is a learning thing for me also . And, these puzzles sure beat jig saw puzzles !

Look, indications are so far that we have a hosed up /boot/efi partition. We want to verify this as we do not want to mess up Windows'.

Return to square 1 with the troubleshooting:
post back to this thread - using code tags - rather than a screen shot.
show me:
```

sudo parted /dev/sda print

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
As code tag is much quicker and easier to work with - what I do is difficult enough as is .
and we verify the partition parameters . Then see where we go from here - again .
[INDENT][INDENT]inquiring minds want to know
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-08-31
Kinshuk_Lahiri; yeah.

> 
You want the output of this:
Code:
sudo parted /dev/sda print

Affirmative. We start all over as I do not want to inhibit or damage Windows. We exercise the care .

[INDENT]careful is no accident
[/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-08-31
Ok. I am on Ubuntu and finally came to know how to enable Wifi while Trying ubuntu. Making some progress :) Here is the output:

```
sudo parted /dev/sda print 
Model: ATA HGST HTS541010A9 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  683MB   682MB   ntfs         Basi  hidden, diag
 2      683MB   955MB   273MB   fat32        EFI   boot, esp
 3      955MB   1089MB  134MB                Micr  msftres
 4      1089MB  922GB   921GB   ntfs               msftdata
 5      922GB   923GB   894MB   ntfs               hidden, diag
 6      923GB   977GB   54.4GB  ext4
 7      978GB   1000GB  22.1GB  ntfs         Basi  hidden, msftdata


```

> **Bashing-om said:**
> Kinshuk_Lahiri; yeah.


Affirmative. We start all over as I do not want to inhibit or damage Windows. We exercise the care .[INDENT]careful is no accident
[/INDENT]


---

### Post by Bashing-om on 2016-08-31
Kinshuk_Lahiri; OK;

That says definitely that sda2 is the efi boot partition:
> 
Disk /dev/sda: 1000GB
2      683MB   955MB   273MB   fat32        EFI   boot, esp

and is set as boot.
There should be no reason that we can not mount it as doing this:
```

sudo mount /dev/sda2 /boot/efi

```
and with this:
```

ls -al /boot/efi

```
we list it's contents.

So, doing this, what results ?

[INDENT][INDENT]a process of fault isolation
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-08-31
Ok i tried the first command and it gave me the following output:

```

$ sudo mount /dev/sda2 /boot/efi
mount: mount point /boot/efi does not exist

```

And for the second code:
```
$ ls -al /boot/efi
ls: cannot access '/boot/efi': No such file or directory

```

I went on searching for this problem on the internet and found something here:

[http://askubuntu.com/questions/335441/boot-efi-cant-be-mounted-after-kernel-update-ubuntu-13-04](http://askubuntu.com/questions/335441/boot-efi-cant-be-mounted-after-kernel-update-ubuntu-13-04)

So then I ran the first command:

```
grep efi /etc/fstab
```

And it returned nothing. And below, someone suggested that if it returns nothing then run this command which I haven't ran till now:

```
sudo dosfsck -a /dev/sda2
```

Do let me know if i should run it or not. And more command that i ran is mentioned below with the output:

```
sudo blkid
/dev/sda1: LABEL="WINRE" UUID="32A0DF9EA0DF673F" TYPE="ntfs" PARTLABEL="Basi" PARTUUID="39e7b58a-3820-4ea9-bd89-db89bc516a57"
/dev/sda2: UUID="AC3F-A5BB" TYPE="vfat" PARTLABEL="EFI" PARTUUID="a39d70f3-f82f-46c4-8526-549b0e0f821d"
/dev/sda4: LABEL="Windows" UUID="1C16D94E16D92A12" TYPE="ntfs" PARTUUID="e63c2f35-f340-4777-9fb3-44f6df9335af"
/dev/sda5: UUID="8CF275DEF275CCC8" TYPE="ntfs" PARTUUID="331f69ef-acff-4351-b889-d3a4db1c7366"
/dev/sda6: UUID="9f3280da-b24c-4c2f-95f5-dfc064312dc6" TYPE="ext4" PARTUUID="d9820c1a-1cb5-4918-b0dd-5c5e2ff29477"
/dev/sda7: LABEL="RECOVERY" UUID="5454DC9854DC7E64" TYPE="ntfs" PARTLABEL="Basi" PARTUUID="3bb944bc-c74a-4088-98ab-c60dad9ac0bd"
/dev/sdb1: LABEL="UBUNTU 16_0" UUID="78C3-323B" TYPE="vfat" PARTUUID="0044760f-01"
/dev/loop0: TYPE="squashfs"
/dev/sda3: PARTLABEL="Micr" PARTUUID="e622098b-ddcf-4f18-a54c-3d9aec6cf8fe"

```

Do let me know. Thanks

> **Bashing-om said:**
> Kinshuk_Lahiri; OK;

That says definitely that sda2 is the efi boot partition:

and is set as boot.
There should be no reason that we can not mount it as doing this:
```

sudo mount /dev/sda2 /boot/efi

```
and with this:
```

ls -al /boot/efi

```
we list it's contents.

So, doing this, what results ?
[INDENT][INDENT]a process of fault isolation
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-08-31
Kinshuk_Lahiri; Welp;

Before we get aggressive in attempting a file system repair;
Make sure that fast boot in Windows is not a factor. that the Windows feature is disabled !
How about we take Rod Smith's hint and check the /etc/fstab and make sure that the entry is present and correct ?
From the liveUSB :
```

sudo mkdir /mnt/looksee
sudo mount /dev/sda6 /mnt/looksee
cat /mnt/looksee/etc/fstab

```

Once the info if obtained we MUST unmount what we have mounted , before we reboot or shut down the system. Else file system damage can occur at some level.
UNmount what we have mounted.
```

sudo umount /mnt/looksee

```

[INDENT][INDENT]just another step
[INDENT][INDENT][INDENT]in the process of fault isolation
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-08-31
Ok so here is the output that i get:

```
ubuntu@ubuntu:~$ sudo mkdir /mnt/looksee
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/looksee
ubuntu@ubuntu:~$ cat /mnt/looksee/etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=9f3280da-b24c-4c2f-95f5-dfc064312dc6 /               ext4    errors=remount-ro 0       1


```

Do let me know what to do next.

> **Bashing-om said:**
> Kinshuk_Lahiri; Welp;

Before we get aggressive in attempting a file system repair;
Make sure that fast boot in Windows is not a factor. that the Windows feature is disabled !
How about we take Rod Smith's hint and check the /etc/fstab and make sure that the entry is present and correct ?
From the liveUSB :
```

sudo mkdir /mnt/looksee
sudo mount /dev/sda6 /mnt/looksee
cat /mnt/looksee/etc/fstab

```

Once the info if obtained we MUST unmount what we have mounted , before we reboot or shut down the system. Else file system damage can occur at some level.
UNmount what we have mounted.
```

sudo umount /mnt/looksee

```
[INDENT][INDENT]just another step[INDENT][INDENT][INDENT]in the process of fault isolation
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-01
Kinshuk_Lahiri; Well, well, well ...

Is Rod smart or what ! .. He called this one!
We must make the appropriate entry in the File System TABle .
As before mount the install's root partition

EDIT:
```

sudo mkdir /mnt/looksee
sudo mount /dev/sda6 /mnt/looksee

```

Make a back up copy of any file prior to editing - SOP - Bad things do happen at the best of times.
```

sudo cp /mnt/looksee/etc/fstab /mnt/looksee/etc/fstab-31Aug2016

```
and now we fire up a text editor with the privileges to edit a system file:
```

sudo -H gedit /mnt/looksee/etc/fstab

```
enter these lines:
```

# /boot/efi has been determined to be on /dev/sda2 for this install
UUID=AC3F-A5BB  /boot/efi   vfat    defaults    0   1

```
while here may as well update the root partition's comment line to reflect what is true.
where presently is inaccurate " was on /dev/sda7 during installation" as we know it is now sda6.
Maybe something like " # / is now - 31Aug2016 - on sda6 " . 

save the file and exit the text editor .

UNmount what we mounted - remember !
```

sudo umount /mnt/looksee

```

reboot the system setting in the firmware to boot the hard drive.

Now what happens ?

[INDENT][INDENT]maybe YES
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-09-01
Kinshuk_Lahiri;  Hey;

I an done for this session; eyes are crossing, and mind is cloudy.
When I get my chores done will be back here to check your status tomorrow.

[INDENT][INDENT]fingers crossed
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-09-01
Kinshuk_Lahiri; Morning ...

Well what have we now ?

I also note there is no provision for swapping . Is this a problem also ? ... How much ram do you have installed ?
```

free -m

```
and do you intend that this machine have the capability to hibernate ?

[INDENT][INDENT]oh what do we do
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-01
I haven't ran those command yet. I just returned home from work. And about to run the commands.

Here is the output for the memory checker code:

```
$ free -m
              total        used        free      shared  buff/cache   available
Mem:           7913         814        5346         331        1753        6470
Swap:             0           0           0


```

In Windows, yes it has the option to hibernate. Do let me know, that I should run those commands or not? 

Thanks
> **Bashing-om said:**
> Kinshuk_Lahiri; Morning ...

Well what have we now ?

I also note there is no provision for swapping . Is this a problem also ? ... How much ram do you have installed ?
```

free -m

```
and do you intend that this machine have the capability to hibernate ?
[INDENT][INDENT]oh what do we do
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-01
Kinshuk_Lahiri; Hey,

With 8 gigs of ram installed in "normal" day to day operations you will not need a swap partition; however, with no swap you will not have the option in ubuntu to hibernate the machine. As fast as it boots up this should not be an obstacle. 

So it is back to the booting issue. Go ahead and make the recommended edit to the /etc/fstab file, and we see what results.

[INDENT][INDENT]one thing at a time
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-01
Just one little thing to ask before i proceed.

```
UUID=9f3280da-b24c-4c2f-95f5-dfc064312dc6 /               ext4    errors=remount-ro 0       1
```

What to do with this? Should i add a ```
#
``` before it? Do let me know,

Thanks

> **Bashing-om said:**
> Kinshuk_Lahiri; Hey,

With 8 gigs of ram installed in "normal" day to day operations you will not need a swap partition; however, with no swap you will not have the option in ubuntu to hibernate the machine. As fast as it boots up this should not be an obstacle. 

So it is back to the booting issue. Go ahead and make the recommended edit to the /etc/fstab file, and we see what results.
[INDENT][INDENT]one thing at a time
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-01
Kinshuk_Lahiri; Well;

The '#" character at the start of the line tells the system this line is a comment only and not to be parsed . So, No, in this instance DO NOT comment out mounting the root partition. Comments in a file are for human comprehension . And we want that the system ignores these human readable comments . Does this make sense ?

Be aware in the edit " UUID=AC3F-A5BB  /boot/efi   vfat    defaults    0   1 " I did see where it might be required - "UUID=AC3F-A5BB" -; though I am not familiar with this formatting as I have never encountered a requirement to quote the UUID .

[INDENT][INDENT]always open
[INDENT][INDENT][INDENT]to learn
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-01
so I souldn't comment out that line and run it as it is and insert the new line below it?

> **Bashing-om said:**
> Kinshuk_Lahiri; Well;

The '#" character at the start of the line tells the system this line is a comment only and not to be parsed . So, No, in this instance DO NOT comment out mounting the root partition. Comments in a file are for human comprehension . And we want that the system ignores these human readable comments . Does this make sense ?

Be aware in the edit " UUID=AC3F-A5BB  /boot/efi   vfat    defaults    0   1 " I did see where it might be required - "UUID=AC3F-A5BB" -; though I am not familiar with this formatting as I have never encountered a requirement to quote the UUID .
[INDENT][INDENT]always open[INDENT][INDENT][INDENT]to learn
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-01
Kinshuk_Lahiri; Uh Huh .

> 
so I souldn't comment out that line and run it as it is and insert the new line below it?

affirmative;
Ya want to add to the file below what is present; these 2 lines:
```

# /boot/efi has been determined to be on /dev/sda2 for this install
UUID=AC3F-A5BB  /boot/efi   vfat    defaults    0   1

```
where the 1st line is for human understanding only - commented (#) .
save the file and exit the text editor ( here gedit, your favorite editor may be different) .

[INDENT][INDENT]lessons n system administration
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-01
So here is the thing that I am going to add in the file:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# /  is now - 31Aug2016 - on sda6
UUID=9f3280da-b24c-4c2f-95f5-dfc064312dc6 /               ext4    errors=remount-ro 0       1
# /boot/efi has been determined to be on /dev/sda2 for this install
UUID=AC3F-A5BB  /boot/efi   vfat    defaults    0   1
```

Do let me know if anything is there to change?

> **Bashing-om said:**
> Kinshuk_Lahiri; Uh Huh .


affirmative;
Ya want to add to the file below what is present; these 2 lines:
```

# /boot/efi has been determined to be on /dev/sda2 for this install
UUID=AC3F-A5BB  /boot/efi   vfat    defaults    0   1

```
where the 1st line is for human understanding only - commented (#) .
save the file and exit the text editor ( here gedit, your favorite editor may be different) .[INDENT][INDENT]lessons n system administration
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-01
Kinshuk_Lahiri; Yepper;

That ^ should work .
Looks good to me.

Save the file, exit out of the text editor , unmount /mnt/looksee.
reboot, set the boot priority to the hard drive, 


[INDENT][INDENT]let's see what happens
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-01
Ok. Did everything. Then used the reboot command. And it restarted the laptop and then went to boot options and then booted from the harddisk and it gave me the same horizontal line blinking. And nothing happened.

So, I went ahead and now I am booted again through the live usb  and i ran the code and the output can be seen below. Let me know what should we do next.

```
cat /mnt/looksee/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# /  is now - 31Aug2016 - on sda6
UUID=9f3280da-b24c-4c2f-95f5-dfc064312dc6 /               ext4    errors=remount-ro 0       1
# /boot/efi has been determined to be on /dev/sda2 for this install
UUID=AC3F-A5BB  /boot/efi   vfat    defaults    0   1


```

Thanks
> **Bashing-om said:**
> Kinshuk_Lahiri; Yepper;

That ^ should work .
Looks good to me.

Save the file, exit out of the text editor , unmount /mnt/looksee.
reboot, set the boot priority to the hard drive, 

[INDENT][INDENT]let's see what happens
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-01
Kinshuk_Lahiri; Well;

Let's poke at it some more:
> 
And it restarted the laptop and then went to boot options and then booted from the harddisk and it gave me the same horizontal line blinking.


As we now get to grub's boot menu; what results when booting a recovery kernel in the install ?

In the install, boot to grub -> advanced options -> recovery kernel.
What results when choosing this boot ?

[INDENT][INDENT]poke at it 'til something gives
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-01
> As we now get to grub's boot menu; what results when booting a recovery kernel in the install ?

In the install, boot to grub -> advanced options -> recovery kernel.
What results when choosing this boot ?

Sorry, I didn't get any of this. Can you please explain in detail and break down into steps. 

When you said:

> As we now get to grub's boot menu; what results when booting a recovery kernel in the install ?
Where I boot? Where is the recovery kernel.

Do let me know. Thanks
> **Bashing-om said:**
> Kinshuk_Lahiri; Well;

Let's poke at it some more:


As we now get to grub's boot menu; what results when booting a recovery kernel in the install ?

In the install, boot to grub -> advanced options -> recovery kernel.
What results when choosing this boot ?[INDENT][INDENT]poke at it 'til something gives
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-01
Kinshuk_Lahiri; Ouch .....

Do we have a language problem ? As English is the only language I can converse in and when you say:
> 
And it restarted the laptop and then went to boot options 

did I misunderstand ? In that what is meant here is the firmware boot options rather then grub's boot menu option ?

Are we back to trying to mount and access the /boot/efi partition - I had "thought" we were past that ???

As I have advised . I have limited familiarity with EFI systems .. and I do not have access to one to have a ready reference for what to expect.

[INDENT][INDENT]me and my tunnel vision
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-01
Sorry, I confused you.

I will clear it out. I entered the reboot command and then the laptop restarted. Since I have a HP laptop and hence I have to press the esc key to pause the start up. Once it paused, I pressed the F9 button to go to the boot options. In this boot options, I had USB drive and the Notebook hardrive with some efi options as well. So, there I selected the Notebook harddrive. And at the starting, if you remember I said I was getting a horizontal line and i posted the screenshot for it which is [http://prnt.sc/cb9iw3](http://prnt.sc/cb9iw3) . I am still getting it.

No grub menu is there. If i hold down the shift key, then I get this: [http://prnt.sc/cb9jet](http://prnt.sc/cb9jet)

Do let me know, what should we do? And I am again sorry for confusing you.

> **Bashing-om said:**
> Kinshuk_Lahiri; Ouch .....

Do we have a language problem ? As English is the only language I can converse in and when you say:

did I misunderstand ? In that what is meant here is the firmware boot options rather then grub's boot menu option ?

Are we back to trying to mount and access the /boot/efi partition - I had "thought" we were past that ???

As I have advised . I have limited familiarity with EFI systems .. and I do not have access to one to have a ready reference for what to expect.
[INDENT][INDENT]me and my tunnel vision
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-01
Kinshuk_Lahiri; OK !

Now that I do understand that when you boot, you boot to a "grub >" prompt.
What that means is that grub can not find the kernel config files. 
In this case I do think the best course of action is to re-install grub, such that then it will re-configure and hopefully find the kernel's config files. 

And, now, in small steps to the end of re-installing grub .. can we now mount the /boot/efi partition ?
From the liveUSB:
```

mount /dev/sda1 /boot/efi

```
If it mounts now .. what returns:
```

df /boot/efi

```

Also, as another thought - as the install used to be sda7 and is now sda6 .. maybe we need to look at grub's config file and make sure that grub has the correct UUIDs to boot from ? 

the more we poke, the more we learn;
[INDENT][INDENT][INDENT]the more we know
[/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-01
When I boot from firmware, I never see "grub >". Earlier when I was on 15.10 I used to see this but after upgrading I don't.

Here is the output of the code:

```
 mount /dev/sda1 /boot/efi
mount: only root can do that
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /boot/efi
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.


```

Do let me know, Thanks
> **Bashing-om said:**
> Kinshuk_Lahiri; OK !

Now that I do understand that when you boot, you boot to a "grub >" prompt.
What that means is that grub can not find the kernel config files. 
In this case I do think the best course of action is to re-install grub, such that then it will re-configure and hopefully find the kernel's config files. 

And, now, in small steps to the end of re-installing grub .. can we now mount the /boot/efi partition ?
From the liveUSB:
```

mount /dev/sda1 /boot/efi

```
If it mounts now .. what returns:
```

df /boot/efi

```

Also, as another thought - as the install used to be sda7 and is now sda6 .. maybe we need to look at grub's config file and make sure that grub has the correct UUIDs to boot from ? 

the more we poke, the more we learn;[INDENT][INDENT][INDENT]the more we know
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-01
Kinshuk_Lahiri; And ...

Back to this:
> 
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting)

Boot back into Windows .. and insure that you have fully shut the system down .,.. no hibernation NO fast boot enabled .
These keep the partition occupied and ubuntu WILL not mount and or mess with the partitions while Windows has a lock on them .

as to:
> 
mount: only root can do that

is a true statement, that is the result of my not focusing properly,
the command should have elevated privileges, as in:
```

sudo mount /dev/sda1 /boot/efi

```

so, make sure that Windows is completely shut down ... and try from the liveUSB once more to mount the /boot/efi partition.

[INDENT][INDENT]sometimes I do wonder
[INDENT][INDENT][INDENT]other times, I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-01
Ok, so just did that and here is the output:

```
ubuntu@ubuntu:~$ mount /dev/sda1 /boot/efi
mount: only root can do that
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /boot/efi
ntfs-3g-mount: failed to access mountpoint /boot/efi: No such file or directory


```

Earlier I guess, we were mounting sda2 for the boot/efi or I could be wrong? Do let me know.

Thanks

> **Bashing-om said:**
> Kinshuk_Lahiri; And ...

Back to this:

Boot back into Windows .. and insure that you have fully shut the system down .,.. no hibernation NO fast boot enabled .
These keep the partition occupied and ubuntu WILL not mount and or mess with the partitions while Windows has a lock on them .

as to:

is a true statement, that is the result of my not focusing properly,
the command should have elevated privileges, as in:
```

sudo mount /dev/sda1 /boot/efi

```

so, make sure that Windows is completely shut down ... and try from the liveUSB once more to mount the /boot/efi partition.
[INDENT][INDENT]sometimes I do wonder[INDENT][INDENT][INDENT]other times, I just do not know
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-01
Kinshuk_Lahiri; eeerkkk ..

Yes, you are correct, it is sda2 that is our target . Sorry was working a similar grub issue where that boot partition was and is sda1 . Ouch .
Sorry 'bout that .

So what now with the correct target :
```

sudo mount /dev/sda2 /boot/efi

```
with 'sudo' for the elevated administrative privilege ??

[INDENT][INDENT]maybe
[INDENT][INDENT]but I just have to wait and see
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-02
For sda 2 it gives the same response:

```
$ sudo mount /dev/sda2 /boot/efi
mount: mount point /boot/efi does not exist

```

> **Bashing-om said:**
> Kinshuk_Lahiri; eeerkkk ..

Yes, you are correct, it is sda2 that is our target . Sorry was working a similar grub issue where that boot partition was and is sda1 . Ouch .
Sorry 'bout that .

So what now with the correct target :
```

sudo mount /dev/sda2 /boot/efi

```
with 'sudo' for the elevated administrative privilege ??
[INDENT][INDENT]maybe[INDENT][INDENT]but I just have to wait and see
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-02
Kinshuk_Lahiri;; WeeLLLL ;

I am stuck, I am hesitant to suggest anything else at this point . Let me sleep on it and see what I can come up with .

Presently I can not understand why the system says the mount point  "does not exist" when clearly the partition is there !

[INDENT][INDENT]presently;
[INDENT][INDENT][INDENT]I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-09-02
Kinshuk_Lahiri; Hey :

After sleeping on it, I do have another idea.
Let's see what the tool efibootmgr can and will tell us.
In the liveUSB install the tool:
```

sudo apt install efibootmgr

```
and see what it now tells us about the /boot/efi partition:
```

sudo efibootmgr -v

```
Beating in mind we may get a good result if we were to enclose the UUID of the /boot/efi partition, in the file /etc/fstab, in the quotes (??) .


Still, as the partition does exist, why oh why can we not mount it ??

[INDENT][INDENT]inquiring minds want o know
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-02
Here is the output for first code:

```
ubuntu@ubuntu:~$ sudo apt install efibootmgr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
efibootmgr is already the newest version (0.12-4).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

And for the second code:

```
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0001,3001,2001,2002,2003
Boot0000*  USB Hard Drive - hp      v228g     BBS(7,,0x500)..................................................................\.........A.....................
Boot0001*  Windows Boot Manager     HD(2,GPT,a39d70f3-f82f-46c4-8526-549b0e0f821d,0x145800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}.../................
Boot0002*  Notebook Hard Drive - HGST HTS541010A9E680     BBS(HD,,0x500)................-...........A......................................5........A.........................
Boot0003* USB Hard Drive (UEFI) - hp      v228g    PciRoot(0x0)/Pci(0x14,0x0)/USB(5,0)/HD(1,MBR,0x15,0x800,0x1df2f00)RC
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC
Boot3001* Internal Hard Disk or Solid State Disk    RC
Boot3002* Internal Hard Disk or Solid State Disk    RC
Boot3003* Internal Hard Disk or Solid State Disk    RC

```

> **Bashing-om said:**
> Kinshuk_Lahiri; Hey :

After sleeping on it, I do have another idea.
Let's see what the tool efibootmgr can and will tell us.
In the liveUSB install the tool:
```

sudo apt install efibootmgr

```
and see what it now tells us about the /boot/efi partition:
```

sudo efibootmgr -v

```
Beating in mind we may get a good result if we were to enclose the UUID of the /boot/efi partition, in the file /etc/fstab, in the quotes (??) .


Still, as the partition does exist, why oh why can we not mount it ??
[INDENT][INDENT]inquiring minds want o know
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-02
Kinshuk_Lahiri; Well, well .....

In that output I do not see a boot entry for ubuntu !

Now it is back to homework and learn how to make that boot entry .

[INDENT][INDENT]light at the end of the tunnel
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-02
Ok. Do let me know whatever you find. I am also doing some research at my end as well.

Thanks
> **Bashing-om said:**
> Kinshuk_Lahiri; Well, well .....

In that output I do not see a boot entry for ubuntu !

Now it is back to homework and learn how to make that boot entry .
[INDENT][INDENT]light at the end of the runnel
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-02
Kinshuk_Lahiri; Hey;

Still scratching my head at this as I still do not understand why we can not mount the efi partition.

However, let us take this poke at it:
from the liveUSB, run:
```

sudo efibootmgr -c -g -d /dev/sda -p 2 -w -L "ubuntu" -l '\EFI\Boot\bootx64.efi'

``` 
reboot into the install .

Let's see if there is any effect .

[INDENT][INDENT]right wrong or otherwise
[INDENT][INDENT][INDENT]do something
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-02
In the code, it should be sda or sda 2? Do let me know..

> **Bashing-om said:**
> Kinshuk_Lahiri; Hey;

Still scratching my head at this as I still do not understand why we can not mount the efi partition.

However, let us take this poke at it:
from the liveUSB, run:
```

sudo efibootmgr -c -g -d /dev/sda -p 2 -w -L "ubuntu" -l '\EFI\Boot\bootx64.efi'

``` 
reboot into the install .

Let's see if there is any effect .
[INDENT][INDENT]right wrong or otherwise[INDENT][INDENT][INDENT]do something
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-03
Kinshuk_Lahiri; Hello;

I think as given - I can however make errors -; in this case we reference the device 'sda', and the partition (2) is given by " p 2 " .

I will not be surprised if it fails due to the system not able to identify the /boot/efi (sda2) . But even in the failure, perhaps we gain additional info to point us to a means of resolution . I am trying real hard here not to mess up the Windows booting ! And, believe me I do not know what we are doing . This is all new territory to me - I learn as we go .

[INDENT][INDENT]all in the process of learning
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-03
Here is the output:

```
sudo efibootmgr -c -g -d /dev/sda -p 2 -w -L "ubuntu" -l '\EFI\Boot\bootx64.efi'
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0004,0001,3001,2001,2002,2003
Boot0000* USB Hard Drive - hp      v228g
Boot0001* Windows Boot Manager
Boot0002* Notebook Hard Drive - HGST HTS541010A9E680
Boot0003* USB Hard Drive (UEFI) - hp      v228g
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk
Boot0004* ubuntu


```

> **Bashing-om said:**
> Kinshuk_Lahiri; Hello;

I think as given - I can however make errors -; in this case we reference the device 'sda', and the partition (2) is given by " p 2 " .

I will not be surprised if it fails due to the system not able to identify the /boot/efi (sda2) . But even in the failure, perhaps we gain additional info to point us to a means of resolution . I am trying real hard here not to mess up the Windows booting ! And, believe me I do not know what we are doing . This is all new territory to me - I learn as we go .
[INDENT][INDENT]all in the process of learning
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-03
Kinshuk_Lahiri; Hey !

It took ! Pleasantly surprised .

So what results when you boot with "Boot0004* ubuntu" ?

[INDENT][INDENT]maybe now Yes 
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-03
Sorry for the delay. As you suggested to reboot after the executing the code. So, i rebooted. And then went to the firmware boot options and it add a ubuntu options. You can see in the screenshot:

[http://prnt.sc/cdq62b](http://prnt.sc/cdq62b)

And then I booted into it and then it booted to Windows. 

> **Bashing-om said:**
> Kinshuk_Lahiri; Hey !

It took ! Pleasantly surprised .

So what results when you boot with "Boot0004* ubuntu" ?
[INDENT][INDENT]maybe now Yes 
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-03
Kinshuk_Lahiri; Well ...

even booting to windows with boot004 is hopeful . I must have passed the wrong ( \EFI\Boot\bootx64.efi ) target .
Back to homework, and determine what the right file is . Not able to access the directory directly is a serious handicap .

[INDENT][INDENT]progress never-the-less
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-03
Great :)

Do let me know whatever info you require from my side, will provide you the same.

Thanks


> **Bashing-om said:**
> Kinshuk_Lahiri; Well ...

even booting to windows with boot004 is hopeful . I must have passed the wrong ( \EFI\Boot\bootx64.efi ) target .
Back to homework, and determine what the right file is . Not able to access the directory directly is a serious handicap .
[INDENT][INDENT]progress never-the-less
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-03
Kinshuk_Lahiri; Welp :

Undo what we have just done:
delete the entry;
make sure that 0004 remains as the entry we want gone:
```

sudo efibootmgr -v

```
where ubuntu is still 0004, right ?
then we run:
```

sudo efibootmgr -b 0004 -B

```

Entry is gone gone .
Now let us try and create the correct boot entry:
```

sudo efibootmgr -c -g -d /dev/sda -p 2 -w -L "ubuntu" -l '\EFI\ubuntu\bootx64.efi'

```
where we change the target path from " /EFI/Boot/" to "/EFI/ubuntu/". Just hope that the file does exist. From my research it is probable that it is valid. But without looking we can not know for sure. But for sure, will not hurt to try and see what happens.

Now reboot and choose the new 'ubuntu' entry as the boot choice . what now results ?


[INDENT][INDENT]poke at it 'til something gives
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-03
Ok removed the entry and then add the new entry. And then rebooted. In the firmware boot options, the older option has been removed and no new option were there. Now running on the Try Ubuntu mode and run the following command and the output is:

```
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0001,3001,2001,2002,2003
Boot0000* USB Hard Drive - hp      v228g    BBS(7,,0x500)..................................................................Z.........A.....................
Boot0001* Windows Boot Manager    HD(2,GPT,a39d70f3-f82f-46c4-8526-549b0e0f821d,0x145800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}.../................
Boot0002* Notebook Hard Drive - HGST HTS541010A9E680    BBS(HD,,0x500)................-...........A......................................5........A.........................
Boot0003* USB Hard Drive (UEFI) - hp      v228g    PciRoot(0x0)/Pci(0x14,0x0)/USB(5,0)/HD(1,MBR,0x15,0x800,0x1df2f00)RC
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC
Boot3001* Internal Hard Disk or Solid State Disk    RC
Boot3002* Internal Hard Disk or Solid State Disk    RC
Boot3003* Internal Hard Disk or Solid State Disk    RC


```
> **Bashing-om said:**
> Kinshuk_Lahiri; Welp :

Undo what we have just done:
delete the entry;
make sure that 0004 remains as the entry we want gone:
```

sudo efibootmgr -v

```
where ubuntu is still 0004, right ?
then we run:
```

sudo efibootmgr -b 0004 -B

```

Entry is gone gone .
Now let us try and create the correct boot entry:
```

sudo efibootmgr -c -g -d /dev/sda -p 2 -w -L "ubuntu" -l '\EFI\ubuntu\bootx64.efi'

```
where we change the target path from " /EFI/Boot/" to "/EFI/ubuntu/". Just hope that the file does exist. From my research it is probable that it is valid. But without looking we can not know for sure. But for sure, will not hurt to try and see what happens.

Now reboot and choose the new 'ubuntu' entry as the boot choice . what now results ?

[INDENT][INDENT]poke at it 'til something gives
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-03
Kinshuk_Lahiri; Yuk !

obviously then the path file is invalid " \EFI\ubuntu\bootx64.efi".
I would have expected however that the installer to have advised of that situation ,, and perhaps offered some direction ?

As we can not - for unknown reasons - mount and access the efi partition directly. I am at a loss of any manner to proceed .
At this point we really need to be able to see the contents to specify a path and the correct file . Or copy the correct file into the correct path

Now I am out of my depth and do not know what to advise.
Anyone else with advise is welcome !

[INDENT][INDENT]there is no quit in my nature
[INDENT][INDENT][INDENT]but now I flounder on my state of ignorance
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-03
What if I format the current ubuntu partition and re-install ubuntu again? 

> **Bashing-om said:**
> Kinshuk_Lahiri; Yuk !

obviously then the path file is invalid " \EFI\ubuntu\bootx64.efi".
I would have expected however that the installer to have advised of that situation ,, and perhaps offered some direction ?

As we can not - for unknown reasons - mount and access the efi partition directly. I am at a loss of any manner to proceed .
At this point we really need to be able to see the contents to specify a path and the correct file . Or copy the correct file into the correct path

Now I am out of my depth and do not know what to advise.
Anyone else with advise is welcome !
[INDENT][INDENT]there is no quit in my nature[INDENT][INDENT][INDENT]but now I flounder on my state of ignorance
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-03
Kinshuk_Lahiril Well ..

A re-install is an option .. but I have my doubts .
There must exist some problem with the efi partition, else we could mount and access it .
The nature of this problem remains un-identified and we can not know if the problem will carry over to a problem with the re-install of the operating system .
Are you prepared for a disaster situation ? in that IF both Windows and ubuntu will require re-installing ? have you backed up all important files ?

I do suggest we address the problem, rather than a nuclear approach . Need to find out why and how to mount the efi partition and see what the contents are . Give efibootmgr something to work with .

But my knowledge of the vfat file system does not permit me to know what to do . In the dark I am not willing to mess about with it and loose the ability to boot Windows too .

In the event that time and frustration is a factor , re-install is always the thing to do . with good backups .. takes but 20 minutes - and a fast internet connection - to re-install .

I do not know of any with the knowledge to get us out of this hole , given the time we see here who responds with some idea of direction .

[INDENT][INDENT]patience is a virtue
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-03
Ok. Will wait for the solution.

Thanks

> **Bashing-om said:**
> Kinshuk_Lahiril Well ..

A re-install is an option .. but I have my doubts .
There must exist some problem with the efi partition, else we could mount and access it .
The nature of this problem remains un-identified and we can not know if the problem will carry over to a problem with the re-install of the operating system .
Are you prepared for a disaster situation ? in that IF both Windows and ubuntu will require re-installing ? have you backed up all important files ?

I do suggest we address the problem, rather than a nuclear approach . Need to find out why and how to mount the efi partition and see what the contents are . Give efibootmgr something to work with .

But my knowledge of the vfat file system does not permit me to know what to do . In the dark I am not willing to mess about with it and loose the ability to boot Windows too .

In the event that time and frustration is a factor , re-install is always the thing to do . with good backups .. takes but 20 minutes - and a fast internet connection - to re-install .

I do not know of any with the knowledge to get us out of this hole , given the time we see here who responds with some idea of direction .
[INDENT][INDENT]patience is a virtue
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-03
Kinshuk_Lahiri; Hey;

Let's give this :
```

sudo mkdir -p /mnt/EFI
sudo mount -t vfat -o rw,users /dev/sda2 /mnt/EFI
ls -al /mnt/
ls -al /mnt/EFI/

```

A try ... to access the efi partition .
Unmount !
```

sudo umount /mnt/EFI

```

[INDENT][INDENT]we have tried before
[INDENT][INDENT][INDENT]try try again
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-04
Ok. Ran the code. And here is the output:

```
ubuntu@ubuntu:~$ sudo mkdir -p /mnt/EFI
ubuntu@ubuntu:~$ sudo mount -t vfat -o rw,users /dev/sda2 /mnt/EFI
ubuntu@ubuntu:~$ ls -al /mnt/
total 4
drwxr-xr-x 1 root root   60 Sep  4 07:08 .
drwxr-xr-x 1 root root  280 Sep  4 06:53 ..
drwxr-xr-x 4 root root 4096 Jan  1  1970 EFI
ubuntu@ubuntu:~$ ls -al /mnt/EFI/
total 16
drwxr-xr-x 4 root root 4096 Jan  1  1970 .
drwxr-xr-x 1 root root   60 Sep  4 07:08 ..
drwxr-xr-x 2 root root 4096 Jun 17  2014 boot
-r-xr-xr-x 1 root root  512 Aug  6  2015 BOOTSECT.BAK
drwxr-xr-x 5 root root 4096 Feb 18  2015 EFI


```

> **Bashing-om said:**
> Kinshuk_Lahiri; Hey;

Let's give this :
```

sudo mkdir -p /mnt/EFI
sudo mount -t vfat -o rw,users /dev/sda2 /mnt/EFI
ls -al /mnt/
ls -al /mnt/EFI/

```

A try ... to access the efi partition .
Unmount !
```

sudo umount /mnt/EFI

```
[INDENT][INDENT]we have tried before[INDENT][INDENT][INDENT]try try again
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-04
Kinshuk_Lahiri; Hey !

Do not ask me the why of it .. but now we can access the efi partition !!
Now we can do something constructive.

OK, we can now see what we have to work with ,

From the liveUSB, the efi partition mounted as above .
Let us look and see what files we have available to install ubunu's files for boot loading:
```

ls -al /mnt/EFI/boot/
ls -al /mnt/EFI/EFI/

```

[INDENT][INDENT]feels good
[INDENT][INDENT][INDENT]to have a way forward
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-04
Ran the command. Here is the output:

```
ubuntu@ubuntu:~$ sudo mkdir -p /mnt/EFI
ubuntu@ubuntu:~$ sudo mount -t vfat -o rw,users /dev/sda2 /mnt/EFI
ubuntu@ubuntu:~$ ls -al /mnt/
total 4
drwxr-xr-x 1 root root   60 Sep  4 19:14 .
drwxr-xr-x 1 root root  280 Sep  5  2016 ..
drwxr-xr-x 4 root root 4096 Jan  1  1970 EFI
ubuntu@ubuntu:~$ ls -al /mnt/EFI/boot/
total 3104
drwxr-xr-x 2 root root    4096 Jun 17  2014 .
drwxr-xr-x 4 root root    4096 Jan  1  1970 ..
-rwxr-xr-x 1 root root 3170304 Jun 18  2013 boot.sdi
ubuntu@ubuntu:~$ ls -al /mnt/EFI/EFI/
total 20
drwxr-xr-x 5 root root 4096 Feb 18  2015 .
drwxr-xr-x 4 root root 4096 Jan  1  1970 ..
drwxr-xr-x 2 root root 4096 Jun 17  2014 Boot
drwxr-xr-x 7 root root 4096 Feb 18  2015 HP
drwxr-xr-x 4 root root 4096 Jun 17  2014 Microsoft


```

Thanks
> **Bashing-om said:**
> Kinshuk_Lahiri; Hey !

Do not ask me the why of it .. but now we can access the efi partition !!
Now we can do something constructive.

OK, we can now see what we have to work with ,

From the liveUSB, the efi partition mounted as above .
Let us look and see what files we have available to install ubunu's files for boot loading:
```

ls -al /mnt/EFI/boot/
ls -al /mnt/EFI/EFI/

```
[INDENT][INDENT]feels good[INDENT][INDENT][INDENT]to have a way forward
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-04
Kinshuk_Lahiri; Welp;

I do not see what I had hoped to see:
We drill further down, see what we have:
```

ls -al /mnt/EFI/EFI/Boot
ls -al /mnt/EFI/EFI/HP
ls -al /mnt/EFI/EFI/Microsoft

```
And I do take note of the change in case for "Boot" .. it do make a difference as linux is case sensitive ! Boot != boot .

Are we going to have to get creative here  ?.. now that might be a trick for me and with my limited experience !

The good thing is that there is more than a glimmer
[INDENT][INDENT][INDENT]of hope
[/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-04
Here's the output:

```
ubuntu@ubuntu:~$ ls -al /mnt/EFI/EFI/Boot
total 1140
drwxr-xr-x 2 root root    4096 Jun 17  2014 .
drwxr-xr-x 5 root root    4096 Feb 18  2015 ..
-rwxr-xr-x 1 root root 1159008 Mar 29 15:48 bootx64.efi
ubuntu@ubuntu:~$ ls -al /mnt/EFI/EFI/HP
total 28
drwxr-xr-x  7 root root 4096 Feb 18  2015 .
drwxr-xr-x  5 root root 4096 Feb 18  2015 ..
drwxr-xr-x  5 root root 4096 Feb 18  2015 BIOS
drwxr-xr-x  2 root root 4096 Feb 18  2015 BIOSUpdate
drwxr-xr-x 40 root root 4096 Jun 17  2014 boot
drwxr-xr-x  4 root root 4096 Jun 17  2014 EFI
drwxr-xr-x  2 root root 4096 Jun 17  2014 SystemDiags
ubuntu@ubuntu:~$ ls -al /mnt/EFI/EFI/Microsoft
total 20
drwxr-xr-x  4 root root 4096 Jun 17  2014 .
drwxr-xr-x  5 root root 4096 Feb 18  2015 ..
drwxr-xr-x 42 root root 8192 Jun 17  2014 Boot
drwxr-xr-x  2 root root 4096 Aug  6  2015 Recovery


```

> **Bashing-om said:**
> Kinshuk_Lahiri; Welp;

I do not see what I had hoped to see:
We drill further down, see what we have:
```

ls -al /mnt/EFI/EFI/Boot
ls -al /mnt/EFI/EFI/HP
ls -al /mnt/EFI/EFI/Microsoft

```
And I do take note of the change in case for "Boot" .. it do make a difference as linux is case sensitive ! Boot != boot .

Are we going to have to get creative here  ?.. now that might be a trick for me and with my limited experience !

The good thing is that there is more than a glimmer[INDENT][INDENT][INDENT]of hope
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-04
Kinshuk_Lahiri; K

I do not see anything for booting ubuntu .. 
Let me consider to try again - seeing as how we can now mount the target partitions - installing grub fresh .
But would sure be nice to have a 2nd opinion here on the proper way to add that boot option to the boot menu .( but can not add what does not exist ) .

[INDENT][INDENT]study twice
[INDENT][INDENT][INDENT]act once
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-09-05
Kinshuk_Lahiri; Morning !

My considered opinion after sleeping on it and now with a fresh mind - is to try and re-install grub:
Boot the liveUSB
and
mount our 2 target partitions:
```

sudo mkdir -p /mnt
sudo mkdir -p /mnt/EFI
sudo mount /dev/sda6 /mnt
mount -t vfat -o rw,users /dev/sda2 /mnt/EFI

```

Now we verify and make sure we have access to the target partitions:
```

ls -al /mnt/EFI
ls -al /mnt/boot/grub/grub.cfg
efibootmgr -v ##<-This so we have a reference, note down the boot options as we will see if a new option is added

```

OK, we have access .. and the results of the ls commands are positive in that files do exist :
```

for i in /dev /dev/pts /sys /proc /run; do sudo mount -B $i /mnt$i; done
modprobe efivars 
sudo chroot /mnt

```
You are now in the install with root access .. be very very careful here .. there is NO forgiveness for any mistakes !

At this point prior to proceeding with the grub install .. make sure we have networking so we can get the files. I have yet to do this procedure in 16.04 (systemd) - you are the ginny pig - ; But, I see no reason why it will not work .
```

ping -c3 ubuntu.com

```
If in the return is :
> 
3 packets transmitted, 3 received, 0% packet loss, time 2002ms

we then proceed with the install of grub.
```

apt install --reinstall grub-efi-amd64-signed
efibootmgr -c --disk /dev/sda --part 2
efibootmgr -v # <-verify a new record/boot option maybe called Linux is there

```

OK, all done here, back out of the install and reboot to see the effect.
```

exit
for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
sudo umount /mnt/EFI #please do this. corrupted efi partitions are not nice
sudo umount /mnt
sudo reboot

```

Reset in the firmware to boot the new boot option, and now what do you boot to ?

[INDENT][INDENT][INDENT]are we there yet ?
[/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-05
Here is the output and just ran the first section:

```

ubuntu@ubuntu:~$ sudo mkdir -p /mnt
ubuntu@ubuntu:~$ sudo mkdir -p /mnt/EFI
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ mount -t vfat -o rw,users /dev/sda2 /mnt/EFI
mount: only root can use "--options" option
ubuntu@ubuntu:~$ sudo mount -t vfat -o rw,users /dev/sda2 /mnt/EFI
mount: mount point /mnt/EFI does not exist

```

> **Bashing-om said:**
> Kinshuk_Lahiri; Morning !

My considered opinion after sleeping on it and now with a fresh mind - is to try and re-install grub:
Boot the liveUSB
and
mount our 2 target partitions:
```

sudo mkdir -p /mnt
sudo mkdir -p /mnt/EFI
sudo mount /dev/sda6 /mnt
mount -t vfat -o rw,users /dev/sda2 /mnt/EFI

```

Now we verify and make sure we have access to the target partitions:
```

ls -al /mnt/EFI
ls -al /mnt/boot/grub/grub.cfg
efibootmgr -v ##<-This so we have a reference, note down the boot options as we will see if a new option is added

```

OK, we have access .. and the results of the ls commands are positive in that files do exist :
```

for i in /dev /dev/pts /sys /proc /run; do sudo mount -B $i /mnt$i; done
modprobe efivars 
sudo chroot /mnt

```
You are now in the install with root access .. be very very careful here .. there is NO forgiveness for any mistakes !

At this point prior to proceeding with the grub install .. make sure we have networking so we can get the files. I have yet to do this procedure in 16.04 (systemd) - you are the ginny pig - ; But, I see no reason why it will not work .
```

ping -c3 ubuntu.com

```
If in the return is :

we then proceed with the install of grub.
```

apt install --reinstall grub-efi-amd64-signed
efibootmgr -c --disk /dev/sda --part 2
efibootmgr -v # <-verify a new record/boot option maybe called Linux is there

```

OK, all done here, back out of the install and reboot to see the effect.
```

exit
for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
sudo umount /mnt/EFI #please do this. corrupted efi partitions are not nice
sudo umount /mnt
sudo reboot

```

Reset in the firmware to boot the new boot option, and now what do you boot to ?
[INDENT][INDENT][INDENT]are we there yet ?
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-05
Kinshuk_Lahiri; Yikes !

I do not have a clue !
> ubuntu@ubuntu:~$ sudo mount -t vfat -o rw,users /dev/sda2 /mnt/EFI
mount: mount point /mnt/EFI does not exist

When we just did mount that partition with the same same syntax .

We can do nothing until we can access these partitions .

[INDENT][INDENT]I just do not know
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-05
Before mounting the sda6, last time when we mounted it first then it was mounted and now when we mound the sda6 first it shows no partition. That's strange.

> **Bashing-om said:**
> Kinshuk_Lahiri; Yikes !

I do not have a clue !


When we just did mount that partition with the same same syntax .

We can do nothing until we can access these partitions .
[INDENT][INDENT]I just do not know
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-06
Kinshuk_Lahiril Hey ...

I am out of expertness; If Windows is fully shut down and you still can not mount the partitions in ubuntu's liveUSB; It is above my skill level now to know . I no longer know the Windows Operating System well enough to even offer an opinion from that perspective.

[INDENT][INDENT]'times I just do not know
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-06
What if i mount the sda 6 after mounting the efi paritition? 

> **Bashing-om said:**
> Kinshuk_Lahiril Hey ...

I am out of expertness; If Windows is fully shut down and you still can not mount the partitions in ubuntu's liveUSB; It is above my skill level now to know . I no longer know the Windows Operating System well enough to even offer an opinion from that perspective.
[INDENT][INDENT]'times I just do not know
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-06
Kinshuk_Lahiri; Welp;

I do not see that the order here of mounting matters . But one can certainly try and see what results. I am wiling to be pleasantly surprised .

[INDENT][INDENT]try try try again
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-06
Take a look sir. It may help:

```
ubuntu@ubuntu:~$ sudo mkdir -p /mnt/EFI
ubuntu@ubuntu:~$ sudo mount -t vfat -o rw,users /dev/sda2 /mnt/EFI
ubuntu@ubuntu:~$ ls -al /mnt
total 4
drwxr-xr-x 1 root root   60 Sep  6 17:18 .
drwxr-xr-x 1 root root  280 Sep  6  2016 ..
drwxr-xr-x 4 root root 4096 Jan  1  1970 EFI
ubuntu@ubuntu:~$ ls -al /mnt/EFI
total 16
drwxr-xr-x 4 root root 4096 Jan  1  1970 .
drwxr-xr-x 1 root root   60 Sep  6 17:18 ..
drwxr-xr-x 2 root root 4096 Jun 17  2014 boot
-r-xr-xr-x 1 root root  512 Aug  6  2015 BOOTSECT.BAK
drwxr-xr-x 5 root root 4096 Feb 18  2015 EFI
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ ls -al /mnt/EFI
ls: cannot access '/mnt/EFI': No such file or directory


```

> **Bashing-om said:**
> Kinshuk_Lahiri; Welp;

I do not see that the order here of mounting matters . But one can certainly try and see what results. I am wiling to be pleasantly surprised .
[INDENT][INDENT]try try try again
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-06
Kinshuk_Lahiri; Hummm ...

Let's try with explicit mounts once more.
```

sudo umount /dev/sda2
sudo umount /dev/sda6
sudo mkdir -p /mnt/EFI #here -p " make parent directories as needed " As this is a shared partition
sudo mkdir /mnt/root #here we do not need any flags, defaults will be fine, as this partition is dedicated now to the install's root .
sudo mount -t vfat -o rw,users /dev/sda2 /mnt/EFI
sudo mount /dev/sda6 /mnt/root

```

And now do we have access ?
```

ls -al /mnt/
ls -al /mnt/EFI
ls -al /mnt/root

```

Remember ! We must UN-Mount what ever we manually mount :
```

sudo umount //dev/sda2
sudo umount /dev/sda6

```
when done with what ever we are doing . Else file system corruption at some level will result !

If  we have access we can continue and re-install grub and create the ubuntu's boot entry .

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-06
:) . Glad to post the output and very much excited:

```
ubuntu@ubuntu:~$ sudo umount /dev/sda2
umount: /dev/sda2: not mounted
ubuntu@ubuntu:~$ sudo umount /dev/sda6
umount: /dev/sda6: not mounted
ubuntu@ubuntu:~$ sudo mkdir -p /mnt/EFI
ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t vfat -o rw,users /dev/sda2 /mnt/EFI
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/root
ubuntu@ubuntu:~$ ls -al /mnt/
total 8
drwxr-xr-x  1 root root   80 Sep  6 17:55 .
drwxr-xr-x  1 root root  280 Sep  6  2016 ..
drwxr-xr-x  4 root root 4096 Jan  1  1970 EFI
drwxr-xr-x 25 root root 4096 Aug 27 12:52 root
ubuntu@ubuntu:~$ ls -al /mnt/EFI
total 16
drwxr-xr-x 4 root root 4096 Jan  1  1970 .
drwxr-xr-x 1 root root   80 Sep  6 17:55 ..
drwxr-xr-x 2 root root 4096 Jun 17  2014 boot
-r-xr-xr-x 1 root root  512 Aug  6  2015 BOOTSECT.BAK
drwxr-xr-x 5 root root 4096 Feb 18  2015 EFI
ubuntu@ubuntu:~$ ls -al /mnt/root
total 15832
drwxr-xr-x  25 root root     4096 Aug 27 12:52 .
drwxr-xr-x   1 root root       80 Sep  6 17:55 ..
drwxr-xr-x   2 root root     4096 Aug 27 12:35 bin
drwxr-xr-x   3 root root     4096 Aug 27 12:59 boot
drwxrwxr-x   2 root root     4096 Nov 17  2015 cdrom
-rw-------   1 root root 16084992 Nov 19  2015 core
drwxr-xr-x   5 root root     4096 Apr 22  2015 dev
drwxr-xr-x 137 root root    12288 Sep  1 17:34 etc
drwxr-xr-x   3 root root     4096 Nov 17  2015 home
lrwxrwxrwx   1 root root       32 Aug 27 12:52 initrd.img -> boot/initrd.img-4.4.0-34-generic
lrwxrwxrwx   1 root root       32 Aug 27 07:26 initrd.img.old -> boot/initrd.img-4.2.0-42-generic
drwxr-xr-x  25 root root     4096 Aug 27 12:57 lib
drwxr-xr-x   2 root root     4096 Aug 27 12:13 lib32
drwxr-xr-x   2 root root     4096 Aug 27 12:12 lib64
drwx------   2 root root    16384 Nov 17  2015 lost+found
drwxr-xr-x   4 root root     4096 Apr 22 09:40 media
drwxr-xr-x   2 root root     4096 Aug 27 12:12 mnt
drwxr-xr-x   4 root root     4096 Nov 26  2015 opt
drwxr-xr-x   2 root root     4096 Apr 17  2015 proc
drwx------  10 root root     4096 Nov 26  2015 root
drwxr-xr-x  10 root root     4096 Apr 22  2015 run
drwxr-xr-x   2 root root    12288 Aug 27 12:42 sbin
drwxr-xr-x   2 root root     4096 Aug 12 15:59 snap
drwxr-xr-x   2 root root     4096 Apr 22  2015 srv
drwxr-xr-x   2 root root     4096 Apr  6  2015 sys
drwxrwxrwt  11 root root     4096 Aug 27 12:59 tmp
drwxr-xr-x  12 root root     4096 Nov 21  2015 usr
drwxr-xr-x  14 root root     4096 Aug 27 12:41 var
lrwxrwxrwx   1 root root       29 Aug 27 12:52 vmlinuz -> boot/vmlinuz-4.4.0-34-generic
lrwxrwxrwx   1 root root       29 Aug 27 07:26 vmlinuz.old -> boot/vmlinuz-4.2.0-42-generic
ubuntu@ubuntu:~$ sudo umount //dev/sda2
ubuntu@ubuntu:~$ sudo umount /dev/sda6


```

Thanks
> **Bashing-om said:**
> Kinshuk_Lahiri; Hummm ...

Let's try with explicit mounts once more.
```

sudo umount /dev/sda2
sudo umount /dev/sda6
sudo mkdir -p /mnt/EFI #here -p " make parent directories as needed " As this is a shared partition
sudo mkdir /mnt/root #here we do not need any flags, defaults will be fine, as this partition is dedicated now to the install's root .
sudo mount -t vfat -o rw,users /dev/sda2 /mnt/EFI
sudo mount /dev/sda6 /mnt/root

```

And now do we have access ?
```

ls -al /mnt/
ls -al /mnt/EFI
ls -al /mnt/root

```

Remember ! We must UN-Mount what ever we manually mount :
```

sudo umount //dev/sda2
sudo umount /dev/sda6

```
when done with what ever we are doing . Else file system corruption at some level will result !

If  we have access we can continue and re-install grub and create the ubuntu's boot entry .
[INDENT][INDENT]sometimes I do wonder
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-06
Kinshuk_Lahiri; That ! Looks absolutely fine !

Let's see now what results - starting with what we now have mounted .
continue !
```

efibootmgr -v ##<-This so we have a reference, note down the boot options as we will see if a new option is added
for i in /dev /dev/pts /sys /proc /run; do sudo mount -B $i /mnt/root$i; done
modprobe efivars 
sudo chroot /mnt/root
ping -c3 ubuntu.com #make sure we get a positive result as we must have networking !
apt install --reinstall grub-efi-amd64-signed
efibootmgr -c --disk /dev/sda --part 2
efibootmgr -v # <-verify a new record/boot option maybe called Linux is there

```

Now if all looks correct and proper .. back out of the CHange Root and reboot.
```

exit
for i in /sys /proc /dev/pts /dev; do sudo umount /mnt/root$i; done
sudo umount /mnt/EFI #please do this. corrupted efi partitions are not nice
sudo umount /mnt/root
sudo reboot

```

Reset in the firmware to boot the new entry .

What now results ?

[INDENT][INDENT]maybe YES
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-06
While running the for loop it got this output:

```

ubuntu@ubuntu:~$ sudo umount /dev/sda2
umount: /dev/sda2: not mounted
ubuntu@ubuntu:~$ sudo umount /dev/sda6
ubuntu@ubuntu:~$ sudo mkdir -p /mnt/EFI
ubuntu@ubuntu:~$ sudo mkdir /mnt/root
mkdir: cannot create directory ‘/mnt/root’: File exists
ubuntu@ubuntu:~$ sudo mount -t vfat -o rw,users /dev/sda2 /mnt/EFI
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/root
ubuntu@ubuntu:~$ ls -al /mnt/
total 8
drwxr-xr-x  1 root root   80 Sep  6 17:55 .
drwxr-xr-x  1 root root  280 Sep  6  2016 ..
drwxr-xr-x  4 root root 4096 Jan  1  1970 EFI
drwxr-xr-x 25 root root 4096 Aug 27 12:52 root
ubuntu@ubuntu:~$ ls -al /mnt/EFI
total 16
drwxr-xr-x 4 root root 4096 Jan  1  1970 .
drwxr-xr-x 1 root root   80 Sep  6 17:55 ..
drwxr-xr-x 2 root root 4096 Jun 17  2014 boot
-r-xr-xr-x 1 root root  512 Aug  6  2015 BOOTSECT.BAK
drwxr-xr-x 5 root root 4096 Feb 18  2015 EFI
ubuntu@ubuntu:~$ ls -al /mnt/root
total 15832
drwxr-xr-x  25 root root     4096 Aug 27 12:52 .
drwxr-xr-x   1 root root       80 Sep  6 17:55 ..
drwxr-xr-x   2 root root     4096 Aug 27 12:35 bin
drwxr-xr-x   3 root root     4096 Aug 27 12:59 boot
drwxrwxr-x   2 root root     4096 Nov 17  2015 cdrom
-rw-------   1 root root 16084992 Nov 19  2015 core
drwxr-xr-x   5 root root     4096 Apr 22  2015 dev
drwxr-xr-x 137 root root    12288 Sep  1 17:34 etc
drwxr-xr-x   3 root root     4096 Nov 17  2015 home
lrwxrwxrwx   1 root root       32 Aug 27 12:52 initrd.img -> boot/initrd.img-4.4.0-34-generic
lrwxrwxrwx   1 root root       32 Aug 27 07:26 initrd.img.old -> boot/initrd.img-4.2.0-42-generic
drwxr-xr-x  25 root root     4096 Aug 27 12:57 lib
drwxr-xr-x   2 root root     4096 Aug 27 12:13 lib32
drwxr-xr-x   2 root root     4096 Aug 27 12:12 lib64
drwx------   2 root root    16384 Nov 17  2015 lost+found
drwxr-xr-x   4 root root     4096 Apr 22 09:40 media
drwxr-xr-x   2 root root     4096 Aug 27 12:12 mnt
drwxr-xr-x   4 root root     4096 Nov 26  2015 opt
drwxr-xr-x   2 root root     4096 Apr 17  2015 proc
drwx------  10 root root     4096 Nov 26  2015 root
drwxr-xr-x  10 root root     4096 Apr 22  2015 run
drwxr-xr-x   2 root root    12288 Aug 27 12:42 sbin
drwxr-xr-x   2 root root     4096 Aug 12 15:59 snap
drwxr-xr-x   2 root root     4096 Apr 22  2015 srv
drwxr-xr-x   2 root root     4096 Apr  6  2015 sys
drwxrwxrwt  11 root root     4096 Aug 27 12:59 tmp
drwxr-xr-x  12 root root     4096 Nov 21  2015 usr
drwxr-xr-x  14 root root     4096 Aug 27 12:41 var
lrwxrwxrwx   1 root root       29 Aug 27 12:52 vmlinuz -> boot/vmlinuz-4.4.0-34-generic
lrwxrwxrwx   1 root root       29 Aug 27 07:26 vmlinuz.old -> boot/vmlinuz-4.2.0-42-generic
ubuntu@ubuntu:~$ efibootmgr -v
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0001,3001,2001,2002,2003
Boot0000* USB Hard Drive - hp      v228g    BBS(7,,0x500)..................................................................\.........A.....................
Boot0001* Windows Boot Manager    HD(2,GPT,a39d70f3-f82f-46c4-8526-549b0e0f821d,0x145800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}.../................
Boot0002* Notebook Hard Drive - HGST HTS541010A9E680    BBS(HD,,0x500)................-...........A......................................5........A.........................
Boot0003* USB Hard Drive (UEFI) - hp      v228g    PciRoot(0x0)/Pci(0x14,0x0)/USB(5,0)/HD(1,MBR,0x15,0x800,0x1df2f00)RC
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC
Boot3001* Internal Hard Disk or Solid State Disk    RC
Boot3002* Internal Hard Disk or Solid State Disk    RC
Boot3003* Internal Hard Disk or Solid State Disk    RC
ubuntu@ubuntu:~$ for i in /dev /dev/pts /sys /proc /run; do sudo mount -B $i /mnt$i; done
mount: mount point /mnt/dev does not exist
mount: mount point /mnt/dev/pts does not exist
mount: mount point /mnt/sys does not exist
mount: mount point /mnt/proc does not exist
mount: mount point /mnt/run does not exist



```

Is it ok? Should i run the next command? Waiting for your reply.
Thanks

> **Bashing-om said:**
> Kinshuk_Lahiri; That ! Looks absolutely fine !

Let's see now what results - starting with what we now have mounted .
continue !
```

efibootmgr -v ##<-This so we have a reference, note down the boot options as we will see if a new option is added
for i in /dev /dev/pts /sys /proc /run; do sudo mount -B $i /mnt$i; done
modprobe efivars 
sudo chroot /mnt/root
ping -c3 ubuntu.com #make sure we get a positive result as we must have networking !
apt install --reinstall grub-efi-amd64-signed
efibootmgr -c --disk /dev/sda --part 2
efibootmgr -v # <-verify a new record/boot option maybe called Linux is there

```

Now if all looks correct and proper .. back out of the CHange Root and reboot.
```

exit
for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
sudo umount /mnt/EFI #please do this. corrupted efi partitions are not nice
sudo umount /mnt/root
sudo reboot

```

Reset in the firmware to boot the new entry .

What now results ?
[INDENT][INDENT]maybe YES
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-06
Kinshuk_Lahiri; Yuk !

And ouch ! I think I missed a mount point:
> 
ubuntu@ubuntu:~$ for i in /dev /dev/pts /sys /proc /run; do sudo mount -B $i /mnt$i; done

let try this rendition:
```

ubuntu@ubuntu:~$ for i in /dev /dev/pts /sys /proc /run; do sudo mount -B $i /mnt/root$i; done

```

Does that run ?

[INDENT][INDENT]me and my little bitty mind[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-06
Yes that worked. And stuck at here. Waiting for the new command for this as well:

```

ubuntu@ubuntu:~$ for i in /dev /dev/pts /sys /proc /run; do sudo mount -B $i /mnt/root$i; done
ubuntu@ubuntu:~$ modprobe efivars 
ubuntu@ubuntu:~$ sudo chroot /mnt/root
root@ubuntu:/# ping -c3 ubuntu.com
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=50 time=160 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=50 time=181 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=50 time=353 ms

--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 160.603/231.780/353.376/86.399 ms
root@ubuntu:/# apt install --reinstall grub-efi-amd64-signed
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  grub-efi-amd64 grub-efi-amd64-bin
The following packages will be REMOVED:
  grub-gfxpayload-lists grub-pc
The following NEW packages will be installed:
  grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed
0 upgraded, 3 newly installed, 2 to remove and 0 not upgraded.
Need to get 1,007 kB of archives.
After this operation, 5,805 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://in.archive.ubuntu.com/ubuntu xenial-updates/main amd64 grub-efi-amd64-bin amd64 2.02~beta2-36ubuntu3.2 [653 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu xenial-updates/main amd64 grub-efi-amd64 amd64 2.02~beta2-36ubuntu3.2 [65.7 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu xenial-updates/main amd64 grub-efi-amd64-signed amd64 1.66.2+2.02~beta2-36ubuntu3.2 [289 kB]
Fetched 1,007 kB in 9s (104 kB/s)                                              
Preconfiguring packages ...
(Reading database ... 195595 files and directories currently installed.)
Removing grub-gfxpayload-lists (0.7) ...
Removing grub-pc (2.02~beta2-36ubuntu3.2) ...
Processing triggers for man-db (2.7.5-1) ...
Selecting previously unselected package grub-efi-amd64-bin.
(Reading database ... 195577 files and directories currently installed.)
Preparing to unpack .../grub-efi-amd64-bin_2.02~beta2-36ubuntu3.2_amd64.deb ...
Unpacking grub-efi-amd64-bin (2.02~beta2-36ubuntu3.2) ...
Selecting previously unselected package grub-efi-amd64.
Preparing to unpack .../grub-efi-amd64_2.02~beta2-36ubuntu3.2_amd64.deb ...
Unpacking grub-efi-amd64 (2.02~beta2-36ubuntu3.2) ...
Selecting previously unselected package grub-efi-amd64-signed.
Preparing to unpack .../grub-efi-amd64-signed_1.66.2+2.02~beta2-36ubuntu3.2_amd64.deb ...
Unpacking grub-efi-amd64-signed (1.66.2+2.02~beta2-36ubuntu3.2) ...
Setting up grub-efi-amd64-bin (2.02~beta2-36ubuntu3.2) ...
Setting up grub-efi-amd64 (2.02~beta2-36ubuntu3.2) ...
Replacing config file /etc/default/grub with new version
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
Found linux image: /boot/vmlinuz-4.2.0-42-generic
Found initrd image: /boot/initrd.img-4.2.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-33-generic
Found initrd image: /boot/initrd.img-3.19.0-33-generic
Found Windows Boot Manager on /dev/sda2@/efi/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Setting up grub-efi-amd64-signed (1.66.2+2.02~beta2-36ubuntu3.2) ...
root@ubuntu:/# efibootmgr -c --disk /dev/sda --part 2
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0004,0001,3001,2001,2002,2003
Boot0000* USB Hard Drive - hp      v228g
Boot0001* Windows Boot Manager
Boot0002* Notebook Hard Drive - HGST HTS541010A9E680
Boot0003* USB Hard Drive (UEFI) - hp      v228g
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk
Boot0004* Linux
root@ubuntu:/# efibootmgr -v
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0004,0001,3001,2001,2002,2003
Boot0000* USB Hard Drive - hp      v228g    BBS(7,,0x500)..................................................................\.........A.....................
Boot0001* Windows Boot Manager    HD(2,GPT,a39d70f3-f82f-46c4-8526-549b0e0f821d,0x145800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}.../................
Boot0002* Notebook Hard Drive - HGST HTS541010A9E680    BBS(HD,,0x500)................-...........A......................................5........A.........................
Boot0003* USB Hard Drive (UEFI) - hp      v228g    PciRoot(0x0)/Pci(0x14,0x0)/USB(5,0)/HD(1,MBR,0x15,0x800,0x1df2f00)RC
Boot0004* Linux    HD(2,GPT,a39d70f3-f82f-46c4-8526-549b0e0f821d,0x145800,0x82000)/File(\EFI\redhat\grub.efi)
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC
Boot3001* Internal Hard Disk or Solid State Disk    RC
Boot3002* Internal Hard Disk or Solid State Disk    RC
Boot3003* Internal Hard Disk or Solid State Disk    RC
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
umount: /mnt/sys: mountpoint not found
umount: /mnt/proc: mountpoint not found
umount: /mnt/dev/pts: mountpoint not found
umount: /mnt/dev: mountpoint not found



```

> **Bashing-om said:**
> Kinshuk_Lahiri; Yuk !

And ouch ! I think I missed a mount point:

let try this rendition:
```

ubuntu@ubuntu:~$ for i in /dev /dev/pts /sys /proc /run; do sudo mount -B $i /mnt/root$i; done

```

Does that run ?
[INDENT][INDENT]me and my little bitty mind[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-06
Kinshuk_Lahiri; Huh ? I did it again .. missed a mount point.
No problem that I see ; the boot entry was added !
> 
Boot0004* Linux


So try as :
```

ubuntu@ubuntu:~$ for i in /sys /proc /dev/pts /dev /run; do sudo umount /mnt/root$i; done
sudo umount /mnt/EFI #please do this. corrupted efi partitions are not nice
sudo umount /mnt/root
sudo reboot

```
to back out of the CHange Root .. back into the liveUSB as the working environment And a reboot .

In the firmware choose Boot0004* Linux to boot .

[INDENT][INDENT]tell me please oH please that you now boot ?

[INDENT][INDENT]hey it could happen
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-06
For unmount root it says busy. here is the output:

```
ubuntu@ubuntu:~$ for i in /sys /proc /dev/pts /dev; do sudo umount /mnt/root$i; done
ubuntu@ubuntu:~$ sudo umount /mnt/EFI
ubuntu@ubuntu:~$ sudo umount /mnt/root
umount: /mnt/root: target is busy
        (In some cases useful info about processes that
         use the device is found by lsof(8) or fuser(1).)
```

> **Bashing-om said:**
> Kinshuk_Lahiri; Huh ? I did it again .. missed a mount point.
No problem that I see ; the boot entry was added !


So try as :
```

ubuntu@ubuntu:~$ for i in /sys /proc /dev/pts /dev; do sudo umount /mnt/root$i; done
sudo umount /mnt/EFI #please do this. corrupted efi partitions are not nice
sudo umount /mnt/root
sudo reboot

```
to back out of the CHange Root .. back into the liveUSB as the working environment And a reboot .

In the firmware choose Boot0004* Linux to boot .
[INDENT][INDENT]tell me please oH please that you now boot ?
[INDENT][INDENT]hey it could happen
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-06
Kinshuk_Lahiri;  Shucks ...

left out a parameter :

run as :
```

for i in /dev /dev/pts /sys /proc /run; do sudo umount -B $i /mnt/root$i; done

```
where /run was formerly omitted .

[INDENT][INDENT]me and my little mind
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-06
It gives:

```

for i in /dev /dev/pts /sys /proc /run; do sudo umount -B $i /mnt/root$i; done
umount: invalid option -- 'B'



```

> **Bashing-om said:**
> Kinshuk_Lahiri;  Shucks ...

left out a parameter :

run as :
```

for i in /dev /dev/pts /sys /proc /run; do sudo umount -B $i /mnt/root$i; done

```
where /run was formerly omitted .
[INDENT][INDENT]me and my little mind
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-06
Kinshuk_Lahiri; Boy !

I must be so scatter brained !

See if this gets it right !
```

for i in /sys /proc /dev/pts /dev /run; do sudo umount /mnt/root$i; done

```


Once more with feeling

---

### Post by Kinshuk_Lahiri on 2016-09-06
Ok. unmonted the root and then rebooted. In firmware boot options, there is no option for linux.

> **Bashing-om said:**
> Kinshuk_Lahiri; Boy !

I must be so scatter brained !

See if this gets it right !
```

for i in /sys /proc /dev/pts /dev /run; do sudo umount /mnt/root$i; done

```


Once more with feeling

---

### Post by Bashing-om on 2016-09-06
Kinshuk_Lahiri;

Sheeshh .. Each and every EFI system is different - there is no standardization ; I can not tell you how to look for the entry.
It is there .. as we have:
> 
root@ubuntu:/# efibootmgr -c --disk /dev/sda --part 2 >>>
Boot0004* Linux    HD(2,GPT,a39d70f3-f82f-46c4-8526-549b0e0f821d,0x145800,0x82000)/File(\EFI\redhat\grub.efi)


But that install path " \EFI\redhat\grub.efi)" throws me for a loop !  How in the world does the 'redhat' OS enter into this ?

[INDENT][INDENT]once again
[INDENT][INDENT][INDENT]I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Dennis N on 2016-09-07
Very strange - redhat - noticed it yesterday, but didn't comment at the time not knowing any background. Ubuntu's grub install produces entries named 'ubuntu', and target boot file (on my machines) is shimx64.efi. 

```
[dmn@Zotac ~]$ sudo efibootmgr -v
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0000,0003,0004,0002
Boot0000* ubuntu	HD(1,GPT,adf95091-cfe2-4af6-a0e0-9df450300d37,0x800,0x28000)/File(\EFI\ubuntu\shimx64.efi)


```Structure of my EFI system partition:

```
[dmn@Zotac efi]$ tree
.
&#9492;&#9472;&#9472; EFI
    &#9500;&#9472;&#9472; boot
    &#9474;** &#9492;&#9472;&#9472; bootx64.efi
    &#9500;&#9472;&#9472; Manjaro
    &#9474;** &#9492;&#9472;&#9472; grubx64.efi
    &#9492;&#9472;&#9472; ubuntu
        &#9500;&#9472;&#9472; fw
        &#9500;&#9472;&#9472; fwupx64.efi
        &#9500;&#9472;&#9472; grub.cfg
        &#9500;&#9472;&#9472; grubx64.efi
        &#9500;&#9472;&#9472; MokManager.efi
        &#9492;&#9472;&#9472; shimx64.efi

```

---

### Post by Bashing-om on 2016-09-07
Dennis N; Hey !

I am sure glad you popped in here .. and with an EFI system ! .. I am sure struggling here. Presently stuck on how to proceed . 
My knowledge of EFI is quite limited and not having access to a EFI system is a serious handicap .

we can use
[INDENT][INDENT][INDENT]all the help we can get
[/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-07
Please help us.

> **Bashing-om said:**
> Dennis N; Hey !

I am sure glad you popped in here .. and with an EFI system ! .. I am sure struggling here. Presently stuck on how to proceed . 
My knowledge of EFI is quite limited and not having access to a EFI system is a serious handicap .

we can use[INDENT][INDENT][INDENT]all the help we can get
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Dennis N on 2016-09-07
This has no definitive solution, but a few observations on the problem and I found a couple of askubuntu questions that may help - one with fixes suggested by Rod Smith himself ([http://www.rodsbooks.com/](http://www.rodsbooks.com/)) - expert on UEFI, he wrote gdisk and rEFInd. You could find more by Googling something like "HP does not boot linux".

_Analysis:_
Your working UEFI installation from 15.10 would need to have had an **ubuntu** folder inside the EFI system partition at first level of the file system on the EFI system partition (see the diagram in post #106). Installing/reistalling grub would replace an existing ubuntu folder with 1604's ubuntu folder, but your /mnt/EFI listing in post #94 doesn't seem to show us any ubuntu folders, so I don't think the reinstall of grub completely worked for some reason.

Your need to start ubuntu 15.10 from the UEFI boot manager (as you said in post #8) suggests that (since you have an HP computer), you are probably affected by HP's bad design for its UEFI.

Rod Smith says*: "Basically, the firmware is hard-coded to boot from Microsoft's boot loader and to make it difficult or impossible to boot from anything else."
*the above quoted from: [http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)

Rod has some fixes in the 2nd of 12 answers within this same link, but all assume Ubuntu is correctly installed. I don't think your is? 

Same problem discussed here:

[http://askubuntu.com/questions/554690/hp-uefi-doesnt-boot-ubuntu-automatically](http://askubuntu.com/questions/554690/hp-uefi-doesnt-boot-ubuntu-automatically)[U]

Redhat[/U]:
The Redhat entry you have suggests that Redhat Linux had been installed on the machine and later wiped, but the efi boot manager entry remained and has now arisen from the dead. Did you use Redhat, or was there a previous owner who did?

_Probably what I would do:_
I would consider a fresh install, then do one of the fixes suggested.

Also please see Rod's suggestions for "Fixing Post-installation Problems" at [http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

---

### Post by Kinshuk_Lahiri on 2016-09-08
I never installed Red Hat on the computer. Don't know from where it came.

I have to re-install ubuntu again. Ok, will do that. 

During the installation, it asks to select a option and I am confused between these two. Whether to erase the Ubuntu 16.04 and re-install it again or select Something Else and then go to the next screen and install by selecting the drive. If have to go with the Something else, then please guide what to do there?

Thanks 

> **Dennis N said:**
> This has no definitive solution, but a few observations on the problem and I found a couple of askubuntu questions that may help - one with fixes suggested by Rod Smith himself ([http://www.rodsbooks.com/](http://www.rodsbooks.com/)) - expert on UEFI, he wrote gdisk and rEFInd. You could find more by Googling something like "HP does not boot linux".

_Analysis:_
Your working UEFI installation from 15.10 would need to have had an **ubuntu** folder inside the EFI system partition at first level of the file system on the EFI system partition (see the diagram in post #106). Installing/reistalling grub would replace an existing ubuntu folder with 1604's ubuntu folder, but your /mnt/EFI listing in post #94 doesn't seem to show us any ubuntu folders, so I don't think the reinstall of grub completely worked for some reason.

Your need to start ubuntu 15.10 from the UEFI boot manager (as you said in post #8) suggests that (since you have an HP computer), you are probably affected by HP's bad design for its UEFI.

Rod Smith says*: "Basically, the firmware is hard-coded to boot from Microsoft's boot loader and to make it difficult or impossible to boot from anything else."
*the above quoted from: [http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)

Rod has some fixes in the 2nd of 12 answers within this same link, but all assume Ubuntu is correctly installed. I don't think your is? 

Same problem discussed here:

[http://askubuntu.com/questions/554690/hp-uefi-doesnt-boot-ubuntu-automatically](http://askubuntu.com/questions/554690/hp-uefi-doesnt-boot-ubuntu-automatically)[U]

Redhat[/U]:
The Redhat entry you have suggests that Redhat Linux had been installed on the machine and later wiped, but the efi boot manager entry remained and has now arisen from the dead. Did you use Redhat, or was there a previous owner who did?

_Probably what I would do:_
I would consider a fresh install, then do one of the fixes suggested.

Also please see Rod's suggestions for "Fixing Post-installation Problems" at [http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

---

### Post by Dennis N on 2016-09-08
What puzzles me is the contents of the EFI partition as taken from post 96:

```
ubuntu@ubuntu:~$ ls -al /mnt/EFI
total 16
drwxr-xr-x 4 root root 4096 Jan  1  1970 .
drwxr-xr-x 1 root root   80 Sep  6 17:55 ..
drwxr-xr-x 2 root root 4096 Jun 17  2014 boot
-r-xr-xr-x 1 root root  512 Aug  6  2015 BOOTSECT.BAK
drwxr-xr-x 5 root root 4096 Feb 18  2015 EFI


```compared to what the efibootmgr outputs in post 98: 

```
Boot0001* Windows Boot Manager    [COLOR="#FF0000"]HD(2[/COLOR],GPT,a39d70f3-f82f-46c4-8526-549b0e0f821d,0x145800,0x82000)/[COLOR="#FF0000"]File(\EFI\Microsoft\Boot\bootmgfw.efi)[/COLOR]

```
Since Windows boots, the path here must be correct - yet there is no Microsoft folder in sda2 if we believe the post 96 output. I would expect to see Microsoft and Ubuntu folders in there from the installs you did. 

How can that be that the folder is not displayed in the first listing? Not clear at this point. And I wonder what is in the EFI subfolder? I've never seen a second EFI folder there.  

Any comment?

---

### Post by Kinshuk_Lahiri on 2016-09-08
I have no clue. Any experts out there.

> **Dennis N said:**
> What puzzles me is the contents of the EFI partition as taken from post 96:

```
ubuntu@ubuntu:~$ ls -al /mnt/EFI
total 16
drwxr-xr-x 4 root root 4096 Jan  1  1970 .
drwxr-xr-x 1 root root   80 Sep  6 17:55 ..
drwxr-xr-x 2 root root 4096 Jun 17  2014 boot
-r-xr-xr-x 1 root root  512 Aug  6  2015 BOOTSECT.BAK
drwxr-xr-x 5 root root 4096 Feb 18  2015 EFI


```compared to what the efibootmgr outputs in post 98: 

```
Boot0001* Windows Boot Manager    [COLOR=#FF0000]HD(2[/COLOR],GPT,a39d70f3-f82f-46c4-8526-549b0e0f821d,0x145800,0x82000)/[COLOR=#FF0000]File(\EFI\Microsoft\Boot\bootmgfw.efi)[/COLOR]

```
Since Windows boots, the path here must be correct - yet there is no Microsoft folder in sda2 if we believe the post 96 output. I would expect to see Microsoft and Ubuntu folders in there from the installs you did. 

How can that be that the folder is not displayed in the first listing? Not clear at this point. And I wonder what is in the EFI subfolder? I've never seen a second EFI folder there. 

Any comment?

---

### Post by Bashing-om on 2016-09-08
Kinshuk_Lahiri; Morning .

> 
Any experts out there.

certainly not me ... However, I can offer:
> 
I am confused between these two. Whether to erase the Ubuntu 16.04 and re-install it again or select Something Else

that you DO NOT want to " erase disk and install ubuntu" unless it it your intent to delete Windows off your system. That option to erase will do just that !

[INDENT][INDENT]only a bit to try and help
[/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-08
Then how to reinstall ubuntu without affecting the winodws partition?

> **Bashing-om said:**
> Kinshuk_Lahiri; Morning .


certainly not me ... However, I can offer:

that you DO NOT want to " erase disk and install ubuntu" unless it it your intent to delete Windows off your system. That option to erase will do just that !

[INDENT][INDENT]only a bit to try and help
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-09-08
Kinshuk_Lahiri; errrahhh ..

I am reticent to offer advise in respect to things I do not know .. Windows and EFI .
However, what I often do in a dual boot install is to use GParted - the GUI partition editor - from the liveUSB to delete the unwanted partitions .. that gets ya "unallocated" space .. depending on what I now want for the system I may set up the partitions at this stage OR
let the install wizard take care of the partitioning details by pointing the installer to this unallocated space (something else option ).
Be aware, in the partition editor .. once you commit, there is no undo . Make sure you are working with the partitions that you want .

[INDENT]no biggy
[INDENT][INDENT][INDENT]all part of the learning curve
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Kinshuk_Lahiri on 2016-09-09
Finally, I formatted the ubuntu partition and re-installed ubuntu again. Both Windows and Ubuntu are working fine.  :) . However, Wifi was not working on Ubuntu but then installed drivers for it and now replying to the thread from ubuntu running on the machine. Thanks everyone for their help. 

> **Bashing-om said:**
> Kinshuk_Lahiri; errrahhh ..

I am reticent to offer advise in respect to things I do not know .. Windows and EFI .
However, what I often do in a dual boot install is to use GParted - the GUI partition editor - from the liveUSB to delete the unwanted partitions .. that gets ya "unallocated" space .. depending on what I now want for the system I may set up the partitions at this stage OR
let the install wizard take care of the partitioning details by pointing the installer to this unallocated space (something else option ).
Be aware, in the partition editor .. once you commit, there is no undo . Make sure you are working with the partitions that you want .
[INDENT]no biggy[INDENT][INDENT][INDENT]all part of the learning curve
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-09
Kinshuk_Lahiri; Outstanding !


You do good work :)

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

