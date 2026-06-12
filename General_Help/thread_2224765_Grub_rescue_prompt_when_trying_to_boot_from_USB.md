---
title: "Grub rescue prompt when trying to boot from USB"
date: 2014-05-18
forum: General Help
---

### Post by James_Scheminant on 2014-05-18
So the title has to say it all. I am new to linux and to Ubuntu and I have obviously screwed something up on my Netbook. So i have an HP A1N60AV Model dm1z-4100 and i tried to put Ubuntu on it from a Thumbdrive. For some reason It will not boot from the USB and it goes to the Grub rescue command and nothing works. Everything i've tried says "unknown Command" or something of that nature. I've read a lot of the same people having the same issue. Can someone help me out? If you need more  details please let me know and I will add more details as requested.

---

### Post by James_Scheminant on 2014-05-18
This is the type [http://h10025.www1.hp.com/ewfrf/wc/product?product=5213603&lc=en&cc=us&dlc=en&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/product?product=5213603&lc=en&cc=us&dlc=en&lang=en&cc=us)

---

### Post by coffeecat on 2014-05-18
> **James_Scheminant said:**
> So i have an HP A1N60AV Model dm1z-4100 and i tried to put Ubuntu on it from a Thumbdrive. For some reason It will not boot from the USB and it goes to the Grub rescue command and nothing works.

Welcome to the forum!

You will need to provide a few more details if people are going to be able to help. I'll ask a few questions to clarify a few points from the above to try to get things moving. Once you've answered them, I'll change your thread title to something more descriptive which will help to attract those able to help you.

It sounds as though you are saying that you were able to boot from the USB drive and that now you can't. Also, the fact that you are getting the grub prompt suggests that you did install Ubuntu to the hard drive of the HP machine. So...

[list=1][*]Briefly describe how you prepared the thumbdrive. What application did you use?
[*]When you first tried to put Ubuntu on the HP machine, describe briefly what you did. Did you get as far as the Ubuntu installer?
[*]You say it will not (now?) boot from the USB. With some HP machines you can tap one of the function keys during the POST screen to get a menu to choose which bootable device you boot from. What are you doing to get the machine to boot from the USB device?
[*]Do you get the grub rescue command when you try to boot without the USB thumbdrive attached?[/list]

---

### Post by James_Scheminant on 2014-05-18
1. I have tried LinuxLive, Universal USB installer 1.9.5.2, Unetbootin, And also the live version. 
2. So it was a Quad boot Partition. (Windows 7, Vista, and 2 version of backtrack linux.) I put the thumbdrive in and followed the prompts from the installer. I clicked on Demo and Full install and then to Help me to boot from CD. It went through a process that i thought was installing a boot loader of some sort and then said "Restart now or Manual restart later". So i clicked restart now. After it restarted it went to the grub rescue command line and then i got totally lost. I looked up numerous forums where people were talking about the same issue but nothing helped. Sudo isn't recognized and apt-get of course wont work. So i restarted using CTRL+ALT+DELETE and went to the bios screen to turn on BOOT FROM USB, but the only things listed are USB Diskette on Key/Usb hard Disk, USB CD/DVD ROM Drive, USB Floppy, Network Adapter and Notebook Hard Drive. I have tried everything at this point and nothing will boot from the USB thumbdrive for some reason and i have no idea why.
3. Yes i've tried that the only thing listed it Notebook Hard Drive.
4. And yes i get it with or without the thumbdrive.

---

### Post by coffeecat on 2014-05-18
Backtrack may be based on Ubuntu, but it is very different and few people will have experience of it here, so I have moved this thread to Other OS/Distro Support. It has also been unmaintained for a long time now, so you are probably wasting your time trying to get it to work at all.

I suggest you look for a maintained distro to try. The main support areas of this forum are for the official flavours of Ubuntu only. In the meantime, if you want to repair the Windows bootloader on your hard drive so that you can at least boot into W7 and Vista, you might find this useful:

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by James_Scheminant on 2014-05-18
Actually that isn't at all what i said. I said it "WAS" i was loading a new version of Ubuntu on it, not Backtrack. I HAD backtrack on it.. I dont know where you got that it was backtrack i was loading.

---

### Post by coffeecat on 2014-05-18
Oh I see. You would not believe the number of people who say they are running Ubuntu when they are in fact running Backtrack. When you mentioned Backtrack in your previous post I thought your "Ubuntu" in the OP was a similar mislabelling. I've moved this to General Help and prefixed it Ubuntu.

---

### Post by James_Scheminant on 2014-05-18
Thanks so much Coffee! Hope someone sees it and knows how to fix it. I am about to try the RUFUS approach now.

---

### Post by James_Scheminant on 2014-05-18
Thought i fixed it but im not sure yet, Using Rufus to try and install Ubuntu... Cross your fingers!

---

