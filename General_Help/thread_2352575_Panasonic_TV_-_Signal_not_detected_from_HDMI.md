---
title: "Panasonic TV - Signal not detected from HDMI"
date: 2017-02-13
forum: General Help
---

### Post by mikenewb on 2017-02-13
Hi guys,

I am new to Ubuntu 16.04 and have it installed alongside windows 10 on my ASUS Vivo (miniPC). I am mainly using the computer to stream netflix etc and some surfing.
Anyways Ubuntu worked fine after installation and I was using my Panasonic TV as a monitor via the HDMI on the computer. After clicking around in my new os i found the Additional Drivers in the Software & Updates menu. The graphics card (a Geforce 820M) was using the X.Org X Server - Nouveau display drivers. I changed this to the NVIDIA Binary driver and rebooted the computer. After reboot my screen (Panasonic TV) was all black. Nothing I tried worked so I went and got a Lenovo monitor from my work-computer downstairs and connected it via the Dp and voila it worked. I uninstalled the Nvidia drivers and setup the card with the Nouveau drivers again, but I still cant get a signal when I connect the TV to the HDMI port. However connecting the Lenovo Monitor to the HDMI or DP works just fine.

HDMI Cable works, HDMI out on the computer works, but Panasonic TV can't get a signal. I will go out and buy a Displayport to HDMI adapter after work tomorrow and try connecting the HDMI from the TV to the DP on the computer to see if that works.

**Anyone had similar problems or know how to fix this?**

---

### Post by mikenewb on 2017-02-14
Ok, heres some new info. I reinstalled Ubuntu (clean), and the problem persists. I have now connected both the lenovo monitor (via DP) and the TV via HDMI. When I start up the computer, I get picture on both screens up to the point where it goes from the Purple screen and switches to Ubuntu login. When this happens I lose the signal on the TV.

---

### Post by Bucky Ball on 2017-02-14
Welcome. Main thing is you have all cables plugged as they should be with everything switched off, switch TV on and make sure you are on the right HDMI source for the computer (HDMI1 or whatever), then switch on the computer with the TV already on and ready to go. Sound like you're doing that in the correct sequence, though. :-k

With everything switched off, make sure cables are where they should be, switch on TV, boot computer, login on the computer (regardless if you're getting a picture on TV) and go to 'Display'. Do you see the HDMI display plugged in there and disabled? See any other anomalies with the configuration? Any other clues? 

If the HDMI monitor is not showing in 'Display' then that is a big fat clue. Let us know if 'Display' shows the TV. You installed the NVidia driver. Do you have the NVIdia X server settings GUI in your apps? You may also be able to do something with that.

Or you could simply switch back to the open-source nouveau driver.

---

### Post by mikenewb on 2017-02-14
> **Bucky Ball said:**
> Welcome. Main thing is you have all cables plugged as they should be with everything switched off, switch TV on and make sure you are on the right HDMI source for the computer (HDMI1 or whatever), then switch on the computer with the TV already on and ready to go. Sound like you're doing that in the correct sequence, though. :-k

With everything switched off, make sure cables are where they should be, switch on TV, boot computer, login on the computer (regardless if you're getting a picture on TV) and go to 'Display'. Do you see the HDMI display plugged in there and disabled? See any other anomalies with the configuration? Any other clues? 

If the HDMI monitor is not showing in 'Display' then that is a big fat clue. Let us know if 'Display' shows the TV. You installed the NVidia driver. Do you have the NVIdia X server settings GUI in your apps? You may also be able to do something with that.

Or you could simply switch back to the open-source nouveau driver.

The "Display" does not show the TV, just the Lenovo monitor. When I hit the "search monitors" button nothing happens. The strange thing is that I get a picture both on the BIOS picture and the Ubuntu screen where I can chose either Ubuntu, safe mode and a couple of more options. After I press enter on the Ubuntu startup it goes to a purple screen for a couple of seconds, and its when this purple screen switches to the ubuntu login the signal is lost to the TV. Dunno if my explanation makes sense :p

After following some guides I tried the  gksudo nvidia-settings command, this opened the Nvidia x server settings app. After closing the app this Error appeared in the terminal:

mike@AsusMike:~$ gksudo nvidia-settings


ERROR: nvidia-settings could not find the registry key file. This file
       should have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       prepopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.

---

### Post by Bucky Ball on 2017-02-14
Where did you get this NVidia driver? Additional Drivers? You should have. Have a look in 'Additional Drivers' and see what is enabled there, if anything. The correct NVidia driver for your card should be there.

As I have already said, the x server settings app is right there in your apps, no need for opening from a terminal. Try opening from there and see what error you get.

Install the driver from 'Additional Drivers' if you haven't already and that should reliably install everything you need, including a functioning x server settings GUI.

---

### Post by mikenewb on 2017-02-15
Hi! I have installed them both from Additional Drivers and in the terminal. Do you think this issue has something to do with my computer also having an integrated intel graphics card on the mortherboard? Its the Nvidia-340 package that is reccomended for my card, and thats what I have installed atm.

---

### Post by Bucky Ball on 2017-02-15
Try booting to the BIOS and disable 'Internal video'. That refers to the video chip on the MB. It may be called something other than 'internal video' but similar. If you have a discrete video card hanging off the board, you do not want the internal video attached to the motherboard enabled as well.

I have a GTX 790 and a sound card and both internal video and audio off in the BIOS.

---

### Post by mikenewb on 2017-02-21
> **Bucky Ball said:**
> Try booting to the BIOS and disable 'Internal video'. That refers to the video chip on the MB. It may be called something other than 'internal video' but similar. If you have a discrete video card hanging off the board, you do not want the internal video attached to the motherboard enabled as well.

I have a GTX 790 and a sound card and both internal video and audio off in the BIOS.

Sorry for the late reply. I dont have the option to turn it off in the BIOS. Anyway the error seems to be on and off. I havent found out what triggers it yet. If you take a look at the pictures I havent done anything inbetween the two. Really weird..

---

