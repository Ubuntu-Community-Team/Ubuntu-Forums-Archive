---
title: "Attempting Boot Repair disk to Repair Grub - Get this Error"
date: 2020-04-22
forum: General Help
---

### Post by Rick St. George on 2020-04-22
Have dual boot HP Elitebook 6930p with Win7 and Xubuntu v18.04. Last update for Win7 corrupted my C: partition. Restore successful. Now Laptop won't boot at all. Get "No Operating System". I blieve if I can restore Grub, the laptop will boot.

Using Boot Repair disk and last Terminal Command is: 

```

lubuntu@lubuntu:~$ sudo chroot "/mnt/boot-sav/sda2" apt-get install -y --force-yes grub-pc linux

```

Then I get:

```

W: --force-yes is deprecated, use one of the options starting with --allow instead.
E: unable to locate pckage linux

```

Replaced "linux" with "xubuntu" still didn't work!  Any suggestions would be appreciated.

---

### Post by CelticWarrior on 2020-04-22
My only suggestion is to use Boot Repair in a live session after entirely removing Windows 7 which is now out of support.

---

### Post by Rick St. George on 2020-04-22
What I did was;

```

sudo mount /dev/sda2 /boot
sudo grub-install --boot-directory=/boot /dev/sda
```

Rebooting Laptop and GRUB prompt showed, then ls to list the drives, and found my Xubuntu installed on (hd0,msdos2). So, followed instructions here;
[https://linuxhint.com/grub_rescue_ubuntu_1804/](https://linuxhint.com/grub_rescue_ubuntu_1804/) 

Then, after bootup into Xubuntu, went to Terminal and did this (since OS could not find "update-grub");

```

sudo grub-mkconfig -o /boot/grub/grub.cfg

```

File generated and able to BOOT Laptop. However, it does not show the Windows partition / Boot Option. I also have Zorin installed on another partition and that does show. But no matter what I try, can't get Windows to show after Update-Grub!  

Any suggestions???

---

### Post by Rick St. George on 2020-04-23
I might also note, have uninstalled Grub-common and re-installed Grub-PC. And tried setting up /etc/grub.d/40_custom as shown here;
[https://askubuntu.com/questions/197868/grub-does-not-detect-windows](https://askubuntu.com/questions/197868/grub-does-not-detect-windows)

Still won't show!?!?

---

### Post by yancek on 2020-04-23
In your initial post, you indicate you have boot repair.  In post 2, a member suggested you post the output of boot repair which you should do with the Create BootInfo Summary option so that you can post the link here.  That will provide details of the system and someone may be able to make a suggestion to help solve the problem.  What you have provided so far is too vague and not really helpful.

You also indicate that your windows system partition was 'corrupted' and after doing a restore, it failed to boot.  Is that the case?  I guess the restore did not work if that is the result.  If your windows boot files are damaged there isn't anything you can do from Ubuntu or boot repair.  Posting the boot repair output might provide some useful information.

---

### Post by Rick St. George on 2020-04-23
Thanks Yancek, Restore of Win7 was successful with Acronis using an earlier BU file (initial Win7 install - no added programs). Boot Repair has many bad comments and is not suggested. I think it put two different Grubs on the machine and "binded" wrong info. Not sure. Thats why I uinstalled Grub-common and Installed Grub-pc as this is an older Laptop with MBR (I'm pretty sure). Xubuntu and Zorin remain installed and show up in Grub. Just now, I got the Windows partition to show in Grub upon Reboot, and Actually I get ... 

```

Error: unknown argument --s
Error: invalid signature

```

Am I getting close? Also of note, Grub doesn't show MemTest, but shows 2 vmlinuz and 2 initrd ???

---

### Post by Rick St. George on 2020-04-23
> **yancek said:**
> In your initial post, you indicate you have boot repair.  In post 2, a member suggested you post the output of boot repair 

NO, He did not!

> 
You also indicate that your windows system partition was 'corrupted' and after doing a restore, it failed to boot. 

NO, I did not. Post 3 I wrote it was successful. Please continue reading. How you totally misread all that is beyond me! Read Post 6 above!

---

### Post by Rick St. George on 2020-04-23
Retracing my steps, and knowing that during RESTORE with Acronis - I also checked Restore MBR. I believe that's what messed things up. Did another RESTORE without MBR checked. Then Booted into Xubuntu, Uninstalled Grub, Re-Installed Grub-pc. ReBoot Laptop and clicked on Windows 7 ... 

And Behold - Win7 came up and all is good. In the process - I learned a lot about Grub. But can't v18.04 use System-D ???
And now the fun of doing it all over again with v20.04 ... Yeepppeee ! ! !

---

