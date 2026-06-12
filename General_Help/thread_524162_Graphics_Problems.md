---
title: "Graphics Problems"
date: 2007-08-12
forum: General Help
---

### Post by Latis on 2007-08-12
I'm having trouble. For the past few months I've been trying to get Wubi to work, and have been running into graphics problems.

First off, I'm new to Linux, so I made a LiveCD of Ubuntu to try it out. When I boot it up, it was the same problem as I had now, so I booted into Graphics Safe mode.

Now that I have Wubi installed, I have no Graphics Safe mode. So it boots up normally, and when the boot screen is finally done, it comes up with an odd looking screen with purple and green colors of the Ubuntu/Kubuntu logos (whichever one I try to use, currently Kubuntu).

It used to be, when I was on Ubuntu, I could semi-see things for about 15-20 seconds before it totally froze, now I can't at all. Some icons at the bottoms is all I see, and my mouse is a huge green and purple square, much like it was when I started windows and it was in the wrong resolution.

So, I researched online and tried several suggestions of editing xorg.conf, but the problem is, I can't even get to that because it freezes up so fast.

My video card is an old NVIDIA GeForce 6600 GT.
My current resolution in Windows XP Pro/SP2 is 1280x1024, 32 bit color quality.

I prefer not to upgrade my video card at this point. So, is there a way around this?

---

### Post by Latis on 2007-08-13
Update:

I pressed Ctrl + Alt + Backspace after the boot screen fininished, typed

sudo nano /etc/X11/xorg.conf

Went all the way to the bottom and changed the driver line from "nv" to "nVidia". Saved it and rebooted.

Here's the new problem: I'm unable to Ctrl + alt + backspace. I tried lots of times. It boots up like normal, after the loading screen it flashes the consul for a moment, shows the loading screen splash without any bar progress, then it gives me a blank screen with a flashing cursor. I can type whatever I want in there, and usually a Ctrl + alt + backspace gives me ]]^H or something. I press the power off on my keyboard, and Ubuntu acts like it's closing down, and turns off normally.

---

### Post by ago on 2007-08-13
(Ctrl) + Alt+F2  should give you a console, if that is what you are after.

---

### Post by Latis on 2007-08-13
Okay, it did bring up the console.

I made changes by deleting all other resolutions than my own in

/etc/X11/xorg.conf

then I saved and rebooted. It still shows the splash screen booting up, and after it's done, it shows a blank splash screen, then it gives me a screen with a flishing cursor _ and allows me to type. 

I still can't see kubuntu/my desktop environment because of this screen.

Any help?

---

### Post by ago on 2007-08-13
do you mean you get a graphic console? Can you type commands in there?

---

### Post by Latis on 2007-08-13
Nope. I can type things, press enter, but all it does is bring me to the next line.

EDIT: I thought I'd try to give you more information to see if it helps.

1.) Power on
2.) Grubselect -> Ubuntu
3.) Starts to load the boot splash screen for Kubuntu. Takes only a second or two.
4.) Boot splash screen loaded. Start loading Kubuntu kernel, blue progress bar slowly fills.
5.) Once filled, the screen goes blank for a quick second, and shows a second Kubuntu loading/booting splash screen. This time with no progress bar being filled.
6.) Screen goes blank, and shows a console for logging in for 1/4th a second
7.) Brings me to a new blank screen with a flashing underscore cursor. It allows me to type, press enter, etc., but all it does is bring me to the next line. The only thing I can do with it is press Ctrl +alt+F2, or type random words and press enter a bunch of times for entertainment.

---

### Post by Latis on 2007-08-13
I changed the driver to vesa and it boots up normally.

---

### Post by Exocer on 2007-11-10
Hi, im having the same exact problem, with the same exact video card. How does one go about changing their driver to Vesa?

---

### Post by antimatter15 on 2007-11-10
you can then try to download the newest nvidia drivers from the nvidia site (not from restricted-manager)

---

