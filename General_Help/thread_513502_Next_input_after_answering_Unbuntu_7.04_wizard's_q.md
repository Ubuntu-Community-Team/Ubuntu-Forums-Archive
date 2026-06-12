---
title: "Next input after answering Unbuntu 7.04 wizard's questions?"
date: 2007-07-30
forum: General Help
---

### Post by littleones on 2007-07-30
Before the Ubuntu 7.04 CD finished loading on my ThinkPad T-60 (with preinstalled Vista Ultimate)  the following error message came up:"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?  
<Yes>    <No>" Well, I clicked "<Yes>" but what came up was beyond my understanding.

Someone on line suggested that I input the command "sudo dpkg-reconfigure xserver-xorg," which started the text-based wizard to reconfigure X.

Upon answering all of the questions of the wizard, the black input screen came up with the following words: "xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in/etc/X11/xorg.conf.20070729111015." This has left me at an impasse. Can anyone assist me with what I should input next?

---

### Post by kens8 on 2007-07-30
I think I can get you started down the right road.  I've had similar problems before.  First, start Ubuntu in a failsafe terminal.  Then type:

[INDENT]sudo nano /etc/X11/xorg.conf[/INDENT]

Look for the "Device" section.  Mine looks like this:

[INDENT]Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 LE]"
    Driver         "nvidia"
EndSection[/INDENT]

Delete whatever it has for "Driver" and type in "vesa"

Save and reboot.  This should get you to a GUI.  I don't know what you want to do from there.  I looked on Lenovo's website and it looks like your laptop has ATI graphics.  ATI is notoriously bad with Linux support.  You could try ATI's linux drivers, or wait for someone more versed in dealing with ATI to help you out from here.

---

### Post by kens8 on 2007-07-30
I forgot to mention that you should make a backup of the xorg.conf file:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

If you need to resore it, just do the oposite:


sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

---

### Post by kens8 on 2007-07-30
Sorry for posting so many messages.  I just ran across [this]("http://ubuntuforums.org/showthread.php?t=414194").  It should help.

---

### Post by louieb on 2007-07-30
Ubuntu on a thinkpad any thinkpad should work (t30 here). This site is all about [ThinkWiki - Linux on ThinkPad]("http://thinkwiki.org/wiki/ThinkWiki").

---

### Post by kostkon on 2007-07-30
> **littleones said:**
> Upon answering all of the questions of the wizard, the black input screen came up with the following words: "xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in/etc/X11/xorg.conf.20070729111015." This has left me at an impasse. Can anyone assist me with what I should input next?

So, did you reboot after the reconfguration of the X server? If yes, what happened? Did you get the same message that the X server failed to start and such or maybe just a black screen? Or did everything work right?

Please tell us in order to help you more, if needed.

---

