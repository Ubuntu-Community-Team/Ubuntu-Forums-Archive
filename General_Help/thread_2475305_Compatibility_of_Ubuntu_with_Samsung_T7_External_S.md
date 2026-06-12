---
title: "Compatibility of Ubuntu with Samsung T7 External SSD"
date: 2022-05-21
forum: General Help
---

### Post by volt-switch on 2022-05-21
I want to install ubuntu on an external ssd but I am wondering if there will be any compatilbity issues, some responses I've searched online say that the encryption will cause problems, some seem to say it will be fine. I would like to know if this is a good idea or not as I don't have space to do a dual boot, and it would be convineint for me to install things on an external ssd, thank you for your help.

---

### Post by oldfred on 2022-05-21
The encryption only works in Windows. 
But you should be able to remove it & repartition with an ESP & ext4 partition for / (root). Any other partitions are optional.

But installs to external drives have a bug.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26), also other options posted
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)


Second drive 
[https://askubuntu.com/questions/1296065/dual-booting-w10-ubuntu-with-2-separate-ssds-in-uefi-mode/1296153#1296153](https://askubuntu.com/questions/1296065/dual-booting-w10-ubuntu-with-2-separate-ssds-in-uefi-mode/1296153#1296153) & 
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079)
[https://askubuntu.com/questions/327229/installing-ubuntu-in-a-external-hard-drive-and-not-placing-grub-of-my-c-hard-dr](https://askubuntu.com/questions/327229/installing-ubuntu-in-a-external-hard-drive-and-not-placing-grub-of-my-c-hard-dr)

---

### Post by mIk3_08 on 2022-05-23
> **volt-switch said:**
> I want to install ubuntu on an external ssd but I am wondering if there will be any compatilbity issues, some responses I've searched online say that the encryption will cause problems, some seem to say it will be fine. I would like to know if this is a good idea or not as I don't have space to do a dual boot, and it would be convineint for me to install things on an external ssd, thank you for your help.
I experience this running Linux Ubuntu Operating System in my external storage with encryption using my laptop so far I did not encounter any error.  so far the performance was amazing. I did not explore much of it coz it was just my experimental and I only run it for a few days. All in total, it was good. Regards and Cheers.

---

### Post by dragonfly41 on 2022-05-23
I don't use encryption but I do endorse using external SSD's to run Ubuntu .. externally.
But to achieve performance run the SSD on a USB 3.0 port, not USB 2.0 port.

I use a dual docking bay .. Startech .. and this makes it easy to have twin SSD's running through a single USB 3.0 port on a Dell tower.

I am now about to swap the internal HDD (containing Windows) with an SSD. I can use the HDD as another backup drive.

I should add that I create a boot/EFI partition on external Ubuntu SSD's which allows me to boot Ubuntu even when internal HDD/SSD is powered down.  I also installed rEFInd.

---

### Post by mIk3_08 on 2022-05-24
For me, encryption is very important specially for external drive. Because once your hdd/sdd is encrypted it is very safe when you lose it. It can't be easily be open/explore by anybody except you. That's why I encourage the users to use encryption because it can help you specially when you have a very important file to be protected. This is the best way. Regards and cheers.

---

### Post by ActionParsnip on 2022-05-24
The physical connection doesn't matter to Linux. It will boot. You can setup encryption as part of the installation process

---

### Post by dragonfly41 on 2022-05-24
> [COLOR=#000000]For me, encryption is very important specially for external drive.[/COLOR]

I know that. I once worked in crypto and biometrics field.
But balancing risks there is very little risk of my drives being stolen from home.
Balance that against losing crypto keys to gain entry to encrypted data.
Far too many passwords to manage already. Convenience vs. risk.

Incidentally, my internal Toshiba HDD was swapped with SSD last night and external Ubuntu (SSD) booted up fine through rEFInd even though the Windows boot was gone. I now just have to reinstall Windows with a pre-prepared Windows bootable USB created using Rufus.

---

### Post by mIk3_08 on 2022-05-25
> **dragonfly41 said:**
> Balance that against losing crypto keys to gain entry to encrypted data.
 In my case, I do have this LibreOffice where I kept all my users and password info there. In that LibreOffice file is also encrypted. I only have two encryption in my mind that is in the LibreOffice file and to open the encrypted archive where my LibreOffice file is located. The rest of my accounts info like, users and passwords and etc is inside that LibreOffice file. I don't have to memorize all of them as they are too many. All I had to focus is the encrypted key to open the archive and the password to open my LibreOffice file. And I do also have a back up of this encrypted archive. it was place in my USB, external storage, and in my media storage with all same encryption key that I used. Anyway it was just my idea. Just sharing it. Regards and cheers.

---

