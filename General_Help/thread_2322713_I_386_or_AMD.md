---
title: "I 386 or AMD"
date: 2016-04-30
forum: General Help
---

### Post by Hitesh_Dhamecha on 2016-04-30
Hi, 

I am new to linux. First time installing any OS other than Windows.

I am using AMD athlon 64 X2 Duel core processor, 2.4 GHz with Gigabyte GA-MA69VM S2 motherboard. Which installation package should I use i386 or AMD?

Currently I am using Windows 10 32bit version. I have downloaded Ubuntu 16.04 desktop i386 package and tried to install but computer not booting from USB at all, I did much googling in this forum for that and used various bootable USB maker too. 

Please guide me for the correct version and procedures.

---

### Post by DuckHook on 2016-04-30
Though old, your CPU is capable of 64-bit processing, so there is no reason to stay with 32-bit. There are many tricks, workarounds and caveats to old hardware. Please see link in my signature: ***Resurrecting Old Hardware***. As for booting from USB, you really should make sure you can run Ubuntu as a LiveUSB first. Creating LiveUSB instructions are [here]("https://help.ubuntu.com/community/Installation/FromUSBStick"). Given the age of your CPU and without further data like GPU and RAM, I would recommend one of the lighter flavours: Lubuntu, Xubuntu or Ubuntu-Mate.

---

### Post by Impavidus on 2016-04-30
You didn't mention how much RAM your computer has. If it's more than 3 GB, definitely use 64 bit, as that will allow your programs to use all that memory. (There is a feature, called PAE, that allows the OS to use more memory, but each application is still limited to 4 GB.) However, a 64 bit system uses slightly more memory for the same task than a 32 bit system, so if you're tight on memory (no more than 1 GB), I'd consider 32 bit. Inbetween, it doesn't matter too much.

Some old computers don't boot from USB. Is USB mentioned in the BIOS boot options? Else, use a DVD instead.

---

### Post by grahammechanical on 2016-04-30
A 32 bit operating system will run on both 32 bit and 64 bit CPUs. But a 64 bit operating system will only run on a 64 bit CPU.

The minimum requirement for 64 bit Windows 10 is 2 GB RAM. Whereas, the minimum requirement for 32 bit Windows 10 is 1 GB RAM

64 bit Ubuntu will run fine on 1 GB of RAM provided the video adapter has 512 MB or 1 GB of its own video memory and it can do hardware accelerated 3D rendering. If the video adapter (GPU) cannot do hardware accelerated 3D rendering then the CPU & system RAM have to take up the load. And that slows things down.

When I say that 64 bit Ubuntu will run fine on 1 GB of RAM I am speaking of my own experience using a video adapter with 1 GB of video memory. Things slow down when having several applications open that use a lot of memory. Ubuntu is very good about freeing up memory for use when it is needed. 

Flavours of Ubuntu such as Xubuntu, Lubuntu and Ubuntu Mate that use a different window compositor to the one used in Ubuntu (Compiz) have a bit more of video memory available for re-drawing the screen. And that can make a difference to a user's perception of how fast the operating system is working.

Regards

---

### Post by kurt18947 on 2016-04-30
I have quite a similar machine, AMD Athlon II X2 2.8 ghz processor on Gigabyte 785 motherboard. It has a fussy BIOS boot function. It will only boot Live USB IF the flash drive is formatted with Windows. Format with Gparted and I get a "no OS found" or similar message. No problem with DVD. The live USB flash drives formatted with gparted boot fine on other machines so I'm pretty sure it's an issue with this motherboard/BIOS. 

It has an Award Modular BIOS 6.0 if I remember correctly. I researched the issue and read that the BIOS boot code was written by Microsoft so it wouldn't really be a surprise that there's an issue with anything non-Microsoft.

---

### Post by Benjamin_Goldstone on 2016-04-30
I would use 32bit for older pc due to lower component usage.  welcome to Ubuntu and Stability:grin:

---

### Post by DuckHook on 2016-05-01
> **Benjamin_Goldstone said:**
> I would use 32bit for older pc due to lower component usage.  welcome to Ubuntu and Stability:grin:I respectfully disagree. OP's CPU is quite capable of 64 bit OS. The extra memory required to run 64-bit is not excessive unless the OP is highly RAM-constrained. For the breakpoints, see Grahammechanical's very complete post above. If OP is either RAM or Video constrained, a better strategy is to move to a lighter flavour. This will have much greater positive impact than staying with 32-bit.

The biggest reason to move to 64 bit is that Ubuntu is increasingly reluctant to support 32 bit. They floated the idea of retiring 32-bit support for Ubuntu earlier this year (see [here]("http://www.phoronix.com/scan.php?page=news_item&px=2016-Ubuntu-32-bit-Desktop-ISO")) until the Old-HW community raised a ruckus. They aren't the only ones (see [this]("http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued")). Many vendors are moving away from or devoting less resources to 32-bit, which just means that fixes will be fewer, of lower quality, and less security-stringent. While support still exists for now, it is IMO better to move to 64 bit now when one still has the time to work out issues instead of when forced to for lack of choice.

I tinker with a lot of old HW. In my opinion, for *typical desktop* use, 32-bit OSes should be used only for 32-bit machines. Atypical needs, of course, dictate different strategies.

---

### Post by Hitesh_Dhamecha on 2016-05-02
Hi,

Thanks for reply.

I did a little bit odd thing to get the solution, I updated the BIOS software from f6 to f10. Though it was risky(as said by motherboard manufacturer). But it worked flawlessly, just ten minutes to get and update the BIOS, more five minutes to make bootable USB and boom.. It's done!!

Hope it will help to others with same hardware configuration.

---

### Post by DuckHook on 2016-05-02
Congratulations on working out your problem.
*Please mark thread ***solved*** so that others can benefit from your solution*.

---

