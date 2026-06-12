---
title: "4k Monitor resolution issue"
date: 2019-05-14
forum: General Help
---

### Post by badziobw on 2019-05-14
Hello, I have recently started usimg ubuntu 18.04 and loved its performance thus far. I had it installed as a dual boot alongside windows 10. 
Last week I have purchased an 32 inch 4k Samsung monitor  model U32J590. I am studying web programming and wanted another large display as my 15 inch laptop wasnt enough. However I cannot get Ubuntu to use 4k or even 2k resolution. I found out that this monitpr is 4k only on 30hz but even that doesnt work. Everything works fine on Windows. 
Could someone guide me through steps of being able to use this monitor to the fullest on ubuntu?

I have tried several methods from intrrnet myself but it led to me not being able to go past black screen of ubuntu loading up on the start up and i had to reinstall the whole OS.

---

### Post by dino99 on 2019-05-14
is the graphic card or chip able to get 4k working ? How is that display identified into Settings ? Is there errors into journalctl about that device ?

---

### Post by badziobw on 2019-05-27
Hi sorry, for the late reply I was on vacation. There are no errros about the device in journalclt. As I said the monitor has no problem displaying in 4k on windows, but there I am able to install some drivers for it (windows only).  If it works on windows i suppose processor/chip are no issue?  it is identified as Samsung Electric Company 31" with highest possible resolution of 1920x1080.  Adding anything bigger than that does not work through xrandr.

---

### Post by Autodave on 2019-05-27
Can we have some info on your laptop?  How is the monitor connected: VGA, HDMI, DVI, etc?

---

### Post by badziobw on 2019-05-27
Yes the laptop is msi GL62 6QD . I have found out that this monitor in 4k works only in 30hz therefore I only tried to setup the modes using xrandr as 30hz and o ly true hdmi 2.0 if Im correct. this is how I connected it to my laptop. and it is allowing 4k resllution in windows but not ubuntu.

---

### Post by CatKiller on 2019-05-27
If your laptop had a HDMI 2.0 (or DisplayPort 1.2) port that monitor would do 4K 60Hz. Since it only has HDMI 1.4 you're limited to 4K 30Hz, or a lower resolution at 60Hz. It's a bandwidth thing.

The issue with your setup is that you're trying to run a single display (combined laptop and monitor) at both 60Hz and 30Hz at the same time. Since you're using Nvidia graphics, you may be able to setup TwinView, where they're more separate.

You don't need to reinstall the OS just because the graphics are broken; you can edit files from the command line and install/uninstall/reconfigure things using the install disk, should you be in that position again.

---

### Post by badziobw on 2019-05-28
> **CatKiller said:**
> ...

And how can I set up that TwinView, I cannot see any option like that in Nvidia driver settings on ubuntu. Any ideas?

---

### Post by CatKiller on 2019-05-28
> **badziobw said:**
> And how can I set up that TwinView, I cannot see any option like that in Nvidia driver settings on ubuntu. Any ideas?
It's a long time since I played with dual monitors. At that time it meant setting things up in xorg.conf. It probably still does.

---

### Post by badziobw on 2019-05-28
> **CatKiller said:**
> It's a long time since I played with dual monitors. At that time it meant setting things up in xorg.conf. It probably still does.

Thats when I ran into trouble, I tried adding settings to 2nd monitor in xorg. And it all led to me not being able to get past black screen on startup , the terminal krpt saying Cant Open display.

---

### Post by badziobw on 2019-05-28
Does anyone know how could I set up this monitor in xorg.conf for it to display 4k?

---

### Post by badziobw on 2019-05-30
bump

---

### Post by kryten35 on 2019-05-30
Run Nvidia X Server Settings

X Server Display Configuration

Detect displays

Click on 4k monitor -in the Configuration dropdown do you get the TwinView option?You should be able to enable /disable monitors and change the resolution and refresh rate here.To make it apply for every boot

Save to X Configuration File

Click Show Preview
Copy all of it
sudo nano /etc/X11/xorg.conf
paste everything and exit.

---

