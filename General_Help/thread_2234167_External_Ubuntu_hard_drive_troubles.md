---
title: "External Ubuntu hard drive troubles"
date: 2014-07-12
forum: General Help
---

### Post by jacob25 on 2014-07-12
I have installed Ubuntu 12.04 32-bit onto an external hard drive which I want to be able to plug into any computer and using the GRUB bootloader, either startup into the computers existing OS, or into Ubuntu itself (along with Ubuntu's recovery mode).

Now, I have no idea if that is possible, it's not to big of a bump, all I have to do if unplug the hard drive to boot into the computers OS, but it would be cool if I could just have an option to boot up whatever is on /dev/sda.

Second of all, on my main PC (Windows 7, 64-bit, dual monitors) I can't seems to get Ubuntu to work with the second monitor. I was able to run it for the first time, and configure Ubuntu with dual monitors no problem, but now, when I get to the login screen, the second monitor does what can only be described as "derp" and doesn't do what it is supposed to do. i don't want to install the drivers for any specific video card, since I will be changing what system it will be running on constantly. I should also mention that my primary monitor is 1920x1080 connected with HDMI, and my secondary is 1280x720 connected through VGA, and I may as well include that the secondary monitor is actually a TV (don't know if it'll help, but I'm always surprised by solutions in Linux sometimes).

A few notes:
I need Ubuntu 12.04 32-bit, as I am fairly certain it will run on any machine created in the past 10-15 years, as it is the last non-PAE distro of Ubuntu, and it's 32-bit, which is quite common in older computers (duh)

I plan on also installing 14.04 64-bit onto the external drive as well to work with newer systems. Is it possible that the monitor thing would be fixed if I run 14.04 on my windows machine?

Any help is appreciated!

Just as a quick afternote, I'm actually writing this with the external drive, but I'm running it on an old system with a corrupt XP install, and with one monitor it works fine.

---

### Post by yancek on 2014-07-13
As to installing Ubuntu on an external hard drive and booting from that hard drive, you would need to install the Grub bootloader to the master boot record of that drive.  If your machine has one internal hard drive and your external drive then it should be /dev/sdb so you would:  sudo grub-install /dev/sdb  You would then need to select that drive as the boot drive when booting another machine.

Because you are going to be using it on different machines with different hardware there is no guarantee that it will work on all.  To boot from this drive with an option to boot from an internal drive, you could put a chainloader entry in the Ubuntu grub.cfg file but it would need to point to a specific partition entry and would only work if the internal drive on the other partition had boot files on that partition.

---

### Post by jacob25 on 2014-07-13
That's what I thought (about grub only being able to boot a partition, not a drive).

I had already installed the grub onto my external drive, as I knew I would need it there for what I want to use it for.

Following with what you said about grub booting partitions, couldn't I "brute force" it and create options to boot sda1, sda2... (And so on as would be logical)? Or should I just stick with my normal remove the external drive method?

---

### Post by yancek on 2014-07-13
You should be able to do that.  An example below of a chainload entry.  The insmod entry might need to be changed in some instances and obviously the partition number would depend on which partition you are pointing to.  The example below is sda1.  That would need to be changed for each entry.

> menuentry 'CHAINLOAD' {
insmod ext2
set root=(hd0,1)
chainloader +1
}

---

### Post by jacob25 on 2014-07-13
Just to make sure, but I would replace ext2 with ntfs if I were trying to boot a Windows version, correct?

---

### Post by Bucky Ball on 2014-07-13
You would probably need to handcraft your fstab for every situation. /etc/fstab now uses UUID numbers that are specific to the partition. They are going to change with every machine you plug into, so forget /etc/fstab unless you use another method than UUID. Fine having chain load entries, but where you going to put them and what's the point when you don't know the sd** of the drive you are trying to chainload? You will need to find that out and tweak accordingly. And to tweak accordingly, you're going to need a machine that will reliably run with your external boot (i.e. you external install has the correct video drivers and wireless if you need it).

The other thing(s) is, switching from machine to machine, the OS on the external drive might boot, but there is no guarantee you will have the appropriate video drivers or wireless drivers for that machine. The idea of installing to an external hard drive so you can boot on different machines is nice in theory, not so simple in practice. 

If you have the time to tweak and fool around on every machine you plug into, fine. If you just want to plug the drive into any machine and boot from it, that may be problematic. Some machines everything will work 'out of the box'. Others you might spend hours getting video or wireless to work and still come up empty handed. Good luck.

---

### Post by jacob25 on 2014-07-13
I've booted the drive to three different computers, and they all seem to work with a single monitor. Since my main goal is to create an easy way to access the files on a computer if something happened to the OS, I'm usually going to be working with... PC n00bs, who usually do not have multiple monitors. For the situations where I'm trying to actually setup a temporary workspace with the external drive, I will actually try to screw around with video settings, but I have no idea how to do so if the screen doesn't function properly in the first place, which is why I don't want to screw around with more permanent video settings.

I will however probably install 14.04 on it for at home use, at which point I will download the proper drivers, and tweak the settings to my needs, but the weird second monitor thing happened after a reboot, not switching the drive elsewhere.
As I said, it worked the first time, but then it glitched on reboot, and I have no idea whatsoever what happened, but I still need to know how I can fix it.

For specific unrelated reasons, I installed Ubuntu with the mini.iso. Is it possible that a package that comes with the normal install was not installed, so that the 12.04 login screen (where when you move the cursor from one screen to the other, it moves where the login password bar is), was not installed or something?

---

### Post by Bucky Ball on 2014-07-13
If you have no graphical login try installing lightdm:

```
sudo apt-get install lightdm
```

Reboot. You could replace 'lightdm' in the command above with 'gdm' or 'xdm' or any other display manager you fancy. lightdm is lightweight and fast.

Did you go for a machine profile during the mini install or did you install everything manually post-install (when you reboot and login at a cursor then 'sudo apt-get install 'the-things-you-want'')? If the latter, it would help to know what you have installed so far. I use mini installs with xfce4 desktop environment and need to install a login manager, window manager and a few other things to get things working nicely.

---

### Post by yancek on 2014-07-13
> Just to make sure, but I would replace ext2 with ntfs if I were trying to boot a Windows version, correct? 		

Yes, you would.  This could get to be a very cumbersome grub menu.  If you have various computers with different operating systems, you would need an insmod ntfs for a windows entry on sda1.  If it had a Linux system you would need the insmod ext2 for sda1, duplicate entries for each partition.  Usually with a Live CD, you will have an option to boot from local hard drive which seems like a simpler solution.  You would then access the bootloader on that machine and boot whatever is there.  Putting a Live CD on a flash drive with persistence would seem to me to be a more appropriate solution.  Use unetbootin or the Ubuntu usb-creator.

---

### Post by at_first_light on 2014-07-16
There is bootable tool called Super Grub2 Disk that can be used to create grub entries on the fly in your ram. Just plug your Ubuntu installation into the computer, make the computer boot from cd/dvd, and a list of all supported operating systems will be made. From this list you should be able to boot locally installed operating systems or your external Ubuntu installation. The downsides of this method are that your existing Grub2 entries won't be used preventing the use of special parameters you might want. It supports Windows and Linux. :)

Super Grub2 Disk website: [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

However when you install an operating system it configures itself for that hardware. Ubuntu may not boot on the other system if it doesn't like the change in hardware. Your networking (internet) will also likely not work. :(

---

