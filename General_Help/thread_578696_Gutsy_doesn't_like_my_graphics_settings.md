---
title: "Gutsy doesn't like my graphics settings"
date: 2007-10-17
forum: General Help
---

### Post by Brainy on 2007-10-17
I upgraded yesterday to the last Gutsy RC to beat the rush downloading, but now have a problem.  At first the resolution was fine.  I then tried to enable the visual effects (wanted to test them out) and was told I needed the Nvidia proprietary driver.  Ok, I clicked to install it.

Then the appearance screen froze and I decided to restart.  How stupid of me.

I got the nice message saying my configuration was wrong, so I corrected it and clicked ok.  It still displayed in 800x600.

So when logged in I changed it... It said I needed to log out to see the changes.  Still, when I logged back in it didn't change.

Not whenever I change it, it just reverts back to the "safe" settings.

I don't have a problem mucking with the command line and configuration files, but I have never encountered this type of problem before and have no idea how to get about fixing it.  Any advice?

I have a widescreen LG L196WTQ monitor and a Nvidia graphics card (don't know the exact info on it)

I would like to use the 1440 x 900 resolution like I had before.

Thanks for all help!

---

### Post by digitalhillbilly on 2007-10-17
Could it be just opening your xorg.conf and fixing up your monitor and or screen settings? Check your /var/log/Xorg.0.log to see what errors are printed and it should have a line or two where it senses your display and prints out it's specs - HorizSync; VertRefresh, etc... 

Sry my help is not so clear, I've run into this a few times and each time I have to do a google search for the answer (ubuntu or xorg and lcd i think is what i look for)

dh

---

### Post by Cannaregio on 2007-10-17
Once you have installed and enabled the nvidia restricted drivers,
try the following: 

1) System tools --> Nvidia X server settings --> server display configuration --> change resolution (your new settings here) --> Apply --> Save to x config file

2) console --> glxgears

3) System --> preferences --> appearance --> Visual effects --> extra

If everything now works, check the xorg.conf just in case and MOVE the new resolution settings at the beginning of the line (Subsection display modes).

Restart X and cross your fingers.

Good luck.

---

### Post by Brainy on 2007-10-17
That didn't fix it, but thanks for trying.  I didn't see the "Nvidia X server settings" under the System tools :(

I finally got back to my normal resolution by running "sudo dpkg-reconfigure xserver-xorg" to reconfigure xserver.  I had some problems getting the settings exactly right with the monitor refresh rate using hte medium and advanced mode, but with simple it worked out fine.

Still can't get compiz to behave (in my tinkering I got some effects for about 30 seconds until athe appearance box froze and I was dead in the water again) but I think I'm just going to have to live with it.  It would be nice to have, but isn't necessary.

Thanks to all who helped!

---

### Post by 11touche on 2007-10-17
Same problem here, but different hardware.
I have an Sapphire Radeon 9600XT (ati chipset, of course) with a Viewsonic G-773 and a Sony Multiscan 200sx, in dual-head setup. Everything worked fine under Feisty, but now, it's a mess.
Just like you, everytime I boot, when I desperately try to activate dual-head, it starts in failsafe graphics mode (800x600), no dual-head.
When I get in the new flashy GUI, I just can't activate dual-screen (it's shaded). The only driver I can get a decent resolution is the fglrx open-source driver, but only in mirror setting.
I don't know how to disable the auto-detect feature of Xorg 7.3, but it would help me a lot. I tried to edit my xorg.conf (which I'm pretty good now at), but it looks like it doesn't care about it, and create it's own "failsafe" xorg.conf.
I need to work with "The Gimp" and on a single screen, it's like trying to f*** a fat girl in a Smart. Not enough space for the tools and the picture.
I'm still trying to find a workaround, but help on 7.3 seems to be rare.
Hope someone can help me out with this one :/

---

