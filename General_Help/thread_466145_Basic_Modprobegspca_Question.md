---
title: "Basic Modprobe/gspca Question"
date: 2007-06-06
forum: General Help
---

### Post by telemann on 2007-06-06
I'm hoping this is an easy one ;)

I have a logitech quickcam chat attached to a Feisty LAMP server.  The camera insists on setting it's brightness and contrast values to really stupid choices.  I'm trying to turn off the camera's/driver's ability to automatically and continually set these values.

I have a theory that I might be able to turn this stuff off by putting some config options in 
/etc/modprobe.d/gspca.modprobe

The problem is I can't find a list of available config options anywhere for the gspca module.  Is there some easy way to get modprobe to list them for me?  Are they documented somewhere?

Thanks a lot for reading.

---

### Post by isayhelloyousaygoodbye on 2007-08-29
modinfo  /lib/modules/`uname -r`/kernel/drivers/usb/media/gspca.ko
..
parm:           autoexpo:Enable/Disable auto exposure (default=1: enabled) (PC-CAM 600/Zc03xx/spca561a/Etoms Only !!!) (int)
parm:           debug:Debug level: 0=none, 1=init/detection, 2=warning, 3=config/control, 4=function call, 5=max (int)
parm:           force_rgb:Read RGB instead of BGR (int)
parm:           gamma:gamma setting range 0 to 7 3-> gamma=1 (int)
parm:           OffRed:OffRed setting range -128 to 128 (int)
parm:           OffBlue:OffBlue setting range -128 to 128 (int)
parm:           OffGreen:OffGreen setting range -128 to 128 (int)
parm:           GRed:Gain Red setting range 0 to 512 /256  (int)
parm:           GBlue:Gain Blue setting range 0 to 512 /256  (int)
parm:           GGreen:Gain Green setting range 0 to 512 /256  (int)
parm:           compress:Turn on/off compression (not functional yet) (int)
parm:           usbgrabber:Is a usb grabber 0x0733:0x0430 ? (default 1)  (int)
parm:           lightfreq:Light frequency banding filter. Set to 50 or 60 Hz, or zero to NoFliker (default=50) (int)
..


btw, the file apparently can also be called /etc/modprobe.d/gspca


although force_rgb fixes the color problem (all blueish) for me in camorama, the stills taken with motion remain odd-coloured.

---

### Post by DBO on 2007-09-05
motion will give odd colors if you force RGB as it understands BGR.  You will want to leave force rgb off and use applications that dont need it.  Cheese/mplayer/motion/webcam all do fine with BGR.

---

### Post by fragos on 2007-09-05
I don't think the gspca driver supports all of the GUI adjustments for your model of webcam.

---

### Post by rudlavibizon on 2007-12-28
Is it possible to make a script that wil change this whenever I want to use different programs?

---

