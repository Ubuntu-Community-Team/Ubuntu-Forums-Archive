---
title: "Error in Laptop trying to access UEFI Toshiba running Ubuntu"
date: 2018-04-27
forum: General Help
---

### Post by bmcgonag on 2018-04-27
I have Ubuntu 17.10 installed, and want to move to 18.04.  I'm trying to boot from USB, but while using F12 on boot gets me to the boot menu, none of the options actually go anywhere when selected (USB, internal main SSD, nothing).  It just freezes there. 

If I try to get to the UEFI / Bios setup using F2 on boot, the machine just continually reboots everytime I catch it with the F@ option. 

I've tried multiple options for fixing Grub to give me the UEFI option, which it does already anyway, but it gives an error when I select it. 
```

Error: could not set EFI variable `OsIndications'.  Press any key to continue.
```

I'm getting to my wit's end, and I just don't know what to try from here.  I can still boot into Ubuntu, but in no way can I boot from USB or into setup to change the boot order.

Any help or ideas are greatly appreciated.

---

### Post by oldfred on 2018-04-27
Does this work?

```
systemctl reboot --firmware
```

---

### Post by brimcgon on 2018-04-28
Tried it but got

```
Cannot indicate to EFI to boot into setup mode: Connection timed out
```

Thoughts? Meanwhile I'll check out the linked thread.

---

### Post by leunam12 on 2018-04-28
Try a cold start up:
1-Shutdown your computer.
2-Unplug the power cord
3-Remove the battery.
4-Press the power button for 45 seconds.
5-Re install the battery
6-plug the laptop to the power cord
7-Press power button and then try to go to BIOS using F2

---

### Post by brimcgon on 2018-04-28
Tried that, and still just go into reboot when pressing F2, and freezes up if trying to use F12 and selecting any device from the list *even the internal SSD that always boots).  

Additionally, have now removed the bottom of the laptop, removed the SSD completely, then plugged in just the USB, and oweer (no battery, and tried, and get the message 'No bootable device found'.  

So, I re-burned the .iso, and tried again.  Same result.  I'm going to find another PC and make sure the USB stick is good, but I think it is.  

Even without the USB I should still be able to get to BIOS / UEFI setup, so I'm still thinking that's where the problem is.

---

### Post by oldfred on 2018-04-28
Have you updated UEFI from Toshiba? 
Many have had to get newest UEFI to have everything work.

---

### Post by brimcgon on 2018-04-28
So, went to toshiba site, adn they only have .exe's for their BIOS / firmware updates.  I thought, "Oh, I'll just use FreeDOS!", then nearly slapped myself in the head, because the whole issue is I can't get the system to boot from a USB.

Dangit!

---

### Post by brimcgon on 2018-04-29
I've literally found nothing that will work thus far.  I'm still open to thoughts or ideas. 

To reiterate the issue:

Toshiba Laptop running Ubuntu Linux with an SSD and 12 GB RAM. 

I want to fresh install Ubuntu 18.04, but when I reboot the machine (or shutdown then restart it) and try to access the BIOS / UEFI menu, using F2, it just reboots immediately, and this cycle continues until I stop trying F2.  

If I use F12 to get to the boot menu, I get the boot options, but any I select and then press Enter to enact, cause the machine to completely freeze up. 

On that menu I have the option of 'Enter Setup'.  Selecting that reboots the machine, then takes me to the grub menu. 

Still can't get to the setup menu, or get it to boot from USB no matter what I try. 

Thanks for all of the suggestions so far, and keep them coming.

---

### Post by oldfred on 2018-04-29
Have you tried a total cold boot.
That is remove all power, remove battery, hold power switch for 10 sec or so to drain all power.
The boot and see if f2 or whatever correct key to get into UEFI/BIOS is works.

---

### Post by brimcgon on 2018-04-30
Yes, I have tried that as well. Same result. 

I also tried removing the hard drive completely, then just plugging in the USB, and booting to force it to use the USB, and nothing.  It just says no bootable device found.  The issue is I can plug the USB into other machines and boot from it just fine, so I know it's not the USB.

---

### Post by oldfred on 2018-04-30
Can you relatively easily access coin battery on motherboard. 
Removing that for a while should then reset UEFI.

My motherboard also has jumper pins next to battery to do a full reset.
But I have a SSD on USB adapter. It boots fine from ESP on hard drive, but I tried to configure to directly boot from UEFI. After several tries system totally locked up. All the suggestions did not work. And then unplugging internal drive with UEFI & replugging it in did work. But that drive has a working bootable system.

---

### Post by linux4me on 2018-04-30
You're not trying to do this with an external keyboard by any chance, are you? According to [Toshiba]("https://support.toshiba.com/support/viewContentDetail?soid=627009"), you can also try the Escape key method of accessing setup.

---

### Post by brimcgon on 2018-04-30
Found the solution - finally.  Apparently this was an issue caused by a kernel update with 17.10 and the Intel SPI stuff.  

Luckily some amazing person made a kernel to fix the issue.  So that rocks!

Here is the link to the site with all of the relevant information.  Hope it helps someone else. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147)

---

### Post by linux4me on 2018-04-30
> **brimcgon said:**
> Found the solution - finally.  Apparently this was an issue caused by a kernel update with 17.10 and the Intel SPI stuff.  

Luckily some amazing person made a kernel to fix the issue.  So that rocks!

Here is the link to the site with all of the relevant information.  Hope it helps someone else. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147)

Nice job! If the Board will allow it, you might want to change your post title to make it easier for other sufferers to find.

---

