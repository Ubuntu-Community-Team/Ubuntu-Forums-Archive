---
title: "GRUB menu updates in customizer, but not on startup..."
date: 2014-02-02
forum: General Help
---

### Post by Hvidemose on 2014-02-02
I have the GRUB customizer, and I customised the startup menu, so that it had my preferred order. But after a system update, these two came in above what i customised before:
[LIST]
[*]Ubuntu, with Linux 3.11.0-15-generic
[*]Ubuntu, with Linux 3.11.0-15-generic (recovery mode)
[/LIST]

The problem is now, that what ever I change in the customizer again, the change wont have any effect on the startup menu, even though the change is sill there when I go back to the customizer...

Is there a way to fix this?

---

### Post by jeanjd63 on 2014-02-02
Hello.
What is your preferred order? 
May be you don't need any customizer.

---

### Post by kajoky on 2014-02-02
You could try [B]sudo update-grub
[/B]If that does not solve the problem, you probably need to [B]sudo grub-install /dev/sda
[/B]If you have more than one operating system then you may need to use something besides /dev/sda
I have two linux operating systems in separate partitions. So I use either /dev/sda1 or /dev/sda6
If you are dual booting with Window, then search for more information as I do not know what this might do with respect to Windows.
I don't have any experience with dual booting with Windows, but from what I read it can be problematic.

---

### Post by Hvidemose on 2014-02-02
> Hello.
What is your preferred order? 
May be you don't need any customizer.

The preferred order would be:

 
[LIST]
[*]Lubuntu

[*]Windows XP

[*]Advanced options for Ubuntu

[LIST]
[*]Memory test (memtest86+)

[*]Memory test (memtest86+, serial 		console 115200)

[*]Windows Recovery Environment 		(loader) (on /dev/sda1)

[*]Ubuntu, with Linux 		3.11.0-15-generic

[*]Ubuntu, with Linux 3.11.0-15-generic (recovery mode)
[/LIST]
 
[/LIST]
 
And this is how it is set in the GRUB Customizer looks.
This is how it appears at starup, no matter how i change the customizer:
 
[LIST]
[*]Ubuntu, with Linux 	3.11.0-15-generic

[*]Ubuntu, with Linux 	3.11.0-15-generic (recovery mode)

[*]Lubuntu

[*]Windows XP


[*]Advanced options for Ubuntu
[LIST]
[*]Memory test (memtest86+)
[*]Memory test (memtest86+, serial 		console 115200)
[*]Windows Recovery Environment (loader) (on /dev/sda1)
[*]Window 7 (something something, 		which is the same as the Windows XP)
[/LIST]
[/LIST]

If I run the **sudo update-grub**, it says:```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
error: syntax error.
error: Incorrect command.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 200
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.done
```

And if i type **sudo grub-install /dev/sda** it says:
```
Installation finished. No error reported.
```

Should i try to install to MBR, or what does that do?

---

### Post by grahammechanical on 2014-02-02
Grub Customiser has an option to install Grub to the MBR. I have found that there is a need to run that instruction to fix any changes that are made in Grub Customiser into the Grub boot menu. That instruction in Grub Customiser is the same as sudo grub-install /dev/sda which installs Grub into the MBR of sda, the first hard disk.

Whenever we receive an updated Linux kernel (vmlinuz) then a new Grub configuration file is generated and the newest kernels are put at the top of the list. Which is the way it should be. It does mean that we need to run Grub Customiser again.

Regards

---

### Post by jeanjd63 on 2014-02-02
If you want lubuntu in first choose, the best way is to install the lubuntu grub in mbr. 
You boot on lubuntu and you do :
[B]sudo  update-grub
sudo  grub-install  /dev/sda[/B]

If the grub lubuntu is good for you in ubuntu you have to suppress grub-customizer :
1) you suppress grub-customizer and grub-pc
[B]sudo  apt-get  purge "grub *"
sudo mv  /etc/grub.d /etc/grub.old[/B]
2) you install grup-pc 
**sudo  apt-get install  grub-pc**
[B]sudo  dpkg-reconfigure  grub-pc
[/B]in the 2 first screens you do ok and for the third you choose the partition / for grub (ie /dev/sdXY).

---

### Post by Hvidemose on 2014-02-02
Thanks for the good answers, but i screwed it up trying do do something. So i just reinstalled lubuntu, updated the system, installed grub customizer and then it worked.

---

