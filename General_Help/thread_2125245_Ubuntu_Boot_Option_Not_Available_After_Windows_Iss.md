---
title: "Ubuntu Boot Option Not Available After Windows Issue"
date: 2013-03-13
forum: General Help
---

### Post by daTomoT on 2013-03-13
Hiya folks,

I'd finally got my Ubuntu working perfectly, and now I can't use it. Shucks. Unhappy, very much so. Anyway, on to the issues.

I recently fixed up laptop (on Which I am dual booting Windows 7 and Ubuntu 12.10) from an error I believe was with windows. The error was, precisely 'NTLDR is missing, Press CTRL-ALT-DELETE to reboot). Well I plugged in my Windows 7 disk, entered the recovery mode and ran the automatic fix option. On the second try, my Windows 7 now boots in perfectly.

However, it boots straight to Windows 7. I have Ubuntu installed in a partition on the same internal hard drive, and before the NTLDR issue, it'd take me to the operating systems list where I'd select Ubuntu (or WIN7 occasionally). Now, it goes straight from the Dell logo to the 'Starting Windows' screen.

I guess if I have to, I can format my (U:) drive where Ubuntu lives and reinstall from within Win7, but I'd rather not, as 12.10 doesn't support many of the drivers my latop needs (including WiFi and touchpad) and it's a pain to get a hold of them! 

Does anybody know how I can force my laptop to show me the operating system list instead of booting straight to (C:)?

Tom.

---

### Post by carl4926 on 2013-03-13
You need your original Ubuntu install media or if necessary download it again
thenTry fixing with the Ubuntu CD 
   * Open a terminal and type
$ sudo fdisk -l 
   
* Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. 
Now we need to mount the filesystem to /mnt
$ sudo mount /dev/sda1 /mnt 
   
* Now mount the rest of your devices
$ sudo mount --bind /dev /mnt/dev 
   
* Now chroot into your system
$ sudo chroot /mnt 
   
*      When that is done you need to run update-grub to create the configuration file.
$ update-grub 
   
*      To install GRUB 2 to the MBR, next you need to run 

grub-install /dev/sda

---

### Post by carl4926 on 2013-03-13
The forum is messed up and all formatting  -  Stand by and see if I can edit that mess

---

### Post by carl4926 on 2013-03-13
Trying to edit the mess> **carl4926 said:**
> You need your original Ubuntu install media or if necessary download it againthenTry fixing with the Ubuntu CD    * Open a terminal and type$ sudo fdisk -l    * Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt$ sudo mount /dev/sda1 /mnt    * Now mount the rest of your devices$ sudo mount --bind /dev /mnt/dev    * Now chroot into your system$ sudo chroot /mnt    *      When that is done you need to run update-grub to create the configuration file.$ update-grub   *      To install GRUB 2 to the MBR, next you need to run grub-install /dev/sda

---

### Post by carl4926 on 2013-03-13
No it's not working

---

### Post by carl4926 on 2013-03-13
There it's all back OK now

---

### Post by daTomoT on 2013-03-13
I used Wubi for the original install, so I can't remember which sda if was. Is there a way to tell which? I think it was potentially 3, so I starte going through your instructions, and completed one and two successfully. 

However, on inputting 
'Sudo mount --bind/dev /mnt/dev'

It says 'mount: mount point /mnt/dev does not exist'

What does this mean?

---

### Post by carl4926 on 2013-03-13
Wubi is totally different

Start a new thread or as a mod to move this one

---

### Post by daTomoT on 2013-03-13
Is that necessary? I have a live disk that I've booted from.

---

### Post by carl4926 on 2013-03-13
> **daTomoT said:**
> Is that necessary? I have a live disk that I've booted from.
If your installation was WUBI then you ought to ask in the WUBI section
+ I have never used WUBI

---

### Post by Mark Phelps on 2013-03-13
Your NTLDR error message is a strange one as MS Windows quit using that when Vista came along.  Win7 uses the BCD for booting, not NTLDR.

Wubi installs to a virtual file system INSIDE an existing Windows partition, and while repairing startup might have corrupted that, I don't think it did.

Look inside your Win7 OS partition and see if there is a root.disk file -- that is the file Ubuntu uses for its filesystem.

I'm not a Wubi user, but what I think MIGHT work is the following:
1) Save the root.disk file to an external drive
2) See if there is an option in Programs and Features to remove Ubuntu, if there is, remove it.
3) Reinstall using Wubi
4) Confirm that when you reboot, you now get an Ubuntu option in the Windows OS selection screen
5) Replace the new root.disk file with the old root.disk file
6) When you reboot, you should still get an Ubuntu option but now, you should have your old Ubuntu back.

---

