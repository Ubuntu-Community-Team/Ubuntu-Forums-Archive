---
title: "BIOS/Ubuntu Hardware Issues"
date: 2012-10-17
forum: General Help
---

### Post by NFLDPower on 2012-10-17
Hey guys, first post so hopefully it in the right section.

Anyway, I got this laptop from a friend who was running Windows but one of her "smart" friends deleted the contents of the entire harddrive to rid it of some malicious software ie: a virus of some sort. 

So I get my hands on the laptop and I decide to install Ubuntu 11.10 on it cause I happened to have a copy on a bootable USB ready to go. I turn on the machine and try to get into the BIOS to change the boot order when I get hit with a prompt for a password. She had no idea what is was and I think it was set on it by the manufacturer or the retailer. I know its possible to reset the BIOS/CMOS settings manually on the motherboard but thats my last resort at this point. 

So I take out the harddrive and install Ubuntu on it via another machine I have but it installs with the hardware specifications of the machine I used to install it. I kinda expected it to happen so thats only minor stuff at this point. 

TL;DR version

What I'm asking here is:
Can I do a Ubuntu system restore from inside the OS? (For the purpose of installing with the right hardware specs)

Is there a utility available for Linux that I can configure the BIOS from inside the OS? I know Windows has one. 

Keep in mind I cannot access the BIOS to boot from a USB/CD at this point.

Please help guys or I'm just gonna have another 250gb external harddrive :)

---

### Post by 2F4U on 2012-10-18
> Is there a utility available for Linux that I can configure the BIOS from inside the OS? I know Windows has one. 

I doubt that Windows can change a BIOS with a password on it, since it would be against the purpose of the password.

> She had no idea what is was and I think it was set on it by the manufacturer or the retailer. 

Very unlikely. Then it would be documented somewhere.

> Can I do a Ubuntu system restore from inside the OS? (For the purpose of installing with the right hardware specs)

The hardware will be detected everytime you start the OS, and, unless you are installing proprietary drivers, it shouldn't matter. Of course, the machines should have the same architecture, i. e. 32 or 64 bit. So, if you install on 64 bit, don't put the disk into a 32 bit machine.

---

### Post by mardybear on 2012-10-18
Hi NFLDPower...

Welcome to the Ubuntu forums :)

My brain tends to work best in a simple, logical way.

You lost me at the very beginning...wouldn't it be much easier to simply reset the BIOS so you can install Ubuntu directly onto the proper machine. To my knowledge, most laptops can be accessed with a simple screwdriver.

If it's now your computer i can't imagine why you wouldn't want full access to your BIOS anyways.

mardybear

---

### Post by Cheesemill on 2012-10-18
It's not a problem switching the drive from one machine to another, just don't install any of the Additional Drivers first.

As mentioned above, unlike Windows the Linux kernel probes for available hardware and loads the correct drivers every time you boot. I've switched drives like this countless times with no issues.

---

