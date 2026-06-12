---
title: "New to Ubuntu and having a major issue"
date: 2015-08-02
forum: General Help
---

### Post by alex_turner on 2015-08-02
Idk what to do I've looked everywhere for an answer but everything up to when I log in works fine. As soon as I log in everything goes away and I only have my mouse cursor and background on screen. I've found ppl saying that it is because unity isn't loading and to do some things in the terminal but the terminal won't come up. Then I see them saying to bring up tty with ctrl alt F(x) but that doesn't do anything but bring me to a blank screen so I have no idea how to fix this issue. Please help if yall have any ideas

---

### Post by sudodus on 2015-08-02
Welcome to the Ubuntu Forums :-)

Without knowing more it looks like a problem with the driver for the graphics chip/card. But in order to give relevant advice, we need to know more about your system. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Also, please tell us

- the version of Ubuntu
- other operating systems (Windows, MacOS?)

Did you try this hotkey combination (press all 3 keys at the same time)?

***ctrl + alt + F1***

---

### Post by alex_turner on 2015-08-02
It's a pic I built myself I have a 4.4ghz Richmond cpu 16gb of ram nvidea 750ti graphics card and no wifi card as I run a direct Ethernet cable since it's a desktop. I'm running version 14.10 and have no other os on this hard drive and yes I used the combination not individual presses for ctrl+alt+f1

---

### Post by ajgreeny on 2015-08-02
You probably need the nomodeset boot option in order to get to a GUI desktop, from where you can install the proprietary nvidia driver fron Additional Drivers.
From.the grub menu, (hold shift at boot to see that, or Esc if a UEFI system) hit e to edit and on the kernel line change "quiet splash" to "nomodeset" then Ctrl + x to boot, hopefully to a complete desktop, though prpbably low resolution. Install the additional driver from.here and you should now be OK.

---

### Post by sudodus on 2015-08-02
+1 to the boot option nomodeset and then install a proprietary nvidia driver

---

### Post by buzzingrobot on 2015-08-02
> **sudodus said:**
> +1 to the boot option nomodeset and then install a proprietary nvidia driver

Yep.  It's the 750ti and the version of Nouveau (the open source video driver) that are the culprits. That driver can't handle the Kepler chip in the 750ti (I have one, too.)

Do a boot with nomodeset.  You'll get a display that's poor but good enough to run Additional Drivers and install the proprietary Nvidia driver.  Reboot and you should be good.

---

### Post by grahammechanical on 2015-08-02
You say you are using 14.10 but that has recently reached end of life. You will be better off using 15.04. 

Try from the Grub boot menu Advanced options for Ubuntu>Recovery Mode>Resume. You will need to hold down the shift key to bring up the menu as you only have Ubuntu installed and we do not get a boot menu if Ubuntu is the only OS.

Regards

---

### Post by sgian on 2015-08-02
That is a good point about 14.10 reaching end of life, so it won't be updated anymore.  14.04 LTS and 15.04 are still supported, I've been using the LTS.

---

### Post by alex_turner on 2015-08-03
Still having the an issue my Linux boot line doesn't have quiet splash at the end but instead debug_plymouth tried doing nomodeset before that but no luck as of yet

Ok update. Upgraded my version from 14.10 to 15.04 from finally being able to access my tty menu. From there ran into a login loop issue so I purged my nouveau drivers and installed the proprietary nvidia-352 drivers. Same problem though now I can log in and I can do a little bit more stuff like open the terminal but that's about it my actuall desktop still won't load

---

### Post by efflandt on 2015-08-04
If you did not use nomodeset boot parameter during install, you can either add **nomodeset** between the quotes in the GRUB_CMDLINE_LINUX_DEFAULT= line of /etc/default/grub (using **sudo nano** or **gksu gedit**), or add a line after that line **GRUB_CMDLINE_LINUX="nomodeset"**. Then run **sudo update-grub** 

I am using a GTX 750 Ti, but in 64-bit 14.04. Not sure which nvidia packages 15.04 includes, but mine worked fine with nvidia-331-updates from normal repos and is currently running nvidia-352 package from xorg-edgers ppa without any issues. I have never purged or done anything else related to nouveau (installing nvidia drivers takes care of blacklisting that).

---

### Post by Topsiho on 2015-08-04
The non-LTS versions are only maintained during 9 months. The LTS-versions during 5 years. So my advise is to use 14.04, which is the latest LTS-version. It is maintained until April 2019.

I have a remark here, as a non-native English speaker: you would get a lot more response (though the responses that you got here are probably quite good enough :) ) if you put them in common English rather than in a sort of newspeak. I had to think for some time what you meant with "Idk what to do" (I think it is: "I don't know what to do"), and probably you could find the other examples in your texts yourself. Please don't forget this is an international forum, lots of users here have a very limited knowledge of English ( but more than you most probably have of their respective languages :)  ).

Topsiho

---

### Post by Vladlenin5000 on 2015-08-04
> **Topsiho said:**
> I have a remark here, as a non-native English speaker: you would get a lot more response (though the responses that you got here are probably quite good enough :) ) if you put them in common English rather than in a sort of newspeak. 


+1

---

