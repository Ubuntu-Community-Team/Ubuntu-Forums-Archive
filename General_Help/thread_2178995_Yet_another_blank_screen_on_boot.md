---
title: "Yet another blank screen on boot"
date: 2013-10-06
forum: General Help
---

### Post by Funk66 on 2013-10-06
Hi,

I'm having that infamous black screen issue after upgrading to 13.04. I already tried some possible workarounds I found on the web:

- Regenerating .ICEauthority and .Xauthority files
- Some tinkering within /etc/X11
- Reinstalling/reconfiguring the X server, unity, nvidia drivers, lightdm/gdm
- Restarting the lightdm service. Adding some sleep to /etc/init/lightdm.conf. Using gdm instead of lightdm

None of these made any change, so I thought it would be good trying to figure out what the problem is, instead of keep trying with random solutions I find all over the place. But there lies my problem. I don't know how to find the culprit for my problem.
I don't have access to the computer itself, so I do everything through ssh.
Sometimes, after boot, X is not working at all. So when I try to open any window, such as 'DISPLAY=:0.0 xclock', I get:

No protocol specified
Error: Can't open display: :0.0

But then, if I 'sudo restart lightdm', I can open any window over a black background, but these windows have no borders around. The graphics card is a GeForce4 MX 440 AGP 8X.
Some further info. The file .xsession-errors reads:

Xlib:  extension "GLX" missing on display ":0".
openConnection: connect: No existe el archivo o el directorio
cannot connect to brltty at :0
Script para cjkv iniciada en run_im.
Script para default iniciada en run_im.
init: update-notifier-crash (/var/crash/_usr_bin_transmission-daemon.122.crash) main proceso (2062) terminó con estatus 127

Does that say something to you guys? Some guidance is appreciated.
Thanks

---

### Post by Funk66 on 2013-10-07
Really? Nobody knows?

---

### Post by fantab on 2013-10-07
How did you Upgrade to 13.04? From the update manager?
Have you installed any Proprietory Graphic Drivers?
Have you tried the [NOMODESET]("http://ubuntuforums.org/showthread.php?t=1613132") option?

Sometimes re-installing Ubuntu can be the better option...

---

### Post by PaulBx on 2013-10-07
I have gotten used to using "Fn-up arrow" (the keyboard method to make the screen brighter) because I end up with a black screen too. I know there are ways to control brightness on boot but the ones I have tried have had side effects I prefer to avoid. Anyway I bring this up in case you are running into this. I have not ever had this problem with Arch Linux nor with Puppy; it does not really bother me but is a little part of my lubuntu boot ritual.

---

### Post by Funk66 on 2013-10-07
I upgraded via terminal. And I did try the NOMODESET option with no luck.
I know re-installing would save me a lot of time, but I'm trying to help somebody else on this and therefore I have to do this remotely. So re-installing is not an option, simply because I cannot do it. That also discards PaulBx's solution (no access to the keyboard).

Propietary drivers are installed, but I don't know how to check which ones are being used.

There must be a detailed log somewhere, right? So it should be possible to see what exactly the error is. Any idea?

---

### Post by fantab on 2013-10-07
If its a graphics card then check Xorg.log... look in /var/log

---

### Post by Funk66 on 2013-10-09
Ok, so I think I found the problem. Reading through the kernel log I found a few lines saying that nvidia-304 were currently installed, but this GPU requires nvidia-96.43.xx
I performed the distribution upgrade from a 12.04 installation, which had the nvidia-96 package installed. But from 12.10 on, this package has been deprecated because of some incompatibility with the X-server, or so I read. That raises some questions:
Did upgrading ubuntu make this pc unusable?
Are the nvidia-304 drivers a replacement for the older nvidia-96? Or why did the update manager make that change if these are incompatible?
Could I still use the open source drivers? If so, how do I set it up from the terminal?

I hope this gets sorted out once mir becomes more stable, but as far as I know it still doesn't work with nvidia drivers.

Thanks

---

### Post by Funk66 on 2013-10-11
Should this thread be in the Hardware or Video sections?

---

