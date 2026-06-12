---
title: "Off-center bootsplash in Edgy..."
date: 2006-11-21
forum: General Help
---

### Post by Donshyoku on 2006-11-21
Quick problem...

My bootsplash is off center!  The Ubuntu logo and the status bar are off from each other by about two inches.  The image overflows to the right edge of the screen.  This is on my laptop, however, which is widescreen.

Anyone else having this problem?  Is there a quick fix?

Thanks in advance.

---

### Post by Donshyoku on 2006-11-22
I've also tried changing the bootsplash both through the terminal using the alternatives update, and even the graphical switcher... but neither worked.  I get a brief text update and then it goes to GDM.

Any ideas?

---

### Post by Jimmy_r on 2006-11-23
You may want to try SUM(in my signature) to play around with resolutions and see if that helps.

Otherwise, post your /etc/usplash.conf and /boot/grub/menu.lst

---

### Post by Donshyoku on 2006-11-23
> **Jimmy_r said:**
> You may want to try SUM(in my signature) to play around with resolutions and see if that helps.

Otherwise, post your /etc/usplash.conf and /boot/grub/menu.lst

Trying now. It seems like a nice little tool.

---

### Post by Donshyoku on 2006-11-23
Sum won't launch.  The terminal just sits and blinks at me after entering the command.

---

### Post by Jimmy_r on 2006-11-23
Hm. Lets see if I get this right:
You installed sum_0.9-2_all.deb
Nothing happened when launching it from System->Administration->StartUp-Manager
You went to a terminal and tried 
```
gksu -k /usr/bin/startup-manager.py
```
and only got a blinking cursor
Is that correct?

---

### Post by Jimmy_r on 2006-12-03
Hm, that is odd. I have installed 64-bit feisty in vmware player.
Trying to launch SUM gives those same problems(only a blinking cursor).
That is when invoking it with gksu -k, gksudo, or just plain sudo.
But when invoking it with startup-manager.py it launches instantly.
Can you try it? Open a terminal and type
```
startup-manager.py
```
and see if it starts. It will not be able to edit anything ofcourse...

---

### Post by StarQuake on 2006-12-09
This is what I did:
[LIST=1]
[*]Make sure /etc/usplash.conf contains the right resolution by running:
  ```
sudo nano -w /etc/usplash.conf
```
[*]Rebuild the initrd image
  ```
sudo dpkg-reconfigure usplash-theme-ubuntu
```
[/LIST]
Please reply if it helped you too.

---

### Post by maruchan on 2007-01-08
Thanks, StarQuake! Let me describe what I did to fix my off-center bootsplash.

First, my monitor is a Dell 2407FPW. After switching to this monitor, I found that my bootsplash was quite messed up. Someone suggested adding "vga=791" to my /boot/grub/menu.lst entry for the kernel in question. I did that. Now I had a bootsplash with great resolution but terribly off-center.

After looking at your post I tried:

```
sudo nano -w /etc/usplash.conf
```

...and I found that it was set to 1600x1200! I thought, hm, this monitor can do 1920x1200, let's try that. So I changed the numbers and did this:

```
sudo dpkg-reconfigure usplash-theme-ubuntu
```

Then I rebooted. That resulted in a bootsplash that wrapped around the screen, and was huge. Wrong numbers.

Next I changed the numbers in usplash.conf to 1024x768, thinking a lower resolution would do it. Perfect! That solved the centering problem. Screen resolution left something to be desired though, so I looked here:

[http://ubuntuforums.org/showthread.php?t=41709](http://ubuntuforums.org/showthread.php?t=41709)

At the end of the first post there, there is a chart of the VGA code table. I learned that the highest resolution is 1280x1024 (can it go higher even? I don't know).

So, I changed the usplash.conf numbers to 1280 and 1024 for X and Y, and changed my /boot/grub/menu.lst VGA=791 setting to VGA=794.

Great! Now I've got a nice clean splash that's centered at a good resolution.

Thanks again for your post! Glad I found it.

---

### Post by StarQuake on 2007-01-09
Great to hear it helped you! You can find more framebuffer modes here:
[http://tldp.org/HOWTO/Framebuffer-HOWTO-5.html#ss5.3](http://tldp.org/HOWTO/Framebuffer-HOWTO-5.html#ss5.3)
But the max seems to be 1600x1200

The number used there are hexadecimal. In example, to get 1024x768 you can use hexadecimal vga=0x317 or use decimal vga=791.

And if it doesn't work you can always swap monitors ;)

---

### Post by maruchan on 2007-01-09
Cool, thanks - I will be sure to try 1600x1200 for an even *smaller* bootsplash ;) (yay, excited)

---

### Post by maruchan on 2007-01-09
Question: is there a way to apply the VGA mode by default, rather than applying "vga=798" to each kernel entry in menu.lst?

---

### Post by bartman on 2007-01-24
To fix this off centre usplash I left the native resolution of my LCD in /etc/usplash.conf as it was (1920x1200) and deleted vga=794 kernel argument from menu.lst. Now usplash is dead centre but it lacks colour depth. I looks like 256 colours only.

I have yet to find a way to incresae the color depth.

EDIT: Seems that a kernel recompile might be needed for 24-bit colour depth. :S
Suggested here: [ Anyone getting a crappy 16 color usplash screen?]("http://www.ubuntuforums.org/showthread.php?t=285519")

---

