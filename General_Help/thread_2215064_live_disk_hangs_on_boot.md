---
title: "live disk hangs on boot"
date: 2014-04-04
forum: General Help
---

### Post by eli_damon on 2014-04-04
I'm trying to boot from an ubuntu 12.04 live disk. On the purple screen with ubuntu logo, there dots that change between white and red. After a short time, all the dots turn red and nothing seems to happen for a long time. I'm trying this on an Intel 2.4GHz quad core with 3GB of RAM. Please help. Thanks.

---

### Post by Double.J on 2014-04-04
Hi there!

Usually suggest booting with the "--nomodeset" option at grub? Failing that, also recommend double checking the hash of the download and re-creating the install media. 

Most commonly a graphics issue. On desktops this can be further narrowed down by booting using the integrated graphics instead of the graphics card, if available.

---

### Post by eli_damon on 2014-04-04
Thank you for responding. 

Could you tell me how to boot with  "--nomodeset" option? And what does this do? And how can I set which graphics adapter is used? Sorry, I don't these things.

Also, I have more information to add about the issue. After 20-30 minutes, I do see a desktop background and a few icons, but not the full desktop, and no response to keyboard or mouse. Also, the activity light on the disk stops flickering.

---

### Post by Double.J on 2014-04-04
That does sound a bit like unity not loading correctly. On this desktop can you log out ctrl alt bkspc?

To add nomodeset at boot try pressing F6 at the grub menu and using the up/down arrows to select nomodeset
if there is no response from F6, press tab and add --nomodeset to the prompt. As for the technicals behind nomodset, have a look at the answers on this question
[http://askubuntu.com/questions/207175/what-does-nomodeset-do](http://askubuntu.com/questions/207175/what-does-nomodeset-do)

as for changing to the interfrated grphics, it's power off remove graphics card, connect monitor to motherboard port, Reboot.

Do you know the specifics of the hardware? It may help

jj

---

### Post by eli_damon on 2014-04-04
> On this desktop can you log out ctrl alt bkspc?
No. The system is totally unresponsive. The pointer doesn't even move when I move the mouse.
Sorry for being dense, but if I boot from the live disk, I don't see a grub menu. 
Also, I only have one video port, so I am assuming it is connected to the integrated graphics.
I can, it turns out, boot an ubuntu 11.10 live disk, if that tells you anything.
Thanks.

---

### Post by xxx6 on 2014-04-04
better try this 'pal'(thus between qm):

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Its a real speed demon, I mean holy cow is it lightning.
   **[COLOR=#ff0000]5 secs[/COLOR]**    holy crud!
  
I have to give Ubuntu credit here!

---

### Post by eli_damon on 2014-04-04
Also, what hardware specifics are relevant here?

---

### Post by Double.J on 2014-04-05
Well usually the key specs are laptop/desktop if laptop; model, then graphics if know, processor, how much ram etc.

Was there any change after recreating the installation media? If you create a live usb then there will be a grub menu at start so we can see if nomodeset helps.
[Windows]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows")
[Ubuntu]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu")

---

### Post by eli_damon on 2014-04-05
It's an HP-Pavilion desktop with a (copying directly from the system monitor) "Intel(R) Core(TM)2 Quad CPU Q6600 @ 2.4GHz" with 3GB of RAM. The device manager shows a video controller "Hauppauge Inc. HDPVR-1250 model 1196".

Yes, I did try making a new live disk. No change.

---

