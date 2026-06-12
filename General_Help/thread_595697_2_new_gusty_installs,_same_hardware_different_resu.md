---
title: "2 new gusty installs, same hardware different results."
date: 2007-10-29
forum: General Help
---

### Post by rwap on 2007-10-29
I have just upgraded 2 pc's to gusty, both pc's have the same hardware, as follows

MSI K9A Motherboard
ATI X1950 With Cross Fire
2GB DDR RAM
AMD X2 5200+ CPU
Onboard sound + Sound blaster

The only different hardware is the monitor,

one is a new acer x221W 22' wide screen, and the other is a KDS 19' CRT

That said, I installed gusty on the pc with wide screen and all works fairly flawless, except the resolution cant be set higher than 1280x1024 @ 76Hz and the sound sometimes doesn't  work and i have to reboot to get it to work, and of course the new 3d effects do not work at all with the same old "Desktop Effects could not be enabled" error- Gee that's descriptive- 

The only thing annoying me right now is the screen resolution on this one, some things are stretched because wrong resolution, i need 1680x1050 how do I fix that? 

The other machine, again identical, except monitor, on fresh install doesn't display correctly just continuously turning on and off and switching between text mode and gfx mode, eventually showing a gray and blue screen saying something about xorg server has rebooted 6 times in 90 seconds and something is wrong-Gee I would have never guessed- all of that happens until i unplug the monitor and plug it back in, when i unplug it ubuntu boots-I hear it- and i plug back in and works just fine.- This is getting old FAST.

also, dont know if it makes difference or not, I have to use DVI for output since my x1900's dont have a VGA.

I tried installing ATI drivers and i had the same problem as many, the gui locked up on boot.

looking forward to responses.

Thanks.

BTW- Please explain any fixes in detail i am a life long windows user, so installing stuff and navigating through folders in linux is really difficult right now-for the most part- I really like the .deb's-why cant they all be like this? Thanks!

---

### Post by rwap on 2007-10-29
I have my Wide screen pc's resolution fixed partially, i opened xorg.conf and removed all the resolution entries except 1680x1050 and it boosted the resolution to 1680x1200 so its allot better but things are hard to read... I have been trying desperately to get the ati drivers to install, i found envy and tried that on this one and it didn't work, it locked up like the old driver.

The good news is that the pc with the KDS monitor is 100% fixed but i dont know why,  i used envy on it and it not only worked but fixed the problem with having to unplug it and plug back in... Strange...

Any ideas why?

also i haven't been able to enable the 3d effects on either pc, I still cannot on the wide screen but after installing and running envy, changing the Composite entry in xorg.conf to Enable and installing xgl it works on the KDS pc... It it sluggish though.

Any ideas?

Thanks!

---

### Post by rwap on 2007-10-30
is un-installation of the old ati driver somehow necessary?

The only thing i can think of is that maybe i have something left over on my pc from the old driver... Following the instructions, I did remove some kind of fgrlx file from a ATI folder, ( whatever the thing said to remove i removed it.) but im thinking thats the file for the driver that ships with ubuntu, which BTW wasn't any good either, Not the one that i installed myself from ATI's site that like many others ended in a black world of nothingness.

Any ideas?

---

