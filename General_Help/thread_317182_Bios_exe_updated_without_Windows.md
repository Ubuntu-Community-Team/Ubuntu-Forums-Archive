---
title: "Bios exe updated without Windows?"
date: 2006-12-12
forum: General Help
---

### Post by aum11 on 2006-12-12
Have just installed 6.10 on a friend's Dell 100 laptop.

There are screen resolution problems which seem to require a bios update.  However, the bios update is in the form of .exe.  And I did a clean install so now there is no more windows in which to download and install the bios update.

Is there some way to use Ubuntu to install the update?  Or any other solution.  This must be a common problem for those who have left Windows behind.

Note that there is another dual boot machine here as well if that can assist.

Thanks for Your wisdom.

---

### Post by bodhi.zazen on 2006-12-12
See biosdisk

[http://linux.dell.com/projects.shtml#biosdisk](http://linux.dell.com/projects.shtml#biosdisk)

---

### Post by aum11 on 2006-12-12
Thanks bodhi.zazen for Your quick advice...it set me on the right trail and now the bios has been successfully updated.

However I would suggest that anyone else in the same situation would be well advised to use the following site,
 [http://www.geocities.com/randomnumbergenerator2001/](http://www.geocities.com/randomnumbergenerator2001/)
because it has an even easier method using a zip file.

All the best.

---

### Post by apelete on 2006-12-12
I have exactly the same problem, BIOS upgrade, on a Thinkpad X60.
The file provided by IBM only works if you have DOS, Windows consequently, on your hardware. I wiped Win weeks ago and I would like to get a BIOS upgrade file for my system.

NB: I tried ThinkWiki guide but failed: I DO NOT want to install FreeDos in order to flash my BIOS...

---

### Post by kevinatkins on 2006-12-12
One method I have used was to use DosEMU, which is, as the name suggests, a Dos emulator. Nice thing about this is you can run everything from within Ubuntu - no need to install FreeDos (although it is possible to run FreeDos entirely from the CD..)

---

### Post by ciscosurfer on 2006-12-13
I have written a HOWTO discussing how to flash your BIOS.  You can find it here: [HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=318789")

---

### Post by apelete on 2006-12-13
I may be stupid, but I didn't succeeded in creating a bios Boot CD for my laptop using the howto...
When mounting the FDOEM image as loop, it is not possible to copy anything into the so mounted image, because the mounted folder is already full, without any space left !!!

Did anyone try this ?!!

---

### Post by ciscosurfer on 2006-12-13
> **apelete said:**
> I may be stupid, but I didn't succeeded in creating a bios Boot CD for my laptop using the howto...
When mounting the FDOEM image as loop, it is not possible to copy anything into the so mounted image, because the mounted folder is already full, without any space left !!!

Did anyone try this ?!!The image is expandable in the sense that all you are doing is initially mounting 6 files from **FDOEM.144** to **/mnt/temp**.  Your **/mnt/temp** directory should be newly created and should be empty.  Additionally, you will want to make certain that you actually have freespace left on your drive in order to do this (the file sizes are very small--from an initial gunzip of roughly 10k, to a full **/mnt/temp** directory with new flash program and new bios rom of 100k--it's typical for the total size of **/mnt/temp** (which remember, is FDOEM.144 at this point) not to exceed 50k.  

To do this, you must first issue: **gunzip FDOEM.144.gz** and this will gunzip the image and will then be called **FDOEM.144**

Then as root (use **sudo /bin/bash** to get root) you will make a temp directory under mnt: **mkdir /mnt/temp**.  Then you will issue: **mount -o loop -t vfat FDOEM.144 /mnt/temp**.

Next you need to read the section in my Howto that describes how to copy over files to the image.  This section is called [B]Unzipping the .EXE

[/B]Follow those directions and use [B]
cp name_of_flash_program /mnt/temp
cp name_of_new_bios_rom /mnt/temp
[/B]

---

### Post by apelete on 2006-12-13
What if the bios image isn't an exe but an iso to be burned initially ?

---

### Post by ciscosurfer on 2006-12-13
> **apelete said:**
> What if the bios image isn't an exe but an iso to be burned initially ?Then you can mount it with the following code, basically removing the vfat switch:```
mount -o loop name_Of_iso.iso /mnt/temp
```Then you can change directories to look at it, or simply enter in the following the see the contents of /mnt/temp at that point:```
ls -l /mnt/temp
```

---

### Post by apelete on 2006-12-14
> **ciscosurfer said:**
> The image is expandable in the sense that all you are doing is initially mounting 6 files from **FDOEM.144** to **/mnt/temp**.  Your **/mnt/temp** directory should be newly created and should be empty.  Additionally, you will want to make certain that you actually have freespace left on your drive in order to do this (the file sizes are very small--from an initial gunzip of roughly 10k, to a full **/mnt/temp** directory with new flash program and new bios rom of 100k--it's typical for the total size of **/mnt/temp** (which remember, is FDOEM.144 at this point) not to exceed 50k.  


My BIOS image file is 3.3Mo when mounted. I can't copy the files over to FDOS mounted image directory...
Should I try the other way around, e.g copy from FDOS mounted image file to the BIOS mounted image file ?

---

### Post by ciscosurfer on 2006-12-14
> **apelete said:**
> My BIOS image file is 3.3Mo when mounted. I can't copy the files over to FDOS mounted image directory...
Should I try the other way around, e.g copy from FDOS mounted image file to the BIOS mounted image file ?**Remember, flashing your BIOS is a dangerous activity, and you should know what you are doing before attempting to flash your BIOS.  Just a healthy reminder.** :-)

*[SIZE=3]If the ISO you've downloaded to flash your BIOS already contains the flashing progrom and new BIOS file, then there is no need to continue on below.[/SIZE]*

To make this work by using an ISO [instead of an .EXE files(s)] that has been created already in order to be burned and used to boot up and flash your BIOS, in the event you need to for some reason, add files to ISO (and b/c ISO images are read-only), we need to create an temp directory for the ISO, then copy those files over a read/write directory and then add the other files (BIOS flash program as well as the new BIOS file to be used to flash your BIOS).

What I recommend doing in this situation, is to copy over the necessary flashing files to /mnt/temp (from /mnt/iso which we will create in a moment) and then following the steps as before in my HOWTO to create the bootable CD for flashing.  [B][I]

The code below is an alternative way of doing this[/I][/B].  **Again, I would recommend reading my [HOWTO for the original procedure]("http://www.ubuntuforums.org/showthread.php?t=318789").**

We can copy over the read-only fielsystem of the ISO to a read/write direcotry, in order to manipulate it```
sudo mkdir /mnt/iso
sudo mkdir /mnt/temp
```***Now, let's change directories to where the ISO is located and then mount up the ISO to /mnt/iso***```
sudo mount -o loop the_filename_of_the_iso_you_have_here.iso /mnt/iso
```Next, let's copy over all those files to /mnt/temp so we can add files to it (you BIOS flash program, as well as the new BIOS file)```
cd /mnt/iso
sudo cp -R * /mnt/temp
cd #to location where your BIOS flash program and new BIOS file are
sudo cp *BIOS_Flash_Program* /mnt/temp
sudo cp *New_BIOS_file_to_be_added* /mnt/temp
ls /mnt/temp #to see all of your files: the ISO files as well as the BIOS flash program and new BIOS file
cd #to go back to home directory (as a starting point again)
```Let's create a new ISO to be used with our new files.  The first command will setup mkisofs if it's not already on your system```
sudo aptitude update && sudo aptitude install mkisofs

mkisofs -o /home/<your_User_Name_here>/myNewBIOS.iso -R -J /mnt/temp
```After the ISO is created, you can again, here, check to make sure the ISO was written correctly with all the new files by mounting it as a loopback device```
sudo mkdir /mnt/checkISO
sudo mount -o loop myNewBIOS.iso /mnt/checkISO/
cd #back to home direcotory
sudo umount /mnt/checkISO
```If you have trouble with the mkisofs step, a good place to start looking is **man mkisofs**.

---

