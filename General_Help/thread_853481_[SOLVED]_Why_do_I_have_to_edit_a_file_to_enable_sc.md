---
title: "[SOLVED] Why do I have to edit a file to enable screen rotation in 2008?"
date: 2008-07-08
forum: General Help
---

### Post by foxmajik on 2008-07-08
Xorg has supported hardware rotation with nvidia drivers since 2004.

Why do I still have to hand edit the xorg.conf file to enable it, as below, if there's an option for it on the resolution preferences dialog?

Why is the option presented only to be grayed out?

Can't there be a checkbox on the same window that says "check this box to allow modification of the xorg config file needed to enable this feature?"

---
    * To enable rotation support find the "Device" section for the "nvidia" driver in the /etc/X11/xorg.conf file: 

Section "Device"                                                               
      Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
      Driver          "nvidia"

    * Add the following option to this section: 

       Option          "RandRRotation" "on"

    * Then the display can be rotated (direction depends on the orientation of the monitor) by: 

   1. Setting the "Rotation" property to either "Left" or "Right" in the "System > Preferences > Screen Resolution" dialog.
   2. Issuing either "xrandr -o left" or "xrandr -o right" command.

---

### Post by 16777216 on 2008-07-08
[RANT]
I hate to say it, *but*,.. go gripe at nVidia about it. I did, and that is the only way they will fix it as the Ubuntu team cannot do much about it.
Now I must apologize for sounding like a smart ***, that was not my intention. 
Truthfully we *all* need to gripe at nVidia about a lot more than this. Even if they don't open up the drivers they at least need to "up the feature parity" with the Windows drivers.
Although I understand that open drivers are the best choice and why, I don't mind non-open drivers as long as the devs are quick to respond to and hopefully fix both the users and OS dev complaints and problems.
Again, I am sorry if I offend.
[/RANT]

---

### Post by starcannon on 2008-07-08
Hardware Manufactures need to hear from more of us.
There is a notion out there that we the linux community encompass maybe 10 individuals (okay I'm exaggerating the misconception) the point is, there are a lot of us out here that our hardware people don't know about.

We need a million penguin march :)

---

### Post by foxmajik on 2008-07-09
I don't see how complaining to nvidia would be productive when the solution is to add a couple of lines to the xorg config file.

I could do this with a one-line perl script so I don't see how it would be hard to do this during Ubuntu upgrade or installation.  All you'd have to do is check if the nvidia driver is being used and if so add the lines to the config file.

---

### Post by 16777216 on 2008-07-09
> I don't see how complaining to nvidia would be productive when the solution is to add a couple of lines to the xorg config file.But then you have two tools doing what one needs to do.
I thought you meant that nvidia-settings needs to have an enable rotation check box in it.
But yeah, putting rotation on by default is kinda easy.
Although, it might break X or have the desktop up-side down on some monitors. :confused: :)

---

### Post by foxmajik on 2008-07-09
> **16777216 said:**
> But then you have two tools doing what one needs to do.
I thought you meant that nvidia-settings needs to have an enable rotation check box in it.
But yeah, putting rotation on by default is kinda easy.
Although, it might break X or have the desktop up-side down on some monitors. :confused: :)

There's no way that enabling this line in xorg conf file can possibly cause a problem because it defines an option that is universally supported by all nvidia devices.

It would be like saying you shouldn't enable hardware acceleration by default, because it might cause a problem.  Sure it might cause a problem.  Having rearview mirrors on your car might cause a problem, too.  But you still get them.

---

### Post by 16777216 on 2008-07-09
I meant possibly with some *monitors *not the graphics cards.
But I don't know even if this is an issue.
And I don't disagree with you in the way you said to implement it, it sounds like a good and easy solution with very little chance of error. 
Aw, hell! I don't know. Yeah!, stupid no rotation by default @%$#&*!:lolflag:

---

### Post by foxmajik on 2008-07-10
Related post with the fix for this problem in Hardy:

[http://ubuntuforums.org/showthread.php?t=682821](http://ubuntuforums.org/showthread.php?t=682821)

---

