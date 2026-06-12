---
title: "Startup Application does not work when HDMI is not plugged in"
date: 2015-04-18
forum: General Help
---

### Post by carr3 on 2015-04-18
Hi,

I have a startup application that runs successfully on my Nvidia Jetson TK1 (runs ubuntu 14.04).  This application does not require a screen to run, so we disconnected the HDMI cable.  But when I remove the HDMI cable from the Jetson, the application is not able to run (I checked by SSHing into it).  I assumed that during boot up the HDMI is turned off for power saving, which may affect the startup application.  Any suggestions on how to run a startup application program without HDMI plugged in would be appreciated.

Thanks,
Carr

---

### Post by papibe on 2015-04-18
Hi carr3.

Could you post the content of these file, right after a boot with no HDMI connected?
```
/etc/X11/xorg.conf
```
Please paste it here: [Ubuntu Pastebin]("http://paste.ubuntu.com/"), and then post back the link to it.

Also, could you give us more information about the application, and how it is being launched?

Regards.

---

### Post by carr3 on 2015-04-19
Hi Papibe,

Here is the content of that xorg.conf file:

[http://paste.ubuntu.com/10853677/](http://paste.ubuntu.com/10853677/)

The application is an executable that was generated from a c++ program I made.  It uses OpenCV/CUDA.  The program itself captures images from a live camera feed and manipulates the frames.  The application is launched using the startup application manager linked to the executable.  I believe the problem is that the EDID is not being setup properly because the HDMI is not being detected.

Thanks,
Carr

---

### Post by papibe on 2015-04-19
Thanks.

I believe you have just one monitor then? 

If the HDMI is not connected how do you login into the desktop (and thus triggering the 'Startup application script')?

Could you do the same with this file (right after a boot with no HDMI connected)?
```
/var/log/Xorg.0.log
```
Regards.

---

### Post by carr3 on 2015-04-21
Yes, I've been using just one monitor.  When the Nvidia Jetson first boots up, it does not prompt me for login information.  It goes straight to the desktop.  Here is the code from the Xorg.0.log file (unfortunately could not ssh into jetson so HDMI was in use. Hopefully this is still useful.):

[http://paste.ubuntu.com/10862568/](http://paste.ubuntu.com/10862568/)

I have also been reading that the startup application may be something that the desktop environment starts.  So since there is no HDMI connected, the desktop environment may not be started at all, which means the startup application will also not start.  Is it possible to configure X.org to start the desktop environment anyway without HDMI?  Also read that I should try running the program via etc/rc.local, but I have not had much success.

Thanks,
Carr

---

### Post by carr3 on 2015-04-21
Solved the problem by running the executable through etc/rc.local.  Thanks for your help papibe!

---

