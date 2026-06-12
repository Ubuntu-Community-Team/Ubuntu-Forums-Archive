---
title: "live usb fail"
date: 2014-04-03
forum: General Help
---

### Post by andrew123ast on 2014-04-03
Hello, I have an hp Compaq 6730s running ubuntu 12.04 lts and windows xp. When I first installed ubuntu I used my USB. Then I decided to re download windows and just dual boot so I could still mod my Xbox games. I've done this multiple times, but now, my computer won't boot from the live cd to run boot repair. Everything that I have tried includes live cd, live USB, and frugal installs. They all just say Try HDD(0,0): EXT 4: then it won't let me type or anything. Any help is appreciated.

---

### Post by sudodus on 2014-04-03
Did you check the md5sum of the downloaded iso file? See this link

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

See the tips how to boot from a USB pendrive in the following link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

---

### Post by andrew123ast on 2014-04-03
Thanks for the reply, but I've tried checking the md5sum of the download. I've re downloaded it about 10 times. Nothing. And like I've said before, I've done this multiple times.

---

### Post by sudodus on 2014-04-03
If you have failed to get the correct md5sum 10 times, I suggest that you try a ***torrent***, because it checks for the md5sum automatically and the final iso file should be correct.

When the md5sum is correct, you can focus on the next step, to create a correct USB boot drive. You may want to try it in another computer. Which tool do you use to create theUSB boot drive? ***Unetbootin*** is a good tool, that works in most cases, and from Windows as well as from linux.

Then it is time to make your computer boot from the USB boot drive ...

---

### Post by andrew123ast on 2014-04-03
I've tried it on my win 7 desktop and my win xp laptop, both had correct nd5sums after about 6 downloads. Then I tried to boot it, when I plugged it into my laptop, the bios detected it right away. So I clicked it, USB HDD. Then it said Try HDD0,0 ext4

---

### Post by sudodus on 2014-04-03
You cannot simply copy the iso file to a USB drive. You need to install it with a special program, for exampel ***Unetbootin***. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

---

### Post by andrew123ast on 2014-04-03
Yes I know, I have tried lili, and unetbootin. They have the same results, try HDD(0,0) EXT4:

---

### Post by XBNCPRk on 2014-04-03
Am I correct in assuming the following?

You downloaded ubuntu, used wubi and wiped winxp to install ubuntu?
You created an ntfs partition, redowloaded and reinstalled windows xp to it?
Wubi is throwing an error when you try to use a usb live version of ubuntu to repair the boot loader? (Pretty sure thats what the Try HDD (0,0) error is btw)

Please remember these are people trying to help, and if you give explicit information of what you have done and tried already, it helps us all move the process along faster.

---

### Post by andrew123ast on 2014-04-03
Pretty much it, except after a few failed attempts of trying wubi, I just went with the live USB approach. It's when I click on the unetbootin option in my bios that it says the HDD thing. Then I can't type anything, my keyboard just beeps. But if I click the win xp instead of the unetbootin option, it boots windows just fine. I have no idea what is going on since its booted from USB just fine before, since when I first installed this, wubi didnt work, so I used the live USB, but now it wont work.

---

### Post by XBNCPRk on 2014-04-03
Sounds like the problem is that you have the windows bootloader and grub both not wanting to play nice together. Perhaps give [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)  a try.

---

### Post by andrew123ast on 2014-04-03
I read most of the article and its pretty much all stuff I've tried. Let me explain my exact problem. When I start my computer it says to click on either unetbootin, which is ubuntu, or windows xp. When I click on xp, it boots xp just fine, but when I click on unetbootin, it goes black for about 1 second, then it pops up try HDD(0,0): EXT 4: then I can't do anything at all except restart the computer. I've tried re downloading, I've tried wubi, I've tried lili, and unetbootin. I've tried a frugal install, they all yeild the same result. Did my bios change suddenly since last time I tried this? If I delete windows xp partition with magic partition 8, it just says no bootable media. So I have no idea how to get grub back.

---

### Post by sudodus on 2014-04-04
Let's try again!

What working operating system have you got? I mean in any computer, where you can communicate with us via the internet, where you can download iso files, and where you can create a USB boot drive?

- Windows, Ubuntu? Is it the Windows 7 computer you mentioned in post #5?

- Is that computer booting with old style BIOS or UEFI?

-o-

Many people have good experiences from creating USB boot drives with Unetbootin from Windows. But if neither your XP nor your Win7 computer boots from the USB boot drive, I suspect it is bad. Something is bad.

Some pendrives do not work as boot drives. So the pendrive itself might be the problem. Some pendrives work with some computers but not with other computers. There might be problems because of the USB system or BIOS/UEFI of the computer.

In some particular cases it is better to use another tool (other than Unetbootin) to create the USB boot drive.

Finally, in some cases the computer is unwilling to boot from USB, but it will boot from CD or DVD. The standard Ubuntu desktop iso file is oversized and does not fit in a CD disk, but it will boot from a DVD disk, if you have a DVD drive.

Read about different alternatives and tips (including the links) at this web page

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by sudodus on 2014-04-04
There might be problems to boot your HP laptop from USB due to some special feature of the computer. See the discussion about that in the following link

[http://ubuntuforums.org/showthread.php?t=2196858&p=12907221#post12907221](http://ubuntuforums.org/showthread.php?t=2196858&p=12907221#post12907221)

---

### Post by andrew123ast on 2014-04-04
As of right now, I have access to my android ics phone, my win xp laptop, can't get to ubuntu, my win 7 desktop, and I have my friends win 7 laptop. I know ny USB is bootable and my bios does detect it. But the error stops me everytime, atleast I think its an error.

---

### Post by andrew123ast on 2014-04-04
> **andrew123ast said:**
> As of right now, I have access to my android ics phone, my win xp laptop, can't get to ubuntu, my win 7 desktop, and I have my friends win 7 laptop. I know ny USB is bootable and my bios does detect it. But the error stops me everytime, atleast I think its an error.
And I have uefi turned off on both computers bios.

---

### Post by sudodus on 2014-04-04
Can you try with another pendrive and make a boot drive with Unetbootin. Test it in more than one computer.

---

### Post by andrew123ast on 2014-04-05
I've tested 3 USB flash drives on three different computers, the only one that booted on the other two computers was the one I'm using, and its what I used to install this in the first place, so it works on this as well.

---

### Post by andrew123ast on 2014-04-05
If its possible to post video on here I made a video of my laptop

---

### Post by sudodus on 2014-04-05
You can make a ***youtube*** video and link to it.

-o-

It is good to know that your original pendrive can boot other computers :-) Then we know the problem is somewhere else.

There could be a problem that some driver of the version of Ubuntu you are testing does not work with 'its' hardware in your computer. If that is the case, you might have better luck with another version of Ubuntu or with some other linux distro. ***Knoppix*** is known for good hardware support, so you might download and try it. If it works, but you want a regular installed linux system, you have more hope to find something that will be good.

---

### Post by andrew123ast on 2014-04-05
All right, ill link them later, but the version should work right, I mean it is installed already, oh and I figured out that hd0 is my ubuntu partition hd1 is my xp and hd2 is my linux swap

---

### Post by sudodus on 2014-04-05
I don't understand. What is working or should be working?

- Can you boot from a USB drive and run live ('try' Ubuntu without installing)?
- Can you boot the installed system but only to see the computer say 'Try HDD0,0 ext4' 				
- How do you boot, when you get that errror message?

---

