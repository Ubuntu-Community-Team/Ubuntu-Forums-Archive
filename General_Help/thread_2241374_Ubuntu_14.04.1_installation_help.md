---
title: "Ubuntu 14.04.1 installation help"
date: 2014-08-25
forum: General Help
---

### Post by clabruno on 2014-08-25
Last night I had the bright idea of installing Ubuntu 14.04.1 on my computer using Unetbootin. I have never used Linux and I recently purchased a new PC so I figured it would be a good idea to install Linux on my old computer for learning purposes. I was very excited and couldn't start learning so I went on YouTube and found a tutorial on how to install Ubuntu. I went on to follow the directions and Ubuntu did boot up and it was gorgeous. Then the trouble began. I hit the button to install Ubuntu and began the process as specified in the tutorial. I had previously shrunk by drive before installing and I created the \ partition and made it 24gb, created the swap space and made it 2gb, and then put the remaining memory on the \home partition and hit install. It began installing and the a box came up with the word (Error!!!!) on the top and it. It said "error informing the kernel about modifications to partition / dev / sda2 ---- Device or resource busy. It then went back to the previous screen where you got to set up the portions and I noticed at the top of the box it said "Your installation medium is on /dev/sda2. you will not be able to create, delete, or resize partitions on this disk, but you may be able to install to existing partitions there."


I then spent hours trying to figure out a solution before it really late so I quit the installation and shut down so I can try again in the morning. Well, I woke up and turned on my computer and as it started to boot the blue screen comes up with the HP logo and the different option to get to boot up options, diagnostic tools, etc. and the  the computer goes to a black screen with a blinking cursor in the top left. So basically it seems like my entire hard disk has been wiped. I tried all kinds of different thing to no avail then decided to burn the ISO to a DVD and try booting to a DVD. So I go and burn the DVD and try to boot to the DVD and the computer won't boot to the DVD. I tried going to boot options and setting CD/DVD to boot as first priority and still no luck. Last think I did is use the diagnostic tool and everything checked out as being good until I saw the at the bottom where it tests Boot Path and it's says:


error code: BIOHD-3
warning: No bootable drives detected.




Any ideas or suggestions? I'm sure this will be fun.

---

### Post by TheFu on 2014-08-25
Please boot off a liveCD or flash drive and run the **boot-info** script - then post the created link back here for help. My signature has instructions.

---

### Post by grahammechanical on 2014-08-25
Please clarify. Were you doing this from a Ubuntu live session running from a USB memory stick or a DVD disk? I ask because of this

> [COLOR=#000000]"Your installation medium is on /dev/sda2. you will not be able to create, delete, or resize partitions on this disk, but you may be able to install to existing partitions there."[/COLOR]

The installation medium should not be on the hard disk we are installing Ubuntu to. Are you by any chance installing Ubuntu inside Windows using wubi.exe? Is there or perhaps I should say, was there another OS on that disk?

Run the Ubuntu live session and open the Disks utility.See, if that shows that Windows is still installed.

Regards

---

### Post by yancek on 2014-08-25
The tutorial below explains installing Ubuntu 14.04 in detail and also has a lot of other useful information.  Your first step now should be to go to the site suggested above and download the bootinfoscript using your Ubuntu installation medium, read the instructions and post the output here as it will show a lot of information on drives/partition and boot files.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by 3rdalbum on 2014-08-26
Unetbootin is only for making a bootable USB drive. It sounds like you have misunderstood its purpose, and told it to turn your internal hard disk into a USB flash drive.

Hence why your data is gone.

If you burn an Ubuntu DVD on your other computer using the "Burn ISO Image" function of your burning software, then tell your old computer's BIOS to look at the DVD drive as the highest boot priority, you should be able to boot the DVD and install Ubuntu from it.

However, any data you had on the disk before is gone. You did a backup before messing with the partitions, right?

---

