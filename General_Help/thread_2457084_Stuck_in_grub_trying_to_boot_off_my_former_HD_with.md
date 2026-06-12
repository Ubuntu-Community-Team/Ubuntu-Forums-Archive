---
title: "Stuck in grub trying to boot off my former HD with Ubuntu 20"
date: 2021-01-25
forum: General Help
---

### Post by 216ann on 2021-01-25
This is a continuation of an issue that initially involved Bios & now has migrated to a grub issue.
See the entire discussion at: ubuntuforums.org/showthread.php?t=2456255&page=2&p=14015707#post14015707
Initially, I was given a newer Toshiba laptop to replace my old HP one.  
I got what I thought was a bright idea to get my old 7200 HD with Ubuntu 20 to replace the 5400 HD in the Toshiba.
It could not boot just sitting there with the Toshiba & Ubuntu logos without ever ending.  
I tried to use a USB to boot off but I had issues with the bios supervisor password which I eventually solved.
Grub recovery did not solve my issues, nor trying to switch it to legacy/CSM & AHCI.
Previously it would say that the initramfs file was missing and give me a grub rescue prompt
Now it says: 
```
error: file '/boot/grub/i386-pc/normal.mod' not found
Entering rescue mode...
grub rescue>
```
I followed the directions at: gutsytechster.wordpress.com/2018/07/24/how-to-resolve-grub-error-file-grub-i386-pc-normal-mod-not-found/
I was able to find the normal.mod in boot/grub.bak/
That allowed me to enter GNU GRUB version 2.04 with a grub prompt
When I tried to boot, it says to load the kernel first.
So I followed the link's instructions and searched for vmlinuz-5.8.0-58-generic & initrd.img-5.4.0-58-generic
I did what the link told me to do regarding insmod linux and then linux with the paths to vmlinuz & initrd.img in the line above and booted.
It seemed to work but then it just ends with a black screen with the cursor in the most upper left corner.
It does not blink or do anything and I did not try to type anything but it sits there for hours.
As a noob, I am not sure what I am doing wrong and I also not sure if maybe I should have picked different files (there are earlier versions of initrd and vmlinuz).
I also tried using the version of vmlinuz without the numbers (so simply  "vmlinuz") at the end as well as various initrd.img files I found.
The error I get in grub is "error: invalid magic number."

I am thinking that the files such as initrd are broken so was thinking of following the instructions here:
linoxide.com/linux-how-to/fixing-broken-initrd-image-linux/
But I want to make sure that it is not going to break my computer.  

I would totally reformat/reinstall the ubuntu 7200HD with the USB but I have some impt files I can't seem to completely copy off the 7200HD.
When I use the usb I can see the files but I can't copy them because I don't have permissions.
I can't seem to figure out how to get permissions on my own drive!!!  (the usb doesn't have any but the 7200HD does which I know but can't seem to find where I can input it).  
It is very frustrating.  Please advise.  Thanks in advance.

---

### Post by slickymaster on 2021-01-27
Closed.

Duplicate [here]("https://ubuntuforums.org/showthread.php?t=2457137").

---

