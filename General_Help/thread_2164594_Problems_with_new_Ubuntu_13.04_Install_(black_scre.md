---
title: "Problems with new Ubuntu 13.04 Install (black screen, no grub, no bios)"
date: 2013-08-01
forum: General Help
---

### Post by andres2 on 2013-08-01
Hello all, I had an Alienware M11x R2 laptop laying around with windows 7 installed that was running with no issues. Today I decided to experiment with it and give Ubuntu 13.04  a try. I'm fairly new to Linux and my plan was to use this machine as a tool to learn some more. I downloaded the 64 bit version of Ubuntu 13.04 and used Pen drive Linux to create a bootable USB drive. Then I restarted the laptop, went into the BIOS (pressing F2) and change boot sequence to start with USB. Once restarted it went through the Ubuntu install process with no issues, I chose to erase Win 7 with ubuntu as well as encrypted HD option, then setup username and password. After all install process was completed I restarted the laptop and was stuck with a black screen.

Now, here is where my dilemma starts, I knew there were some issues with nvidia cards but saw that most were easily troubleshooted as long as you have access to grub. My first issue was realizing that I couldn't get grub access by pressing shift, then I tried accessing the BIOS to see if maybe I had to switch around boot sequence again, but to my surprise not a single key is letting me access the BIOS either. 

I was reading the comprehensive guide posted here [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) which gives the option to running some commands from a Live CD, my problem being the lack of CD drive on the laptop and my bootable USB stick not working when connected.

So seems like my BIOS somehow got affected by installing ubuntu, im just wondering how is that even possible, has anybody encountered this issue before? any hopes other than a BIOS recovery? Thanks a lot for any help

---

### Post by dino99 on 2013-08-01
ubuntu installation CANT trouble the bios. Check the Alienware bios doc, and reset it to default if needed. Then with a single installed OS, the grub menu can only be seen by holding down "shift" at the bios end process.

---

### Post by andres2 on 2013-08-01
yeah i was wrong about the BIOS part, i got the computer to boot up once i took the hard drive out. Now to figure out how to salvage this hard drive...

---

### Post by dino99 on 2013-08-01
note that each device (hdd/sdd/usb/...) get a new uuid everytime it is plugged; so doing the grub confused (as it only knows the uuid registered with the latest "update-grub" process).

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by andres2 on 2013-08-01
> **9d9 said:**
> note that each device (hdd/sdd/usb/...) get a new uuid everytime it is plugged; so doing the grub confused (as it only knows the uuid registered with the latest "update-grub" process).

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

thanks a lot! after had to recover the hard-drive on another laptop and do a proper format with no os installed and was able to successfully install ubuntu this time :)

---

