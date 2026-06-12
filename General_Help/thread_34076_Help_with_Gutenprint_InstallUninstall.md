---
title: "Help with Gutenprint Install/Uninstall"
date: 2005-05-13
forum: General Help
---

### Post by SteveF on 2005-05-13
I'm not sure which is th ebest forum to place a message like this (seemed like either here, desktop or install).  Anyway...

I'm looking for some help/direction/pointers on a problem I'm having with gutenprint.  I haven't compiled and installed before so take this note as from someone who decided to jump in without really knowing what they were doing.

So far, I've been happy with my output from my printer in all areas except for photographs.  They come out too dark.  I read on the gimp-print site that this is a known issue with Epson printers and that they improved this starting with v5.  They have since renamed the package to gutenprint.  I decided to see if the prints would be better and downloaded the source.  I saw they had a build script for Debian, but I was hesitant to use it since it referenced Woody and Potato.  I was concerned these might be too old, so I went what I thought to be the safer route and did a configure, make, make install.

I installed the packages it said it needed to compile and I ran the following:
./configure --with-cups --with-gimp2
make
sudo make install
/etc/init.d/cupsys restart

I didn't notice any errors during this process.  When I went into gnome printer setup, I added a second printer using the new Epson drivers (I figured I would keep the old printer and just use the new drivers for photos, so I could configure it that way).

I went into GIMP and tried printing.  I only saw one printer displayed (instead of the two I was expecting).  I selected the one printer and chose setup printer.  From here I was able to select the new driver (quality of output will still need to be tested because my printer at that point chose to run out of ink - I htought I could squeeze out a couple of more tests - wrong).

Just to see what my options were (since I print photos from Wine also), I loaded my printing app under Wine and looked for the new printer. It also only showed the original printer.  I tried clearing out the print information from system.reg and win.ini and restarted the app.  System.reg showed both printers, but win.ini (and therefore the printer dialog) only showed the first printer (using the older drivers).

I decided that maybe CUPS had issues with having 2 printers on the same port.  So I deleted both printers and added one with only the new driver.  The Gimp showed this one printer (I had to setup printer and choose the driver again), but now the Wine app acts as if there are no printers.

Now to my questions:
1) Anyone have any idea how to get Wine to see the new printer?
2) If I decide to remove gutenprint, where do I look to find out where the files got installed and can I just delete them?  I noticed that the make file had an uninstall option, would that remove the files?
3) If I delete the files, will that leave my printing in a partially installed state (possibly gutenprint overwrote files)?  And if so, how do I recover back to the way printing was set up when I first installed Ubuntu?  Will I need to uninstall and then install all packages related to printing?
4) Would I have been better off doing a "make deb" to do the Debian build?  Would that have been easier to unintall?

Thanks for any help/direction someone can provide.  Hopefully by the time I get this post answered I'll have some new ink and will be able to see if the printing is better.

Steve

---

