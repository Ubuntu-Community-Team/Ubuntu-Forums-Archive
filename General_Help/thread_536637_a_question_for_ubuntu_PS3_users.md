---
title: "a question for ubuntu PS3 users"
date: 2007-08-28
forum: General Help
---

### Post by speedingbullet on 2007-08-28
I just have a simple question, how is it working out for you?

You see, I was never really intending to get a ps3 since I thought you could only install yellow dog Linux on it, plus I have a 360 and a Wii.

Why I want to do this, is because my home computer is good and all... but its very outdated, even though its a year old. I wouldn't be too concerned about it if I didn't want to install guild wars on my Linux box. I would love to simply update the graphics card, but it wouldnt entirely matter, because my processor is 2.53 GHZ celeron, plus my computer has no PCI express or AGP support.

I was seriously considering using that king kong exploit, and buying another hard drive so I could get my 360 running Linux, but it looked too risky, it looked illegal, and when I checked, the 360 uses ATI graphics.

Since sony seems fine with people using another OS on their system, so im considering buying a ps3 so I wont have as much of a problem playing computer games on wine (like halo and guild wars), not to mention being able to be more productive.

So how is it working out for you? Can you emulate computer games that have been proven to emulate on wine without a problem? Or do the Graphics perform horribly?

It would make more sense if I just made a custom build, but something tells me I'll end up buying a ps3 sooner or later, plus one of my friends wants to know how to do it (Im much more experienced at this stuff than he is)

---

### Post by Ribs on 2007-08-30
Feisty installs okay, but needs some work to properly use all the PS3 hardware. A custom kernel is avalible from psubuntu.com

There are, however, two major problems with the PS3 under Linux:

1) Lack of memory.
The PS3 comes with "only" 256mb of system memory. This cannot be upgraded. I've heard it's *possible* to use the other 256mb on the graphics system. But it's only theory, I'm not aware of anyone being able to do this. And it would be pretty slow memory anyway. I can use xubuntu without too much hassle here. It's not a fast system, but it's not too slow.

2) No access to the RSX chip.
The PS3 comes with a nice powerfull graphics chip from nVidia. This is called the RSX chip. However, Linux is running under a hypervisor in the console, and the hypervisor blocks access to the RSX chip. This means you get no 3D, or even 2D, acceleration of any kind. You are actually forced to use the framebuffer driver in x.org. This make things like turning the PS3 into a nice mythtv box pretty damned tricky. It's stuggles with SD video, anything higher is simply un-watchable right now.

There are some clever people using the SPUs inside the PS3 to do colour conversation, and I've heard that they have managed to get the PS3 to play full HD content at HD resolutions without frameskipping or stutter. But these patches are very much in a pre-alpha state right now. I was able to compile them into my mythtv system, but was not able to get any video from them.

Don't think for a second you're going to be able to play any 3D games in the Linux install. That's the main reason Sony blocked access in the first place.

Other minor problems:
You are forced to use these video modes, and these modes only:
480p
720p
1080i
1080p
VESA (whatever that means)
WXGA
SXGA
WUXGA
Anything else, you can forget. Oh, and make sure your monitor/TV support HDCP if you're planning on using HDMI, otherwise you won't see too much (so I've been told, not experienced this myself as my monitor is new, thankfully).

Yellow Dog supports a lot out of the box, but I found it to be a awfull and unusable distro. A very limited package selection, along with very outdated (and I'm thinking very insecure) software. They could never get everything right. The kernel update would fix wifi support, but then break joypad support, then the boot-game-os command would be broken. Given Terrasoft are pretty much relying on the PS3 to stay afloat right now, it's not a very impressive effort.

Linux support is still very new. This really is for the testers and tweakers right now. Things will improve, I have no doubt. This time next year, the kernel will support pretty much everything out of the box without patching, mythtv will have patches in the SVN at least to give me smooth playback, and I'll be moaning that everyone has it easy.

Having said that, I have a nice set-up running MythTV (addmittedly in a small window in the middle of the desktop) which I can also use to launch snes9x, which plays retro games very nicely. Using a custom kernel, I can use the joypad to navigate mythtv and play my games. I've been told mame and UAE work well as well. When not using Linux, I managed to get my mythtv backend to share it's video with the PS3 "game OS", and that works really well. I even wrote a guide: [http://www.mythtv.org/wiki/index.php/PS3_GameOS](http://www.mythtv.org/wiki/index.php/PS3_GameOS)

If you want to buy a PS3, buy it for the right reason, and that's to play games. Don't buy it for a nice Linux experience. At least, not yet.

I wouldn't bother going the XBox 360 route. Support for that hardware is never going to be big unless a uncloseable exploit is found and a lot of people start using it. Support on the PS3 is much better right now, and I can't see that changing unless MS openly allow you to run another OS on the system (and we all know how likely that is)

---

