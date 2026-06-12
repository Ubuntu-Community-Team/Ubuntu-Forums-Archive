---
title: "Unable to start windows after installing Ubuntu"
date: 2015-05-17
forum: General Help
---

### Post by Oria on 2015-05-17
Hello everyone, nice to meet you all, my name is Oria.

I'm doing a university project in Python and it's much easier to work and get packages in Ubuntu so today me and my supervising professor installed Ubuntu on my Asus G53JW laptop.

If I understand correctly, Ubuntu was installed in a different hard disk than my windows installation, as to avoid problems.

Alas, it was not to be. The problems arrived anyway. I can't boot to windows. The boot menu shows me 3 options:

p4: ST95005620AS
P0: ST95005620AS
P1: my DVD ROM

So obviously either P4 is Ubuntu and P0 is windows, or the other way around.
when I try to boot from P0, it load ubuntu without any issue.
When I try to boot from P4, I get the following error message an error message that says windows couldnt load. this is because a change in hardware or software, status: 0xc0000225 required device is inaccessible.

It should be noted I'm a complete newbie when it comes to Ubuntu, I really have very little idea what's going on and what was suggested in other topic like this (hence why im making this one) but here is what I tried:

1) I tried installing and updating Grub, whatever that may be. Made no difference, still unable to load windows
2) I tried installing Wine (whatever that may be) to open the windows usb/dvd install tool to make a bootable windows 7 usb flash drive, i thought maybe repairing windows would work. I was unable to open the exe file even after installing wine.

My goal is to have a working ubuntu and windows. Right now I'm only able to access Ubuntu. Please help, thank you so much.

---

### Post by Vladlenin5000 on 2015-05-17
Hi and welcome.

1) How did you do it? What commands exactly? Any error messages? 
This should work anytime provide the Windows wasn't previously left in an unstable state - hibernated instead of being fully shut down - or when the dual boot installation wasn't done properly.
2) DON'T.... NEVER again... Use a Windows machine to make that recovery media, the one you should have had before starting any installation (also tell that to your supervising professor)... And backups.

---

### Post by Oria on 2015-05-17
Thank you.

1) I ran the following lines in terminal: sudo get-apt install grub
sudo update-grub

No errors.

2) Lesson learnt.

---

### Post by Vladlenin5000 on 2015-05-17
Regarding 1), your first command is wrong and does nothing. I'm surprised it didn't spit out an error message saying just that... The correct command would be *sudo apt-get install <package_name> *_if you were to install Grub_. You aren't. You're looking for *maybe* install Grub in the correct drive (and yes, you should know what this is/will be).

Generally speaking and assuming the machine has no UEFI but plain old BIOS or legacy - assumption made because of Windows 7 but some manufacturers actually shipped Windows 7 machines with it installed in UEFI mode - you'd want to install Grub in the first drive's MBR (not any partition inside), irrespective of what OS or OSs is/are already present in that drive. Grub is the bootloader therefore it must be called before any other OS specific loader. Again assuming that drive is *sda* then you would need to do:

```
sudo grub-install /dev/sda
sudo update-grub
```


*** Before you try the aforementioned procedure ***

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Follow the "2nd option" to install and run Boot-Repair. At this point DO NOT try any recommended or advanced repairs. Instead use the Create a Boot-info Summary button/feature and post back here so we all know unequivocally what are we dealing with in terms of partitions, bootloaders, etc.

---

### Post by Oria on 2015-05-17
I followed your instructions, and this is the output boot-repair gave me

[http://paste.ubuntu.com/11195534/](http://paste.ubuntu.com/11195534/)

---

### Post by Vladlenin5000 on 2015-05-17
The "good" news: Everything is installed as it used to be, ie, non-UEFI. The only reason this is "good" is because there are way more people able to help you with a traditional installation than there are to UEFI. UEFI is a new thing and it's rather complex
The really good news: Grub is installed where it should be > sda

The probably "bad" news: There's a Windows bootloader in the second drive. _I'll leave it for others to comment_ about whether or not this is really bad or just my assumption.

Now, let's try to solve this without additional tools. It might not be possible without Windows installation (or recovery) media but we can try. So...

- Try the  *sudo update-grub *again or both commands as explained in post #4. Reboot.

What should happen: Grub menu with probably TWO entries for Windows (only one or none boots Windows).
Please post back the results.

---

### Post by Oria on 2015-05-17
Ok, first thing I did just now was just sudo update-grub and reboot. Nothing happened. It just booted Ubuntu, there was no additional menu or anything like that.

Then I tried writing the command you wrote into the console, but after i input "
sudo grub-install /dev/sda"
it says "Probing devices to guess BIOS drives. this may take a long time.
/dev/disk/by-uuid/../../sdb5 does not have any corresponding BIOS drive

I tried doing what's written at [http://askubuntu.com/questions/71867/grub-menu-doesnt-appear-when-pressing-shift](http://askubuntu.com/questions/71867/grub-menu-doesnt-appear-when-pressing-shift) to make the grub menu appear, but doesn't work.

---

### Post by Vladlenin5000 on 2015-05-17
You must select the same drive always, the one that has the boot loader installed, the same that has Windows already, irrespective of the actual location of the system partition for the OS you're trying to boot. That's how a proper dual boot works. 

And you can't really use one command without the other or in a different order. It has to be used exactly as explained in post#4. As such, please try again in the exact order and post the results (the grub-install won't output messages when successful; the grub-update should show several lines including the OSs detected). You can select any area in the terminal with the mouse, right-click and copy (then paste it here using code tags -> Go advanced, press "#" and paste inside).

Obs.: The "sdb5 does not have any corresponding BIOS drive" error message may or may not show up again. If it does please make sure you copy/paste the entire text concerning that message. This message indicates an issue indeed.

---

### Post by Vladlenin5000 on 2015-05-17
One more details that I may have missed before: You may need to change the boot order in BIOS.
Reason: As it seems it's booting from the disk with Ubuntu installed, hence it booting directly with Grub menu. 
It may also work if you install Grub to sdb instead of sda.

---

### Post by Oria on 2015-05-18
As I said...
```
oria@oria-G53JW:~$ sudo grub-install /dev/sda
[sudo] password for oria: 
/dev/disk/by-uuid/../../sdb5 does not have any corresponding BIOS drive.
```

I also tried messing with the boot priority in the BIOS. That doesn't seem to be the issue. As even when I put Windows first, it still says unable to load windows.

and regarding the "it may work if you try to install to sdb rather than sda":

```
oria@oria-G53JW:~$ sudo grub-install dev/sdb
[sudo] password for oria: 
Format of install_device not recognized.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.


```

---

### Post by Oria on 2015-05-18
A friend helped me and we managed to solve the problem.

The solution was to install grub customization as said here [http://www.howtogeek.com/howto/43471/how-to-configure-the-linux-grub2-boot-menu-the-easy-way/](http://www.howtogeek.com/howto/43471/how-to-configure-the-linux-grub2-boot-menu-the-easy-way/)

After we did that, the grub menu appeared as it should, and it showed both ubuntu and windows. And they are both working correctly. Thanks for your help.

---

