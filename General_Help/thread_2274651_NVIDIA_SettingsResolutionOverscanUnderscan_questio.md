---
title: "NVIDIA Settings|Resolution|Overscan/Underscan question"
date: 2015-04-21
forum: General Help
---

### Post by Axxon95 on 2015-04-21
How do I change the mode from "HDMI" to "DVI/PC" on Ubuntu?
I only need 1360x768(native) from my TV but since it has 1080p+Audio I assume the Drivers and GPU are defaulting to using an HDMI mode(1080p), but the TV is not "FullHD" so it causes me some quality issues, overscanning/underscanning/bad font/etc.
On Windows its simple to fix, I can go to the NVIDIA Control Panel and look under "Change resolution" and see a tab with the option to choose a "PC" resolution while still being Digital Video, giving access to standard resolutions(e.g 800x600, 1024x768, 1280x720, 1280x1024 1360/6x768, etc). On Windows that **fixes** my problem. I just need to find the equivalent on Ubuntu/Linux.

GPU: GeForce GT 610 with 331.x NVIDIA drivers.

On this TV, I had the same problem with Ubuntu on my Raspberry Pi 2 but that was as simple as changing the hdmi_mode from CEA(HDMI) to DMT(DVI/PC) and choosing the mode number needed for the screen's native resolution.

Thanks!

Edit 2: These are my main two priorities. My RPi2 is fixed, but I need the equivalent for my steam streaming client.
My GT 610: [https://www.youtube.com/watch?v=S9ephkblgDU](https://www.youtube.com/watch?v=S9ephkblgDU)
My Raspberry Pi 2, with fix: [https://www.youtube.com/watch?v=A0jB2ozkygo](https://www.youtube.com/watch?v=A0jB2ozkygo)

Edit: I'm using the DVI Out on my GPU with an adapter to change it to HDMI so I can plug it into my TV. I only need the Digital Video, not audio. Sadly I don't have a DVI port on my TV for just video.

---

### Post by dino99 on 2015-04-21
Hdmi might be  the first choice  [http://www.cnet.com/news/hdmi-vs-displayport-vs-dvi-vs-vga-which-connection-to-choose/](http://www.cnet.com/news/hdmi-vs-displayport-vs-dvi-vs-vga-which-connection-to-choose/)
HDMI transmits sound as well as video. DVI is used for monitors because its solely for video.
[http://www.diffen.com/difference/DVI_vs_HDMI](http://www.diffen.com/difference/DVI_vs_HDMI)

about nvidia driver, you should move to 346 (xorg-edgers ppa, or archive with vivid)

---

### Post by Axxon95 on 2015-04-21
I'm not having trouble choosing what connection I'm going to use, I should have made that clear sorry.
But I am using it just for video, I have no need of audio from this TV, but I do need Digital Video, and it only has 2 HDMI ports, a DVI port is not an option.
I know the TV can work in just digital video mode(thru HDMI) because my Raspberry Pi 2 running Ubuntu as well is working just fine with 1360x768(DVI mode without Audio).

There's gotta be a setting I can add to my NVIDIA x.conf.

---

### Post by grahammechanical on 2015-04-21
If you are using an Nvidia driver then there will be installed a utility called Nvidia Xserver Settings. See if that does what you want.

But generally speaking if we use HDMI to connect TV to computer then the TV source should be set to HDMI and if we use DVI to make the connection the TV source should be set to DVI and if we use VGA to connect the TV to the computer then the TV source should be set to PC or VGA/PC as it is called on my TV.

I have used a TV as a monitor that had connections for HDMI, DVI and VGA. I am now using a TV that has connections for HDMI and VGA but I have never needed to set the computer to HDMI, DVI or VGA. It is detected automatically.

By the way, there is a Displays utility in System Settings but it is meant for use with an open source video driver. When a proprietary video driver is use this Displays utility is disabled.

Regards.

---

### Post by Axxon95 on 2015-04-21
I've tried using the NVIDIA Settings, but it doesn't help at all really. It only tries to help fix over/underscan.

For computer use, my TV only has 2 HDMI and 1 VGA/RGB port(which I'm not going to default to). It lacks DVI so I'm using the HDMI port, the closest thing I can get. VGA works just fine without issues, even gets the real native resolution(1360x768) but its not Digital.
I also checked my old Radeon 9600 AGP, and NVIDIA FX 5200 AGP cards(with open source drivers and DVI ports) and I'm get the same problem. It puts it in HDMI mode and only gives me interlaced and progressive resolutions for HDMI TV use, such as 640x480i/p 720x480i/p 1280x720i/p 1920x1080i/p, and some "scaled" resolutions that aren't any better and all come with the over/under scanning problems.

I guess when Linux is probing, it sees the TV as HDMI and just defaults to 1080p but I don't want that, due to over/underscan reasons. Its just ugly.

For proprietary or open source drivers, is there any type of setting in KMS or X I can set to choose between what display mode I want? I only want standard resolutions.

I wish this were as simple as the Raspberry Pi config settings. :|                                        

         
     
Thanks.

---

