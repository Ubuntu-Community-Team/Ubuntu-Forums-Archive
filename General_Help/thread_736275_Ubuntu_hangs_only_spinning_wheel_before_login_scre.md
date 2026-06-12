---
title: "Ubuntu hangs only spinning wheel before login screen"
date: 2008-03-26
forum: General Help
---

### Post by SilverShadow on 2008-03-26
Hi guys,
I've been using Ubuntu for a while now and I'm absolutely loving it!
However I'm in a little trouble now. I'll try to explain the things I did before this problem occured as accurate as possible.

I wanted to turn on the special effects in the Gnome appearance manager or whatever it's called, so I first tried to set it to 'normal' (they were completely turned of from the beginning). A little error window popped up saying somethign like 'Composite extension not installed'. I clicked 'OK' but it just kept popping up again and again. So I closed the popup window with the cross icon and it went away. The option 'normal effects' was still selected however. I think this is the problem but I'm not sure. I don't think my graphics card supports the effects (I have ATI maybe the driver is the problem?)

After that I found this post on the forum telling you how to improve the fonts: 
[http://ubuntuforums.org/showthread.php?t=180647]("http://ubuntuforums.org/showthread.php?t=180647")

So I followed the instructions listed in the codebox, installed those packages, copied the font file, did the dpkg thing (maybe part of the problem as well?) and rebooted my pc. From that moment on everytime I start Ubuntu it doesn't get to the login screen but instead gets stuck at the spinning wheel which also 'hangs' (stops spinning). I went into recovery mode and edited my xorg.conf file to auto-login, and now it does login, even loads my correct mouse skin (nothing fancy just the glas one) but doesn't display anything else except a pink background.

How can I solve this without having to reinstall??
Many thanks in advance.

---

### Post by danwood76 on 2008-03-26
In recovery mode are there any errors in your xorg.conf?

do the following commands to find out:
```

cat /var/log/Xorg.0.log | grep '(EE)'
cat /var/log/Xorg.0.log | grep '(WW)'

```

What graphics card and drivers are you using?

---

### Post by SilverShadow on 2008-03-26
Hi, thanks for the reply.

The first command didn't return anything.
The second command returned the following:

```
The directory '/usr/share/fonts/X11/cyrillic' does not exist
Open ACPI failed ('/var/run/acpid.socket') (no such file or directory)
RADEON: No matching device section for instance (BusID PCI:1:0:1) found
RADEON(0): No crtc mode list for crtc 1, continuing with desired mode
AIGLX: 3D driver claims to not support visual 0x23
AIGLX:       ''                            ''                        0x24

Same till visual 0x32.
```

I have a RADEON X300 128MB HyperMemory graphics card, and I installed the driver through Ubuntu, it told me my graphics card needed a driver or something but that it wasn't maintained by Ubuntu blablabla. I think it was a restricted driver I don't remember what those things are called. I didn't download one from the internet.

---

### Post by SilverShadow on 2008-03-27
BUMP.

Can anyone help me with these warning messages? I don't know what they mean :(
Or with my problem in general?

---

### Post by danwood76 on 2008-03-27
Sorry forgot to reply, at work at the moment.

I get the 'AIGLX: 3D driver claims to not support visual 0x23' errors in my install aswell.
What worries me is the message before, I think that maybe your ati driver is slightly messed up.

You can try resetting the graphics driver to be the vesa driver which should work with your machine.
In recovery mode run the following command:
```

sudo dpkg-reconfigure xserver-xorg

```
This will give you a menu which will talk you through the config, select the vesa driver when prompted and also your monitor settings etc. (it should hopefully be self explanitory)
When youve finished try rebooting normally to see if it makes a difference.

---

