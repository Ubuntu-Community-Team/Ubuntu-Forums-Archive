---
title: "Ubuntu 64-bit fails to boot"
date: 2008-03-09
forum: General Help
---

### Post by themistocles on 2008-03-09
Just purchased a Gateway FX7024 (Intel Core 2 quad with nVIdia 8800GT video card). Vista works fine (sending this from it). 

I loded the Ubuntu 7.1 live CD (64 bit version) , restarted and got to the  boot screen. I chose the first boot option (normal). The screen went dark, and then I started hearing several beeps, which then become one continuous beep.  They were coming from the motherboard, not the speakers.  I turned off the machine by holding the Power button.

Second attempt,  tried to boot with "safe graphics". It loaded OK (got to the Desktop, launched GIMP, FIrefox etc..). Tried to get online, but could not connect to any site. So I decided to reboot. 

Third attempt, again in "safe" mode. This time, blank screen, multiple beeps that then became one long beep. I gave up and rebooted in WIndows. Everything OK.

Any idea what's wrong? Again, Vista works fine, so doubt this is hardware. Is the 64 bit Ubuntu not ready for prime time? Is a Gateway thing?

I'd hate to return this machine to the store (stocking fee and all), and I can't stand windows!

---

### Post by steveneddy on 2008-03-10
Did you go online and check to see if the hardware was supported yet in Linux.

That is probably your biggest hurdle.

---

### Post by davarino on 2008-03-10
First of all, it is unusual for a Live CD not to boot properly... unless the Live CD was burned improperly. I suggest that you check the md5sum on your Live CD. See this: > **jingo811 said:**
> 
Did you then follow this tutorial in order to MD5sum in Windows?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Did you then follow these steps to burn your *.iso CD like Ubuntu.com suggests?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

If the problem is not in your Live CD, I would suggest, in addition to what steveneddy says, that you look at Ubuntu 7.04 or 6.06LTS if the problem persists.

There *have* been a higher number of problems with 7.10 than with several previous releases.

---

### Post by Sef on 2008-03-10
Besides not checking the md5sum, did you

1) Burn the iso at 4x or less?  (Faster can corrupt the burn.)

2) Check that the disk is good?  (Instead of clicking on start/install, go down the list to 'Check disk for errors' (or something similar.))

---

### Post by themistocles on 2008-03-11
Thanks for the suggestions. 
Where do I check hardware compatibility? 

The ISO image checks out. 
I reburned it, but same problem. 

I found a temporary solution. I suspected that the problem is with the graphics card. So I went to BIOS and changed the VIdeo output to Integrated Graphics option. This allowed me to boot in safe graphics mode, and I am sending this message from the Live CD firefox. 

Now, how do I go about making the awesome nVidia card work?  (sorry for the nooby questions).

---

### Post by themistocles on 2008-03-14
In case someone runs into my same problem with a Gateway FX7024, here's how I did it in the end. 

Used the 32 bit Ubuntu Gutsy Live CD (7.1)
In the BIOS, switched to Internal Graphics (Advanced Settings, VIdeo Settings) to run live CD & install system.
Then I installed the Envy script 
I switched back to Auto in the BIOS on reboot. 
It is now working fine at all resolutions with acceleration. 


Caveat:L Between installing the envy script and getting it top work  there were MANY attempts at configuring the X server etc.. based on various other posts and multiple restarts of the GDM and X Server, and I think a boot or 2 in recovery mode, where I cannot remember what I did. But it seems to be working now...


Anyway, my point is that Gateway FX7014 is compatible with Linux as far as I can tell,

---

