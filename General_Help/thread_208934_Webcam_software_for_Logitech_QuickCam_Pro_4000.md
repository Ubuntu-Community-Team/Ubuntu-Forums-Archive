---
title: "Webcam software for Logitech QuickCam Pro 4000"
date: 2006-07-04
forum: General Help
---

### Post by Muffe on 2006-07-04
I have a  Logitech QuickCam Pro 4000 USB webcam connected to an Ubuntu Dapper PC. The camera is fixed in a window, and grabs a picture every minute and upload it to a webserver via FTP. I am currently using the 'setpwc', 'dov4l', 'streamer' and a custom shell script to capture the image and upload it.

The problem is that the image quality is poor, mainly because neither of the programs that I use support any kind of auto-adjusting the camera settings (brightness, gain etc). Therefore, I have configured it to take OK pictures in bright daylight, and when it gets cloudy or darker, the image is virtually black.

Does any of you know about any kind of software that can capture pictures and do some auto-adjustments (mainly on the brightness) that improves the over-all quality of the images?

What else can I do to make the image quality better?

Thanks.

---

### Post by erimar77 on 2006-07-04
i don't have a webcam, but have you looked at the qc-usb-utils package.. i was just browsing through synaptic
> Utilities to tweak paramters of your QuickCam Express or similar
webcam.

---

### Post by sal on 2006-07-04
[QUOTE=Muffe]I have a  Logitech QuickCam Pro 4000 USB webcam connected to an Ubuntu Dapper PC. The camera is fixed in a window, and grabs a picture every minute and upload it to a webserver via FTP. I am currently using the 'setpwc', 'dov4l', 'streamer' and a custom shell script to capture the image and upload it.

The problem is that the image quality is poor, mainly because neither of the programs that I use support any kind of auto-adjusting the camera settings (brightness, gain etc). Therefore, I have configured it to take OK pictures in bright daylight, and when it gets cloudy or darker, the image is virtually black.

Does any of you know about any kind of software that can capture pictures and do some auto-adjustments (mainly on the brightness) that improves the over-all quality of the images?

What else can I do to make the image quality better?

Thanks.[/QUOTE]


could you please document how you got the quickcam 4000 working in dapper. thanks.

---

### Post by Muffe on 2006-07-05
1: Locate a free USB input on your computer.
2: Take the USB plug from the camera in your right hand.
3: Insert it into the port you found under #1.
4: The camera is now working.

This process works on both Dapper and Breezy.

Has anyone else got any tips regarding my problem?

---

