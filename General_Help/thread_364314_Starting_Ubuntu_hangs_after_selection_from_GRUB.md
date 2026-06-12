---
title: "Starting Ubuntu hangs after selection from GRUB"
date: 2007-02-18
forum: General Help
---

### Post by topgan1 on 2007-02-18
Hi folks,
I have been using Ubuntu for some years now but its the first time I'm encountering a big problem like the following.

I Installed Ubuntu 6.10 for some time now and I have problem booting it. After I select it from GRUB I get a blank screen with the blinking cursor and some times it also displays  "Starting Ubuntu..." and it just hangs there with the blinking cursor. I have waited for more than 15 minutes and I also have not noticed hard disk drive activity. The Caps/scroll/num lock works if that makes any difference.

The weird thing is that I was getting this problem for some weeks now but I was resetting my pc and retrying to boot Ubuntu. After 1-2-3 tries eventually it was booting without stucking on the "Starting Ubuntu" message and without any other problems. The last day though, this "work-around" didn't work and from then I cannot boot ubuntu at all. 

I don't think the problem has to do anything with my multimedia interfaces (sound card and/or video card) cause I can't explain why I get them working on windows and some times I had no problem booting with ubuntu too. I don't even get the Ubuntu splash screen. Also I don't think its a grub problem for the same reason. I was not having problem booting with it some times. One thought it came to my mind was that the /etc/fstab maybe had an error or something, I double checked it and even tried to replace the UUIDs with the /dev/sdXX settings, but as far as I know, correct me if im wrong, the root file system doesn't get mounted so fast (at the Starting Ubuntu... blank screen), maybe after 2-3 seconds (at the splash screen). I also tried reversing the hard disk sequence at the BIOS but didn't work. The Live CD boots fine and smoothly also. 

I forgot to mention that the recovery mode encounters the same problem, it stucks at Starting Ubuntu... 

I really can't understand this problem as it doesn't give me any error message so I can search around it.

I don't experience any other problems than that at my system. Windows XP boots and works fine without any problems. My pc specifications are : 
Pentium 4 (3.00 GHz) Hyperthreading enabled, 
1024 MB Dual DDR Ram, 
1 SATA 160GB (3 partitions, windows base system, and two other ntfs parts)
1 PATA 120GB (3 partitions, linux root, linux swap, ntfs partition) both are working fine
DVD-RW/floppy drive
Creative Sound Blaster Live
NVIDIA Geforce 6600

The installation was from the 6.10-desktop live cd and I had no problems installing it.
Also I can't afford reinstalling the whole thing atm cause I had many programs installed from synaptic and other from source, also I was using xgl/beryl without any problems and I don't feel like to setup it again from the scratch :)

If you want me to post any configuration files please tell me, I'm on windows atm and can't see them. I will boot with the Live CD or try to mount the linux partition from windows if you need any information from my linux system.

Thank you for reading my post, I hope someone can help me.

---

### Post by Rui Pais on 2007-02-18
Hi,
your problem seems to be kernel related, not necessarily ubuntu related.

Try this. At grub menu select Ubuntu entry and press the key 'E' on keyboard. 
(If you set passwords on grub, first press 'P' and give the password)

That will allow you edit the entry. 

Ensure that you have a line with a initrd.img and with same number as kernel number.
After that, remove the word 'quiet' from the kernel line (key 'E' again to edit).
And finally delete the line that contains only the word 'quiet' (key 'D' to delete a line).
(Note that those changes will not be permanent, only for the boot).

You will be then in fully verbose mode.

Press 'B' and check when it stop, what it was doing and check if there are any failure messages...

Post here.

Alternatively you can start from liveCD, mount your Ubuntu partition and check /var/log/messages and /lar/log/kern.log. But that could be more complicated (logs are usually huge and hard to read)

Good luck.

---

### Post by topgan1 on 2007-02-18
I did what you said and i got no messages at all, even by removing the quiet flag when I booted I got stucked on the same message. As it seems it doesnt get to the kernel loading process at all. 

And from the logs as far as I can observe these are from the last time I booted my system succesfully.

My kern.log here: [http://www.divshare.com/download/137503-c00](http://www.divshare.com/download/137503-c00)
and my messages file here: [http://www.divshare.com/download/137507-f18](http://www.divshare.com/download/137507-f18)

Now that I'm thinking about it I will try playing with my ACPI bios settings or with any shadow memory options there and see what I get.

Any other ideas?

---

### Post by topgan1 on 2007-02-18
I had tried changing ACPI settings on my BIOS but I got no progress. Maybe I should try to install LILO instead of GRUB?

---

### Post by Rui Pais on 2007-02-19
> **topgan1 said:**
> I had tried changing ACPI settings on my BIOS but I got no progress. Maybe I should try to install LILO instead of GRUB?

hi topgan1,

Uhmmm... since you can boot till the grub menu, select and launch a kernel, it isn't a Grub problem.

Your config files are in fact from a succefully booted session and don't have, at least that i could see, no problem.

Without seeing any message errors or logs it's very difficult to track the issue :(

But since it happens only sometimes and on occasions you can boot normally sounds like an hardware failure. 

 Some suggestions:

.Try to rum memtest from grub menu for a large period of time.
.If you have more then one ram stick try to to remove them and boot with only one. Experiment with them and see if some work correctly or some work bad.

.Do, from a liveCD, an e2fsck -f on all partition on your drives, specially the one with the linux root / and the  /boot.

.Try to boot with different vga settings to check if you can see some output from kernel. Add vga=773 (or 769/771/775) to the kernel line.

If all that gives no solutions or trace of the problem... maybe trying to chroot to your Ubuntu and reinstall or update the kernel and see it if work with a fresh or another kernel (if you don't know how to do it post that i explain it, try first check partitions and mem)

Good luck

---

### Post by topgan1 on 2007-02-19
> **Rui Pais said:**
> hi topgan1,
Without seeing any message errors or logs it's very difficult to track the issue :(

But since it happens only sometimes and on occasions you can boot normally sounds like an hardware failure. 


The hardware failure is one of the things I'm currently thinking. But since I have no other similar cpu/motherboard/vga card available to test I hope that if something failed that is the memory so I can figure it out with some trial and error.

I'll run full memtest at the night to see if I have any problem with my RAMs. I will try to boot with each one sticks alone anyway.

> 
.Do, from a liveCD, an e2fsck -f on all partition on your drives, specially the one with the linux root / and the  /boot.

.Try to boot with different vga settings to check if you can see some output from kernel. Add vga=773 (or 769/771/775) to the kernel line.


going to check that immediately...

> 
If all that gives no solutions or trace of the problem... maybe trying to chroot to your Ubuntu and reinstall or update the kernel and see it if work with a fresh or another kernel (if you don't know how to do it post that i explain it, try first check partitions and mem)

I have two different kernel options on my grub. I don't think its the kernel. Both versions don't work and they used to work before without any changes.

I think the problem has to be from the hardware. I can't think of anything else. But if that is the case I just can't understand why windows work fine. Only Linux Boot Up process trigger my faulty hardware???

Anyway, thank you for your help. I'll keep reporting my progress, in case someone has the same or similar problem.

---

### Post by fcumok on 2007-02-19
I had this with a computer. If i ran any other version of linux it worked fine. I found if I changed the USB Keyboard for a PS2 one then the system worked fine.

---

### Post by neocoretech on 2007-07-18
I had the same problem... it was also usb related. When I started with a usb-disk plugged in, it hang also bevor any kernelmessage. But when it's powered off it starts without. Here also: windows boots without problems *shame* must be changed... any hints welcome... :)

---

### Post by Ralphie on 2007-12-14
I was having an issue with this as well, with the new system that i bought. it never did it with my older system.
my new specs:

MB:   Asus P5k-e
VID:   Asus EN7600GS Silent (Nvidia)
MEM: Corsair XMS2 2x2GB DDR2-800
CPU:  Intel Core 2 Quad 2.4GHz

It seems as if my system does not like USB cables that are plugged in, but go to a device that is off. such as external HDD, and a scanner that i only turn on when i am going to use it.

I have restarted a few times now with these things unplugged and it has not hung up yet.
if it does i will report back.

I'm just glad none of my hardware was faulty, it was hard enough putting it all together the first time :lolflag:

---

