---
title: "Installing Ubuntu from USB"
date: 2017-04-30
forum: General Help
---

### Post by nisemono on 2017-04-30
Hello everyone!
I need help with installing Ubuntu. The thing is, I haven't used Ubuntu for a couple of years, because it was just more convenient at work to use windows.
Now I bought a used Fujitsu Siemens Amilo M1437 laptop running on Windows XP (for lack of money) and I've got a few problems installing up-to-date software and printer drivers etc. So I thought I might give Ubuntu a try again.
The laptop doesn't have a cd burner, so I made a bootable usb stick using rufus and the guide on ubuntu.com. The problem is that I can't boot from USB at all. When I enter the bootmenu, it only offers me CD or harddrive. So I checked the Bios, but "Removable device" is number one in the boot order.
Maybe I need to configure the USB-stick in a different way for such an old laptop, but I don't know how. I tried Ubuntu 17.04 and this: [https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
I'd appreciate any help.

---

### Post by dragonfly41 on 2017-04-30
Gleaned some info on your Amilo M 1437G by reading here ...
[http://www.insanelymac.com/forum/topic/12927-fujitsu-siemens-owners-read-this-the-x43xg-issue/](http://www.insanelymac.com/forum/topic/12927-fujitsu-siemens-owners-read-this-the-x43xg-issue/)
> The 1437G has no possibility to boot from USB-Harddrive, too (Mine could not directly, maybe other drives are more compatible). 
I don't know if is this is true. Perhaps check the appropriate Fn button to bring up BIOS Setup and look at boot order. Is USB in that list?
But on this old laptop I would try installing a lighter weight Ubuntu which boots from CD instead of USB.
[http://www.debianadmin.com/list-of-ubuntu-based-linux-distributions-and-live-cds-2.htmlhttp://lubuntu.net/](http://www.debianadmin.com/list-of-ubuntu-based-linux-distributions-and-live-cds-2.htmlhttp://lubuntu.net/)

And refer to the sticky thread “Old hardware brought to life” ...

[https://ubuntuforums.org/showthread.php?t=2130640](https://ubuntuforums.org/showthread.php?t=2130640)

[Later edit]

Reading your post again I see that you don't have a CD burner.

---

### Post by Impavidus on 2017-04-30
Many old computers don't boot from usb. The easy solution would be to use a different computer to burn the .iso to a dvd and boot from that. If there's no dvd player, you can also use a minimal install, which is a bit harder.

As this is a WinXP-era laptop, I expect it will be underpowered for Ubuntu. It may be better to use a lighter flavour of Ubuntu, like Lubuntu. Also, 17.04 only has 9 months of support. You're not going to run anything state-of-the-art on that computer, so you may prefer 16.04 LTS (=long term support), which has 3 years of support for the lighter flavours, until april 2019. The next LTS release will be released in april 2018.

---

### Post by dragonfly41 on 2017-04-30
One further idea to explore.
Remove the laptop internal drive and place it in a USB container.
After backing up any files you need, format the drive and create ext4 partitions.
Use another PC to install Lubuntu into that drive.
Reinstall bootable drive (containing Lubuntu) in your laptop.

---

### Post by oldrocker99 on 2017-04-30
I had an old laptop which wouldn't boot from USB, until I realized it was a 32-bit machine and installed the 32-bit version of 14.04. Yes, I know about dwindling 32-bit support, but it was the only way to get that old laptop running, and the OP should try it.

---

### Post by oldfred on 2017-04-30
My old systems saw flash drive as another entry in hard drive boot choices. Check that.

---

### Post by mörgæs on 2017-05-01
> **oldrocker99 said:**
> I had an old laptop which wouldn't boot from USB, until I realized it was a 32-bit machine and installed the 32-bit version of 14.04. Yes, I know about dwindling 32-bit support, but it was the only way to get that old laptop running, and the OP should try it.

The dwindling support is only a rumour. Chrome is the only application I know of which is not offered any more for 32 bit (Chromium is still there), everything else carries on as always.


32 bit hardware is still produced, by the way.

---

### Post by nisemono on 2017-05-01
Thank you very much for the answers. I'm trying to find a way to burn a CD with a lighter version. The problem is that I recently moved, so I don't know people here, and my old laptop broke so I can't burn DVDs or CDs. I'll maybe try to find a shop that can burn a DVD or CD with Ubuntu for me.
So, which version of Ubuntu or Lubuntu do you recommend?
I don't know enough about computers to be able to remove the internal drive... I'd probably just break it.Maybe I'll try and fool around with it when I've got the money to buy a new computer.

---

### Post by Impavidus on 2017-05-01
Without knowing more about the hardware than that it's a Windows XP-era laptop, I suggest 32 bit Lubuntu 16.04.2 LTS. But to give meaningful advice, we need more details, in particular CPU, memory (RAM that is) and graphics.

---

### Post by mörgæs on 2017-05-02
> **nisemono said:**
> I'll maybe try to find a shop that can burn a DVD or CD with Ubuntu for me.

You could also buy a Lubuntu installation DVD by mail order. They are cheap. 

> **nisemono said:**
> my old laptop broke
What was wrong with it? Hard- or software errors?

---

### Post by russkyca on 2017-05-02
> **nisemono said:**
> Hello everyone!
I need help with installing Ubuntu. The thing is, I haven't used Ubuntu for a couple of years, because it was just more convenient at work to use windows.
Now I bought a used Fujitsu Siemens Amilo M1437 laptop running on Windows XP (for lack of money) and I've got a few problems installing up-to-date software and printer drivers etc. So I thought I might give Ubuntu a try again.
The laptop doesn't have a cd burner, so I made a bootable usb stick using rufus and the guide on ubuntu.com. The problem is that I can't boot from USB at all. When I enter the bootmenu, it only offers me CD or harddrive. So I checked the Bios, but "Removable device" is number one in the boot order.
Maybe I need to configure the USB-stick in a different way for such an old laptop, but I don't know how. I tried Ubuntu 17.04 and this: [https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
I'd appreciate any help.Isn't there a function key that allows a selection of other bootable devices?   I press F8.   This would be done with the BIOS screen as your computer is booting up....before you get to the OS screen part.... it is very quick so you have to notice it right away....

---

### Post by nisemono on 2017-05-03
> **mörgæs said:**
> You could also buy a Lubuntu installation DVD by mail order. They are cheap. 


What was wrong with it? Hard- or software errors?

My old netbook has a broken screen (completely cracked, doesn't work anymore) and since it was a very cheap one, there are no spare parts sold by the manufacturer or ways to repair it. I'll buy a good new one as soon as I have the money...
Now, I saw a Linux magazine in a bookstore and bought it, it's got a DVD with Ubuntu, Ubuntu Mate, Mint, Q4os and SUSE. In the magazine it says that Q4os is good for old hardware, so I thought I'd give that a try.
Q4os runs good from DVD and I wanted to try installing it and see how it goes. There's gparted on the DVD and I tried partitioning the hard drive so I can keep Windows just in case. The thing is when I finished, it said that the partion needs to have the mountpoint "/". I couldn't figure out how to set the mountpoint. I downloaded the Minitool Partition wizard for windows, but again I couldn't set the mountpoint to / and so I couldn't install Q4os on the new partition. Any ideas on that?


To answer the other questions, 
processor:  x86 Family 6 Model 13 Stepping 8 GenuineIntel ~800 Mhz
2GB RAM
I don't know how to find infos about the graphic, I've just looked through a lot of settings and couldn't find it.

Thanks for the help :)

---

### Post by mörgæs on 2017-05-05
> **nisemono said:**
> I'll buy a good new one as soon as I have the money...

You don't necessarily have to. The present one is of the latter Pentium M breed which is both low power and fairly strong. I use some of them myself.


> **nisemono said:**
> The thing is when I finished, it said that the partion needs to have the mountpoint "/". 

If you can run Gparted from a live boot you can set the mountpoint. 

Still I recommend to erase the hard disk to get rid of XP. After being out of support for so long time you can be almost sure that something bad is nesting there.

---

### Post by nisemono on 2017-05-06
I somehow couldn't figure out how to set the mountpoint. But ok, I'll erase it. It's pretty slow anyway and can't run newer programs or connect to my printer.
I'll hopefully be back when and if I've made Linux work :)

---

