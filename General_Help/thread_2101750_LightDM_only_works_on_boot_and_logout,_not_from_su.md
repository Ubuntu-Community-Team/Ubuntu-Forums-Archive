---
title: "LightDM only works on boot and logout, not from suspend"
date: 2013-01-05
forum: General Help
---

### Post by llogg on 2013-01-05
I've been running 12.10 for a while but only recently realized that it was using GDM as the default display manager when I couldn't get the login screen to change backgrounds.  I then managed to set LightDM as the default and edit it to what I wanted.  When I boot or restart I get the LightDM with unity-greeter as I expect, but if the session suspends when I go to wake it I get a different login screen (same background but different box for password/switch user).  This is probably related to the fact that I set up Cinnamon as the DE after setting up LightDM.  The computer never suspended between doing those two things so I don't know if LightDM would have worked properly on suspend before I installed Cinnamon.  One last comment is that I used Linux Mint for a long time and the login from suspend looks exactly like the one I was used to seeing in Mint.  I do not have MDM installed.  Any help would be appreciated, sorry for the long post.

---

### Post by llogg on 2013-01-07
A little clarification.
When I boot up or log out/in I get essentially this screen (which is what I want):
[IMG]http://iloveubuntu.net/pictures_me/unity%20greeter%20024%201.png[/IMG]
But when the computer is idle and suspends or I choose to suspend session, when I go to log in again I get this:
[IMG]http://www.linuxmint.com/pictures/screenshots/nadia/mdm-switchuser.png[/IMG]
I do not think I have MDM installed.  When I run dpkg-reconfigure lightdm it only shows lightdm and gdm as options.  Again, any help is appreciated.

---

