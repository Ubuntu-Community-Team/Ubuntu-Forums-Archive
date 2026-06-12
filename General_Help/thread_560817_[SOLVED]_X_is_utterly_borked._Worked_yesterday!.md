---
title: "[SOLVED] X is utterly borked. Worked yesterday!"
date: 2007-09-26
forum: General Help
---

### Post by hoborocket on 2007-09-26
Backstory: Today I was given a "broken" LCD monitor. I brought it home and tried to get it working with my laptop. The errors it gave and a google search led me to mess with my refresh rate in xorg.conf. I was dumb and didn't back it up first, yeah. So I doofed with it, and restarted X. I got the "Cannot start X" error. I got it to start by dpkg-reconfigure, but it refuses to use any resolution higher than 1024x768. Previously I ran 1600x1200. Now, depending on how I configure it with dpkg, it does one of two things:

Runs in 1024x768 the whole time, and works fine.
Runs 1600x1200 perfectly in the login window, but once I log in, it goes to 1024x768 and looks like this: [http://www.genericus.org/b/screenerr.jpg](http://www.genericus.org/b/screenerr.jpg)

If I select fglrx in dpkg, it gives me the x cannot start error. If I select vesa, it does the above. As I said, it worked perfectly before I started messing with it. How do I get it to work right again? x.x

When I installed originally off the Feisty CD, everything worked fine. I could get full resolution even without the right video drivers. I thought dpkg-reconfigure did the same thing as the original install, but it seems that it doesn't.

---

### Post by por100pre1 on 2007-09-26
Try [this]("http://ubuntuforums.org/showthread.php?t=83973"). Hope it helps. :)

---

### Post by Clay_Banger on 2007-09-26
> **hoborocket said:**
> I thought dpkg-reconfigure did the same thing as the original install, but it seems that it doesn't.

it should.. you may have put incorrect info in somewhere. could you please post your xorg.conf?

---

### Post by hoborocket on 2007-09-26
[http://extraball.sunsite.dk/notepad.php?ID=481720](http://extraball.sunsite.dk/notepad.php?ID=481720)

---

### Post by hoborocket on 2007-09-26
Bump. I still dunno what to do with this x.x

---

### Post by muralpennies on 2007-09-26
You don't have any 1600x1200 entries in your xorg.conf file, so you can add it manually (edit the xorg.conf file) and see if that helps.

Change these lines: **Modes        "1024x768" "800x600" "640x480"**

To these lines: **Modes        "1600x1200" "1024x768" "800x600" "640x480"**


Also verify that the horizontal and vertical frequencies listed below match the specs of your monitor and change them if they're not correct.

[B]HorizSync    28-51
VertRefresh    43-60[/B]

---

### Post by DagMan on 2007-09-26
another thing to try is booting back into the live CD and copying the xorg.conf file it writes in RAM to the hard drive and test it out.

---

### Post by hoborocket on 2007-09-26
I'll try that, thanks!

---

### Post by hoborocket on 2007-09-27
OK, I did that, and it works, but my restricted video drivers aren't working. It's not the generic ATI one apparently, since following the directions for that just breaks X again.

Relevant lspci: 
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 LX [Mobility FireGL 7800 M7]

Is there another ATI restricted driver?

---

### Post by DagMan on 2007-09-27
I don't have any experience with ATI drivers, but one thing I have come across with intel drivers is that having more than one version installed can screw things up.  I don't know if that's the case or not or what your situation is, but if the card did previously work out of the box after install with the restricted drivers, I'm thinking that if you remove anything extra you've done then if you are really lucky, then apt-get install --reinstall  the restricted drivers and whatever other packages might have them might write the correct changes in your xorg.conf.  It's doesn't seem likely though.

Probably the easiest thing is to wait for someone to post their xorg.conf who has the same card, or even start a new thread for it since other than this detail your problem is solved and X isnt utterly borked anymore.

Edit: Also I'm looking at these [http://wiki.serios.net/wiki/Ubuntu_ATI_proprietary_display_driver_installation](http://wiki.serios.net/wiki/Ubuntu_ATI_proprietary_display_driver_installation)
[http://ubuntuforums.org/showthread.php?t=305665](http://ubuntuforums.org/showthread.php?t=305665)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
but like I said, I have no experience at all with it.

---

