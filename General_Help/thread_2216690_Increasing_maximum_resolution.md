---
title: "Increasing maximum resolution"
date: 2014-04-13
forum: General Help
---

### Post by thomasch-f on 2014-04-13
Hi. This is my first post on these forums, so sorry if this is a bad location for this thread or there's another problem.  And sorry if I'm a little hard to understand in this post. :)

I recently switched to Ubuntu 13.10 after my computer didn't take too kindly to Linux Mint 16. There was a problem with the driver for my AMD HD Radeon 7770, and for whatever reason I couldn't get a resolution above 1024x768, nor play any games as games were missing textures. I know my monitor is capable of resolutions above 1920x1080 because of my experience with Windows 7. I tried numerous fixes online, and tried to swap out the driver for a proprietary one, but that just lead to all sorts of other problems that I won't go into. I switched to Ubuntu just on the offchance that things would be better, and for some reason Ubuntu has been far happier with a new driver, increasing the resolution to 1600x1200, and making games playable :D. 

I'd still rather like 1920x1080 though. I've looked into AMD Catalyst Control Centre and it states a maximum resolution of 1600x1200 there, and won't let me edit it, even with administrator privaleges. I've also tried the following code (along with numerous variations based on different links online):
 ```
cvt 1920 1080
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode CRT1 1920x1080_60.00
```
but every time the Terminal comes back with:

'X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  141 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  49
  Current serial number in output stream:  50'

Does anyone know how I can raise the resolution through the Catalyst Control Centre or through any other code? The driver I'm using is '4.2.12337 Compatibility Profile Context 13.101' according to Steam :S. The code worked with the X.Org driver from before, so I think it might have something to do with the current driver.

Anyway, if anyone has any ideas and could help, please do. :)

---

### Post by thomasch-f on 2014-04-13
Without meaning to post too much, I've also been suffering from a couple of glitches that I can't really find a solution to. The first one means that whenever I try to create a desktop shortcut, I get a message saying 'There was an error getting information about &#8220;/&#8221;.' and 'The specified location is not supported'. Seoondly some of my keys are a little messed up, for example to create an '@', I have to press Shift+2, which contrasts from my keyboard layout. Thirdly, and this is a bit picky I know, is that whenever I open 'Appearance' in the settings menu, the position of the 'Show Desktop' icon changes. These aren't really big problems but I'd like to put them out there anyway in case someone can help :)

---

### Post by thomasch-f on 2014-04-17
Can anyone help?

I'm still having trouble. I've tried the recommended X.Org driver again, and the fix above with xrandr and the Terminal only works temporarily. After that everything reverts after a restart with an error message that extends beyond the screen. I would post it now but since having tried switch back to the proprietary driver every time I log in my screen goes black. The message mentions something about being unable to apply the settings, despite the fact that I did edit the xorg.conf file as recommended here. [http://community.linuxmint.com/tutorial/view/877](http://community.linuxmint.com/tutorial/view/877)

If anyone has any advice, I'd be grateful if they'd say :)

---

### Post by thomasch-f on 2014-04-18
I've just updated to Ubuntu 14.04 but there's still no change. I've heard that installing Ubuntu 12.04 might help for some reason, but I really don't want to have install it considering there are much newer versions. At the risk of sounding a little impatient, I could really use some advice if anyone has any ideas. :)

---

