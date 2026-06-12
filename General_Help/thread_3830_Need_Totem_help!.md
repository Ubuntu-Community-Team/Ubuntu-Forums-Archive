---
title: "Need Totem help!"
date: 2004-11-09
forum: General Help
---

### Post by vaskark on 2004-11-09
I opened Totem after I inserted a dvd into the drive. I went to Movie > Play Disc and got this error:
  
 Totem cannot play this type of media (tmw_aspect_ratio_square_menu_item) because you do not have the appropriate plugins to handle it.
  Please install the necessary plugins and restart Totem to be able to play this media.
  
  Does anyone know what plugins I am missing? Thanks.
  
  [http://www.ubuntuforums.org/images/smilies/eusa_wall.gif]("http://www.ubuntuforums.org/images/smilies/eusa_wall.gif")
  
  -- vaskark

---

### Post by andy_sp1ke on 2004-11-09
If it is the totem that came initially with Ubuntu then it plays nothing at all!! Go in to the synatptic Package Manager and remove Totem- Gstreamer and install Totem-Xine!! 

( Computer menu - System Configuration - Synapitic Package Manager , in the the program that opens click on "Settings" "repositiries" and make sure the universe ones are selected, they should be the two that are not ticked!! Click Apply and then search for totem and mark the totem-gstreamer for removal and mark for installation the Totem-Xine.)

This should give you a proper plugin happy Totem, but get MPlayer to. 

I dont know if this is useful to you or not, but it sounds like it maybe the problem. I got stuck on media playing the other day when I replaced Windows with Ubuntu and that s how I solved it!

Andy

---

### Post by vaskark on 2004-11-10
Thanks for responding. I did what you suggested. After I inserted a dvd Totem automatically began playing it, so I thought everything was fixed. Then it crashed, right after the FBI warning. It keeps crashing at this point. I'll have to so some more investigating ...
  
  -- vaskark

---

### Post by vaskark on 2004-11-10
Here is the output from **totem dvd://** at the CL:
  
  Bonobo accessibility support initialized
  GTK Accessibility Module initialized
  /dev/dsp: No such file or directory
  /dev/dsp: No such file or directory
  /dev/dsp: No such file or directory
  libdvdnav: Using dvdnav version 1-rc5 from [http://xine.sf.net]("http://xine.sf.net")
  libdvdread: Encrypted DVD support unavailable.
  libdvdnav: DVD Title: KILL_BILL_VOL2
  libdvdnav: DVD Serial Number: 30ce7b17
  libdvdnav: DVD Title (Alternative): KILL_BILL_VOL2
  libdvdnav: Unable to find map file '/home/jason/.dvdnav/KILL_BILL_VOL2.map'
  libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4
  libdvdread: Invalid IFO for title 4 (VTS_04_0.IFO).
  libdvdnav: ifoOpenVTSI failed - CRASHING!!!
  libdvdnav: ifoRead_VTS_PTT_SRPT failed - CRASHING!!!
  libdvdnav: ifoRead_PGCIT failed - CRASHING!!!
  libdvdnav: ifoRead_PGCI_UT failed - CRASHING!!!
  libdvdnav: ifoRead_VOBU_ADMAP vtsi failed - CRASHING
  libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
  libdvdnav: *** pgci_ut handle is NULL ***
  Bonobo accessibility support initialized
  GTK Accessibility Module initialized
  /dev/dsp: No such file or directory
  
  Sorry about not posting this in my previous post. Any suggestions?
  
  -- vaskark

---

### Post by andy_sp1ke on 2004-11-10
Ok, I havent had that problem with mine (but i've not played a DVD with totem as i use my Xbox). I will try sticking a DVD in it. Can you play other movies? DiVX, MPEG, AVI etc?

Also have you followed the media instructions on installing MPlayer, it is better than totem. 

I think we might need some more help here! I'm still learning about linux myself I just happened to worked around the Ubuntu install of totem not actually being able to play anything

andy

---

### Post by andy_sp1ke on 2004-11-10
Well my Totem player throughs up and error telling me i am trying to play an encrypted disc with out Libdvdcss. And its just after the FBI warning comes up! MPlayer however will play them so you could install that to see if it plays it. I'm looking into getting TOTEM to play them.

---

### Post by vaskark on 2004-11-11
K, I installed MPlayer, but clicking on it nothing happens. I tried from the command line (gmplayer), and it says that MPlayer ws compiled without GUI support! I need the gui interface. What the heck am I missing?

---

### Post by Julius on 2004-11-11
Have you installed libcss2 (or something like that)
Go to the howto forum and take a look at multimedia howto. 
My GMplayer and Totem-xine can play commercial dvds without a problem :)

---

### Post by vaskark on 2004-11-11
I followed the HOWTO and got MPlayer working fine (the plugin, too). But DVD's still don't work. I get this error:
 
 Cannot open the IFO file for DVD title 4
 
 It's a real bummer. Hopefully I'll figure it out. Totem is still not working, either.
 :(
 
 Thanks for all your help, guys. It makes this a lot easier for this newbie.
 
 -- vaskark

---

