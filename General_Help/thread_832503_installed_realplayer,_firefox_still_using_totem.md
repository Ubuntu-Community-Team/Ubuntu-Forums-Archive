---
title: "installed realplayer, firefox still using totem"
date: 2008-06-17
forum: General Help
---

### Post by joekidston on 2008-06-17
Hi all,

I see there's a ton of threads on Firefox/RealPlayer/Totem, but I can't find what i'm looking for.

I have installed RealPlayer, and followed the instructions in [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy) for how to make RealPlayer your default, and all looks good (even the Firefox about:plugins page looks correct)

When I click on a RealPlayer link, it asks me what I want to use to open it, and points to RealPlayer, so click 'OK', but then it still tries to open it with Totem, which of course doesn't work.

I have done the 

******************************************************************
cd /usr/lib/firefox-addons/plugins
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.xpt nphelix.xpt
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.so nphelix.so
  sudo mv /usr/lib/totem/gstreamer/libtotem-complex-plugin.so ~/.
******************************************************************

and 
******************************************************************
Open Firefox and type about:plugins in the address bar. Scroll down and look for the following entry.

  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
  File name: /opt/real/RealPlayer/mozilla/nphelix.so
  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.4005 built with gcc 3.4.3 on Feb 25 2008
******************************************************************

looks correct (although the File name simply says nphelix.so, not the full path.  Is this my problem?

Any help is greatly appreciated
Cheers

---

### Post by RealPSL on 2008-06-17
I would think that you have to change the mime type associations in firefox by doing Edit > Preference > Applications. I had a similar problem playing mp3 audio and reconfigured firefox to use real player by changing the associations in the above window and it works fine.

---

### Post by joekidston on 2008-06-17
Thanks for the reply...

When I look there, it says for RA files, use /opt/RealPlayer/realplayer, which is the correct location for my realplayer, and yet it still opens totem.  WTF?

---

### Post by joekidston on 2008-06-22
Does anyone have any ideas on this?  It's doing my head in - i can't play any .ram files.

When I do manually open RealPlayer, if I try and open e.g. an mp3 file, the application closes immediately after trying to open it (my VLC player does the same - very frustrating).

Maybe Firefox is trying to open RealPlayer, it's failing, and defaulting to Totem?

---

### Post by mainak_sen on 2008-06-26
i am having exactly the same problem as you...
have you got any updates?

---

### Post by manfer on 2008-06-26
> **joekidston said:**
> Thanks for the reply...

When I look there, it says for RA files, use /opt/RealPlayer/realplayer, which is the correct location for my realplayer, and yet it still opens totem.  WTF?

The path is /opt/real/RealPlayer/realplayer (but use /opt/real/RealPlayer/realplayer doesn't work, don't know why). I solved it just chosing there, use other... and looking for it /opt/real/Realplayer/realplayer, That way it works and adds other entry use realplay, that you can use in any other mimeType you need it. I use that for RA files.

For SMIL Multimedia Presentations, use RealPlayer 11 (default) is available, so I use that instead.

---

### Post by drs305 on 2008-06-26
I believe MediaPlayerConnectivity plugin now works in FF3. It allows you to set which media player is used for each format. You would have to click on an icon before it began to play but I don't think I've ever had a system setting override what I set up in MPC. 

This is a workaround and shouldn't be considered a fix to the problem. Assuming you can use Real Player to run files outside FF, it will open RA with Real Player within FF after setting up MPC (to the best of my experience).

---

