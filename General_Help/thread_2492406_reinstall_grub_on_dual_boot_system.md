---
title: "reinstall grub on dual boot system"
date: 2023-11-09
forum: General Help
---

### Post by garyed on 2023-11-09
I have a Dell Inspiron laptop dual booting Ubuntu & Windows 10 for a few years without a problem.  
I was planning on upgrading the HD so I was playing around in the bios & trying to get a gparted live usb to boot up just see how things might work. 
Anyways I couldn't get the bios to recognize the usb until I changed the boot mode from efi to legacy. I never made any changes except in the bios but when I tried to put things back to where they were the Unbuntu boot loader 
did not show up like it did before. Now it shows Windows bootloader in the Bios instead of Ubuntu. 
I'm assuming I'm going to have to reinstall grub efi & I'm not sure how to do it without messing anything up on the drive. 
I can boot from the 18.04 live usb which I think is what I used to originally set up the dual boot system to begin with. 
There's a lot of different steps on the web to do it which makes it confusing as to which way to go.  I was wondering if anyone with experience here could walk me through it.

---

### Post by garyed on 2023-11-09
Here's a shot of gparted & I only have 1 hd on the system. 
I think my grub files are on sda7

---

### Post by Rubi1200 on 2023-11-09
From the liveUSB please run the boot info script in my signature and post the link to the pastebin back here. No repair, just the results.

The script will tell us where everything is and what might need to be done to fix the problem.

Thanks.

---

### Post by garyed on 2023-11-09
Here's the link:
[http://paste.ubuntu.com/p/pFeQ7ShwSM/](http://paste.ubuntu.com/p/pFeQ7ShwSM/)

but I tried the link & it doesn't work.
How do I try it again?

---

### Post by garyed on 2023-11-09
I ran the boot-repair command again & this time I clicked on the recommended repair & it fixed it. 
Now my computer boots like normal into Windows or Ubuntu as needed. Thank you for that link. 
I also got another link that works if you want to see the data: [https://paste.ubuntu.com/p/tzV8fWCPmS/](https://paste.ubuntu.com/p/tzV8fWCPmS/)

---

### Post by Rubi1200 on 2023-11-09
Glad to hear things worked out in the end :-)

Since 18.04 has reached EOL I would recommend backing up important data and upgrading to 20.04.

Please mark this thread Solved using Thread Tools at the top of your first post.

---

### Post by garyed on 2023-11-09
Just to let anyone know who runs into this problem I used these commands from the link you listed after booting from a live Ubuntu usb.
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt update
sudo apt install -y boot-repair && boot-repair 

I ran the command "boot-repair" to get another chance to let it fix the problem & it worked.

---

### Post by yancek on 2023-11-10
As suggested on the boot repair page, it is better if you are not familiar with the Grub bootloader, to run boot repair with the Create BootInfo Summary option and post the link you are given here or at another forum.

If you changed from EFI to Legacy in the BIOS to boot the GParted iso, you simply should have changed it back to EFI in the BIOS and disabled Legacy.  If you needed to change to Legacy boot for GParted, you had the wrong version (non EFI) as you clearly have an EFI install on the computer.  Also, Ubuntu install disks/usbs have gparted on them so there should be no need to download the gparted iso if you keep the Ubuntu install usb.

---

