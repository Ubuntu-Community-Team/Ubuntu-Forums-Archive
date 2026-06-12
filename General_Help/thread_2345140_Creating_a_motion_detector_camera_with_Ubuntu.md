---
title: "Creating a motion detector camera with Ubuntu"
date: 2016-11-30
forum: General Help
---

### Post by ChristmasPi on 2016-11-30
I am running Ubuntu 14.04 on my laptop and I have a logitech camera.

I was wondering if there was any way to setup the camera on my laptop so that it acts as a motion detector camera and takes pictures whenever something goes by the camera.

Thank you

---

### Post by yancek on 2016-11-30
Probably the best or at least software with most options is zoneminder.  See the link below which has instructions for different Ubuntu releases.

[https://wiki.zoneminder.com/Ubuntu](https://wiki.zoneminder.com/Ubuntu)

Motion is another simpler option, should be in the Ubuntu repositories.

---

### Post by papibe on 2016-11-30
Hi ChristmasPi.

Definitively possible. Take a look at a package called 'motion' for a simple option, and 'zoneminder' for a complete surveillance solution. 

Hope it helps. Let us know how it goes.
Regards.

---

### Post by ChristmasPi on 2016-12-01
> **papibe said:**
> Hi ChristmasPi.

Definitively possible. Take a look at a package called 'motion' for a simple option, and 'zoneminder' for a complete surveillance solution. 

Hope it helps. Let us know how it goes.
Regards.

Thank you, I have been playing around with Motion.  I'm not the best in setting these things up without a GUI, but what I'm struggling with is setting up the USB camera to record.  I have an integrated camera in my laptop and I have attached a USB logitech camera as well.  Motion is using the integrated camera by default, but I'm not clear on what I need to do to get it to record from the USB camera.

I know the USB camera works because it is detected by Cheese Webcam Booth.

I think i might have to do something with this section of the config file, I'm just not sure what to enter for my USB camera.

###########################################################
# Capture device options
############################################################


# Videodevice to be used for capturing  (default /dev/video0)
# for FreeBSD default is /dev/bktr0
videodevice /dev/video0



Thank you

---

### Post by yancek on 2016-12-01
> Videodevice to be used for capturing  (default /dev/video0)

That's the expected default for the camera so if you have two cameras, try running "ls -l /dev/video*" (without quotes) to see what else shows.  Possible /dev/video1

---

