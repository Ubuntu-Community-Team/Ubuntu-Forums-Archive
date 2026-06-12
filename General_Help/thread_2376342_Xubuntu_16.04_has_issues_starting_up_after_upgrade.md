---
title: "Xubuntu 16.04 has issues starting up after upgrade to 17.10"
date: 2017-11-01
forum: General Help
---

### Post by 1jarwolf on 2017-11-01
I would I be able to do that before it reboots after the upgrade has been done? The original OS that was on this computer of mine was Windows Vista in which I saw something about that in another thread [https://ubuntuforums.org/showthread.php?t=1613132&page=11](https://ubuntuforums.org/showthread.php?t=1613132&page=11) about [COLOR=#000000]nomodese[/COLOR] Do I just go to the terminal and type [COLOR=#000000]acpi_osi="Windows 2006"[/COLOR] or [COLOR=#000000]acpi_osi="Linux"[/COLOR] or do I type acpi_osi= 
and hit enter and then reboot?

I have tried all of these and nothing has worked. My 16.04 can upgrade just fine but when I go to restart the computer, it goes to a black screen with a dash.

     I then did nano /var/log/Xorg.0.log 
and I get an error as far as I know it says

[     2824.423]  (EE) modeset (0): Failed to initialize glamor at ScreenInit() time.
[     2824.423]  (EE)
Fatal server error:
[     2824.423]  (EE) AddScreen/ScreenInit failed for driver 0
[     2824.423]  (EE)
[     2824.423]  (EE)

---

### Post by yetimon_64 on 2017-11-01
> **1jarwolf said:**
> ... about [COLOR=#000000]nomodese[/COLOR] Do I just go to the terminal and type [COLOR=#000000]acpi_osi="Windows 2006"[/COLOR] or [COLOR=#000000]acpi_osi="Linux"[/COLOR] or do I type acpi_osi= 
and hit enter and then reboot?...
You need to read the opening post of the thread you linked to (Page 1 of the thread), all the information you need, to use the boot optoins, is in the opening post there. Your link here is to page 11 of that thread.

nomodeset and those other boot options mentioned are usually added to the "GRUB_CMDLINE_LINUX_DEFAULT=" line of the file /etc/default/grub.

In the link you included read further down the opening post of the thread, specifically the section titled [SIZE=2]"How to permanently set kernel boot options on an installed OS (not wubi)"[/SIZE] for how to permanently set any of those options.

However at the moment as you cannot get to a desktop you will first have to temporarily set the options to get yourself into the system from which you can then set them as permanent. To do so read the section in your link "How to temporarily set kernel boot options on an installed OS (not wubi)". 

Regards, yeti.

---

### Post by 1jarwolf on 2017-11-02
I know, it did not work. I have made a fresh Xubuntu 17.10 on a USB and went to install it, it installed, shows a black screen but now I see a cursor and like blue and red coloring across the top of the screen and about half of a centimeter ? wide. Is there any way I can perhaps lower the resolution or something of the startup?

---

### Post by mörgæs on 2017-11-02
I think it's about time that we get to see the hardware details. 

From any Buntu running installed or from a live boot, please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` to the terminal, run it and post lshw.txt in CODE tags.

---

### Post by 1jarwolf on 2017-11-03
Alright so, it did not let me upgrade from the system it's self, but when I used my dad's laptop to download the Xbuntu 17.10 onto a USB ((as I do not have a Windows PC)) and I then installed the OS onto my laptop and it worked....so, it has to be something about upgrading from the previous version to the newer one on the system itself which I have no clue as to how that can happen.

---

### Post by mörgæs on 2017-11-03
[https://ubuntuforums.org/showthread.php?t=2376183&p=13705661&viewfull=1#post13705661](https://ubuntuforums.org/showthread.php?t=2376183&p=13705661&viewfull=1#post13705661)

---

