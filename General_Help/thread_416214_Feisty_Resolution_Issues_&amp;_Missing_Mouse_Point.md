---
title: "Feisty Resolution Issues &amp; Missing Mouse Pointer"
date: 2007-04-20
forum: General Help
---

### Post by booljayj on 2007-04-20
Here's the story:

I finally get my Feisty Live CD and am totally ready to smack Windows in the face. So, I pop it in, start it up, and tilt my head curiously. The reason, you ask? The resolution is horribly low. 800x600 to be precise. Not only does it look bad, but all of the windows are simply too big and get cut off at the bottom of the screen. When I go to the screen resolution tool under preferences, I also find that I cannot in fact make it larger than 800x600. That's the max.

Thinking this was simply a graphics card glitch, I did what I did last time I had one: I installed nvidia-glx from synaptic. A quick configure and restart and... tadaa! Glorious 1280x1024 screen resolution! My problem solved, I took my mouse in hand and prepared for a new tomorrow.

But what is this? My mouse is seemingly invisible. Gliding around the top of my screen unseen, it tempts me by triggering the highlights on buttons as it passes over them. Oh cruel fate, you seem to have taken away my ability to enjoy high resolution... Ah well, I'll simply disable and remove nvidia-glx and go sadly back to the hell that is 800x600.

No, no it cannot be! Now I am faced with the horror that is low resolution and an invisible mouse! I let out a howl of agony at my predicament, and retreat into Windows to find some sympathy in the Forums of the Internet...

That being said, anybody have any clues? I don't want to install until I'm sure there's a solution to this problem.

AMD Athlon 64 3500+
Nvidia GeForce 6100
Ubuntu Feisty Fawn 7.04 Live CD

---

### Post by dvord on 2007-04-21
Same thing here.  Common theme?  6000 series nvidia card.  I have a 6600 GT.

I had the same problem when I installed 6.10.  I worked through it, but I cannot remember what I did.  I am pretty certain it's a video card issue.  So that's how I'm going to proceed.

I'm going through the install now, using the old steps I had for 6.10.  I'll show you what I'm about to do and when it's through (or I am) I'll tell you how it went:

(as copied from a long-gone post) [I]It's your lucky day! I just had the same problem and could get little support here, so I figured it out on my own.

First, as others have suggested, use the alternative install CD. This should get the OS installed.

Still, when you try to log in, it will give you the garbled screen. Don't log in yet; instead, hold control and alt and press F1. If this gives you a garbled screen too, reboot and select "Recovery Mode" at the bootloader. Log in in this terminal. Then, type:
Code:
sudo nano /etc/X11/xorg.conf
Scroll down to where it says "Section" "Device". Where it says Driver "nv", change the nv to vesa. Then, hold control and press O then press enter (to save changed) and press control-x (to exit nano).

Now, type this:
Code:
sudo /etc/init.d/gdm restart
You can now login every time without a hassle. However, performance will be very, very bad (it takes a few seconds to scroll down in Firefox). So, we need to install a driver. I have only done this with an NVIDIA card, so MAKE SURE YOU ONLY DO THIS WITH AN NVIDIA CARD. The instructions are here:

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

EDIT: Almost forgot this part.

Also, in addition to these instructions, there is a security hole in the NVidia drivers, unless you're using the beta release. It can compromise your system or (more likely) just restart the X server while you're using Firefox. To fix it, open a terminal and enter:
Code:
sudo gedit /etc/X11/xorg.conf
In the Device section, above the line that says Driver "nvidia" (if you followed the instructions), add this line:
Code:
Option "RenderAccel" "false"
Then log out and press control-alt-backspace.

Enjoy your Edgy-working goodness! If you need help with anything, whether I posted it or it's in the guide, just ask. I'll monitor this topic for a while.[/I]

I wanted 1280X1024 resolution, so I did the following:

	sudo gedit /etc/X11/xorg.conf 
and modified the line for 24 bit color depth to include 1280X1024 line under:

	Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    SubSection     "Display"
        Depth       24
        Modes      "1280X1024" "1024x768" "800x600" "640x480"
    EndSubSection

---

### Post by dvord on 2007-04-21
Well, I'm up and running.

After much pain and anguish, I would urge you to try what I did, go to the System menu, choose the Administration section and click on Restricted  Drivers.  

You should see your Nvidia card there.  If you click the enabled checkbox it will go out and find your restricted driver, load it, and after a reboot, you might find that errant mouse pointer.

Best of luck to you!

---

