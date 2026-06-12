---
title: "Whats wrong?"
date: 2007-05-12
forum: General Help
---

### Post by Golden Helmet on 2007-05-12
Not 100% sure if this is the right forum. Don't hurt me if it's wrong:( 

Anyways. My problem. I was running Ubuntu 6.10 or whatever that one was, and I upgraded to the latest version through the Synaptic version changer or whatever that was (I'm a newbie, don't hurt me!). Easy as pie.

When I rebooted my system to see what was new though, thats when trouble started. After I selected my OS (I'm dual-booting), my screen simply went blank and my monitor went in to stand-by mode. It did that every time since.

Ok, so I figured something just went corrupt. Today I finally got around to just downloading a fresh ISO and re-installing. I get the same problem though, just this time it's after I select Install.

I tried a few times, then thought to change the resolution. I hit F4 at the selection screen and switched it to 1280x1024, and like a charm, it worked. So I continued on with the install, happy that I would soon be re-united with Linux.

After the install was complete, yep, you guessed it, monitor goes to standby after selecting the OS. Apparently, my resolution didn't stick. It's selecting like 1900-something res I think, not sure exactly but either way, it's something my monitor can't handle.

Any suggestions on how to fix this? I'm almost a complete newbie and I've fallen in love with Ubuntu especially for it's ease of use. For what it's worth, this is what I'm using:

Monitor: Rosewill 17-inch LCD, 8ms response time I think. Can't remember the exact model number.
Videocard: Sapphire ATI Radeon X800 GTO 256mb AGP
CPU: Athlon 64 3400+ @ stock 2.4ghz
Motherboard: Asus K8N-E Deluxe, Nvidia nForce 250gb the chipset should be.
RAM: 1.5gb

If this is the wrong forum or this problem was already addressed before and I missed it, I apologize. Don't flame me too hard :P

---

### Post by Nythain on 2007-05-12
my guess would be the resolution grub is setting/using
sudo nano /boot/grub/menu.lst
add vga=792 after quiet splash
if that doesnt fix it, and you dont mind not having a splash screen, i would try deleting quiet and splash
that will remove the splash screen and have it load verbosely

---

### Post by bapoumba on 2007-05-12
Moved to "General Help".
Have you tried reconfiguring your X settings?

Hit CTRL-ALT-F2. You get to a non graphical session. Login.

Run:
```
sudo dpkg-reconfigure xserver-xorg
```
Keep the default answers when you do not know.
To select an item (like screen resolution for ex), use <space> to inset a * in the resolutions you want to select.

CTRL-ALT-F7 to go back to graphical session.
CTRL-ALT-Backspace to restart X

(or **sudo reboot **from the non graphical session).

---

### Post by Golden Helmet on 2007-05-13
Thanks for the replies. I tried the second suggestion (couldn't try the first because I couldn't edit the right file from the LiveCD, no idea how to edit stuff through the command line), and I'm still having the same problem. I get to the OS selection window fine, but after selecting Ubuntu, thats when my screen goes blank and monitor goes in to standby.

I was able to boot in to Ubuntu through the safe mode thing (or whatever that was called), thats where I ran the xserver-xorg reconfigure thing via command line. It, by default, had nothing above 1024x768 selected, so I left it at that. Should work fine, weird =\

May just have to use the old version of Ubuntu (which, of course, is great, but I like new stuff :p ), unless you guys have anything else I could try?

---

### Post by bapoumba on 2007-05-13
> **Golden Helmet said:**
> 
I was able to boot in to Ubuntu through the safe mode thing (or whatever that was called), thats where I ran the xserver-xorg reconfigure thing via command line. It, by default, had nothing above 1024x768 selected, so I left it at that. Should work fine, weird =\

I do not know much about video, but what's your hardware? What video driver are  you using? If using a proprietary one, you can try using vesa driver in the mean time. That should allow to boot up in a graphical session, no 3D, not best resolution, but start working from there.

---

### Post by Golden Helmet on 2007-05-13
I'm using a Sapphire Radeon X800 GTO. I don't have any drivers for it installed, since I can't even get to the log in screen. I'll try using vesa when I re-install later though.

---

### Post by RedSquirrel on 2007-05-14
There are issues with ATI X*** cards it seems. Try this guide:

[Installing Ubuntu 7.04 (Feisty Fawn) on machine with ATI X**** series video cards]("http://ubuntuforums.org/showthread.php?t=414194")

It's a sticky at the top of Absolute Beginner Talk forum. :)

---

### Post by Golden Helmet on 2007-05-14
Alright, quick update. I actually got it working! YAY!

Found out how to edit the boot thing from the OS selection. I did the first suggestion, removing the quiet and splash things. I reconfigured xserver, using the ati driver choice (vesa didn't work), and it worked fine from then on out. Except for...

Yes, there was one more little problem. Why me, why? My internet refused to work. I copied the settings directly from my Windows install, and they refused to work (automatic config didn't work either). The exact same settings I'm using right now of my Ubuntu 6.10 install (just got it up a few minutes ago).

I'm giving up on Ubuntu 7.04. Fix one problem, another pops up, and then with my luck, two more will take that one's place. Ubuntu 6.10 works great and I'm enjoying it, so not much of a loss anyways. Fingers crossed for the next version! :( 

Thanks for the help guys, much appreciated. I'll be sure to pester you guys the next time I screw something up (back in 10 mins! :p )

---

