---
title: "More Ubuntu/Mythtv guides  PVR-350 this time"
date: 2005-05-04
forum: General Help
---

### Post by Jon K on 2005-05-04
I've seen the guides from both Scholzie and Windexh8er.

Fantastic!

But I have a pvr-350 -- (which has it's own MPEG-2 out)

I'd like to provide some additional info for these two guides.  Perhaps we could collaborate

OK, so State of the Nation:

From scratch I've installed a backend server on Hoary Hedgehog with a PVR-350 

compiled and installed IVTV
installed mythtv
modified the mythconverge MySql database to be visible outside of localhost

installed mythtv on a second computer using an nvidia fx5200 for the svideo out
(thanks Schlolize)  (have a working frontend)

At this point, on the backend I had the tuner displaying tv channles on the pvr-350 out by setting an option in mythtv, but did not have the X server display on the TV screen.  

I made all kinds of modifications to the Xorg.conf file with no luck.   

All it took was a single command to install the correct driver for the X server.

install -c -m 0444 ... from the README.X11 file.  
  
The problem I had is that the README.X11 for the latest, stable version of the IVTV driver is NOT in the /docs directory!  it's in the /utils directory.  So I spent two days wasting time before I noticed the /utlis directory had some ore README files  

Once I found this I modifed the xorg.conf file and installed the ivtvdev driver for the X server and the pvr-350.  (the X display ibleeds over the edges of my TV slightly, but I've seen other posts on this issue, and it should be easily corrected).  The TV picture does not appear to do this. 

All works. 

What remains: 

lirc for the remote that came with the pvr-350 (or I'd love to prgram the system to run off of the remote from my (quickly obseleting) tivo. 

Scholzie and Windexh8er: you promised guides.  I have not even tried to install this yet, so have no idea what issues I may encounter.  

automatic startup for the mythtvbackend (and frontend)

Ultimately, I'd like these to be remote driven systems with no keyboards, or mice.  That boot directly into the mythtv screen

Multiple tuners.   (the pcHDTV hd card or the px-tv402u USB device with an mpeg 4 encoder.  

installing mythtv plugins

---

