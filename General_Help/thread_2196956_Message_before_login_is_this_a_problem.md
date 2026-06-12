---
title: "Message before login: is this a problem?"
date: 2014-01-01
forum: General Help
---

### Post by tfglynn on 2014-01-01
Hello. I very recently installed Ubuntu 13.10 onto my laptop to replace Windows 8. This is my first time using Ubuntu. Everything has worked fine so far, but I've been getting a message while booting up and I don't know whether I should be concerned. The message appears right before my login page and it disappears after a couple of seconds. Here it is:

```

[   12.448751] nouveau 0000:02:00.0: Invalid ROM contents
[   12.448880] nouveau E[   VBIOS][0000:02:00.0] unable to locate usable image
[   12.448925] nouveau E[  DEVICE][0000:02:00.0] failed to create 0x10000001, -22
[   12.448964] nouveau E[     DRM] failed to create 0x80000080, -22

```

I haven't noticed any problems that I can relate to this message. The numbers in the far left change slightly if I restart, but the rest of the message stays the same. Can anybody tell me if this is indicating some issue with my computer? And if yes, what can I do to solve it?

---

### Post by grahammechanical on 2014-01-01
Nouveau is the open source video driver. So, if anything is happening it is connected with the graphics adapter and the video driver. You could try installing a proprietary video driver. That problem might then go away. System Settings>Software and Updates>Additional Drivers tab. If changing drivers does not get you to a working desktop. Then at the Grub menu select Advance Options for Ubuntu (it is a sub-menu) and then select Recovery mode. At the Recovery menu select Resume. That will try to get you to a desktop using a fall back subset of the Nouveau driver. It that works you can experiment with another driver.

If you get to a desktop but it lacks the top panel and the Launcher, try right clicking the desktop wallpaper and selecting Change Desktop Background. That will open System Settings at the Appearance utility but there will be a button that will fully open System Settings and then you can open Software and Updates.

Such is life in Linux.

Regards.

---

### Post by tfglynn on 2014-01-01
Hours later, my original problem has disappeared. Here's what I've done:
[LIST=1]
[*]Checked [COLOR=#000000]System Settings>Software and Updates>Additional Drivers and got "No additional drivers available," just like [the person here]("http://ubuntuforums.org/showthread.php?t=2189408").[/COLOR]
[*][COLOR=#000000]Sought NVIDIA drivers. Tried to install [this one]("http://www.nvidia.com/download/driverResults.aspx/69372/en-us") but gedit froze.[/COLOR]
[*][COLOR=#000000]Installed Bumblebee after seeing above linked thread.[/COLOR]
[/LIST]
I no longer see the message on startup, so I think installing Bumblebee fixed my initial problem, but I still see no drivers in "Additional Drivers." I tried looking there while in Recovery Mode as well, but still saw nothing. I don't *feel* as though my issue should be solved, but there you have it. Thank you for your help.

---

### Post by Bucky Ball on 2014-01-01
If the error message is gone then the problem originally outlined in this thread is solved. But I know what you're saying.

If everything is running fine and no errors there is no need to install proprietary drivers. The open-source ones are working fine. If you are a heavy gamer you will probably need to hunt down the proprietary drivers, otherwise don't bother. I don't use them myself.

---

