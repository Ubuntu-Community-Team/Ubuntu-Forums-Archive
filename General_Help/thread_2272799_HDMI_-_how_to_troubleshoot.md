---
title: "HDMI - how to troubleshoot?"
date: 2015-04-08
forum: General Help
---

### Post by sunfromhere2 on 2015-04-08
Hello!

I have 2 laptops (Ubuntu 12.04, Fedora 20) that I'm trying to connect via HDMI cable to Samsung TV, but I'm getting no signal.

Both laptops recognize the TV when I go to Settings - Display: it is shown as a Samsung TV, and I'm able to change the resolution, select whether it's primary/secondary/mirrored etc.

Both laptops give this output in terminal for xrandr (different resolutions though):

HDMI-0 connected (normal left inverted right x axis y axis)
   1920x1080     60.00 +  50.00    59.94    30.00    25.00    24.00    29.97    23.98  
   1920x1080i    60.00    50.00    59.94  
etc

But the TV constantly claims: No signal, check the connection.

Both laptops have Intel integrated chips. There is a Win7 laptop in the house, but on Display it doesn't even recognize the TV as an additional display.

Now, this is probably a TV issue, but is there any additional way to test HDMI connection to see what may be wrong? Thanks!

---

### Post by Eglefino on 2015-04-08
I have a Samsung TV (Syncmaster) myself with a desktop and a NVIDIA graphic card. I can't give you any commands (I'm too a starter) but I tried to connect a VGA-cable first, you have to change the connectionof the source to PC-TV on the Samsung. When I had all setup, I took the hdmi and took it together and changed the connection to hdmi- ? and refresh the connection with the red button of the remote.
IMO your trouble is the source in the menu of the TV, you can change them between each other. Read the manual of your TV.

---

### Post by SeijiSensei on 2015-04-09
I have to ask this:  you did switch the TV to the correct HDMI port, right?

I'm looking at a 32" Samsung TV right now that is connected to a laptop with HDMI.  I just connected them together, switched the TV to the proper HDMI port, and it all worked.  This TV has three HDMI ports; the most convenient one was on the side of the device and labelled HDMI3.

---

### Post by sunfromhere2 on 2015-04-09
Thanks for the answers.
'Twas the cable :)

Borrowed another cable, it works plug'n'play.
Going to the store tomorrow to replace it.

---

