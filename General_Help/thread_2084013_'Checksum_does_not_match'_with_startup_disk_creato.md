---
title: "'Checksum does not match' with startup disk creator"
date: 2012-11-14
forum: General Help
---

### Post by zcacogp on 2012-11-14
Hello, 

I'm trying to make a startup USB stick to install 12.10 (gnome-remix) on my machines, but can't make it work. The situation is that I have two computers (AMD64-bit desktop and Intel 32-bit laptop), both running 12.04. I also have two USB memory sticks (2Gb and 16Gb). I have downloaded the ISO's for both 32-bit and 64-bit Ubuntu 12.10, and have tried making bootable USB sticks with startup disk creator. However, although I have tried each combination of USB stick, computer and ISO, I always get the error "Checksum does not match, try again?" I've removed usb-creator-gtk and re-installed it and that made no difference. Running usb-creator-gtk from the terminal produces no errors until the checksum error window pops up. I have tried formatting the USB sticks as FAT-16 bit and FAT-32bit, and tried formatting the larger stick down to 2Gb. Some internet posts suggest that problems can occur when you format the USB stick to have a persistant file but I have tried setting it such that there is no such a file and it makes no difference either. 

The checksum for the files I have is the same as that posted on the Ubuntu website. 

I have also tried using Unetbootin on the desktop machine and, while that appears to work, booting from the USB stick produces a list of errors and the installation halts. 

If anyone has any suggestions then I'd love to hear them. I have tried every possible combination and have met with no success. 

Sorry this post is so negative in tone. I've spent a lot of time on this and am stuck for more options! 

All help welcomed - thanks! 


Oli.

---

### Post by zcacogp on 2012-11-15
OK, there has been some progress with this. 

Creating install USB's from Startup Disk Creator has failed every time I have tried it. I don't know why, but each time I am told that the checksums don't match. 

I did however manage to create a bootable USB from unetbootin - I re-ran the program and tried again, and it procued a USB that I can boot from. I have installed 12.10 on my laptop with this (and it works very well - I am really enjoying it.) 

However I am still in the same hole with the desktop machine. I have two USB sticks, one 2Gb one 16Gb, and can use unetbootin on the (newly-built 12.10) laptop to make bootable USB's out of them, but they won't work in the desktop. The 2Gb stick always hangs on start-up at "Verifying DMI Pool Data", the 16Gb one appears to run but always produces errors once I have chosen an option from the unetbootin menu. 

If anyone has any suggestions I would be really grateful to hear them - thank you. 


Oli.

---

### Post by zcacogp on 2012-11-18
Update on this; I still haven't understood why I was struggling with the USB boot drives; one USB wouldn't be recognised in my desktop machine by the BIOS, the other one always caused a crash when installing Ubuntu. However I did try installing 12.10 from one partition to another, using these instructions: 

[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

... and it now works perfectly! It's a slightly fiddly process, but not that difficult, and I'm very pleased the desktop machine is now as it should be. 

Hopefully this thread will be of use to someone else who has had difficulty with installing from USB sticks. 


Oli.

---

