---
title: "Blank screen on bootup on T61p"
date: 2008-07-05
forum: General Help
---

### Post by backdoor on 2008-07-05
Hello,

I just installed the Kubuntu Hardy Heron (8.04.1) on my T61P thinkpad (dual-boot with WinXP).

The installation went fine, but when it boots up, I get no display.

The splash screen shows up and seems to do its full start.  After that, the expectation would haven been to see the login screen.  But, that´s when the display disappears.

As far as X is concerned, I did not see any errors in the Xorg.0.log file. However, I do see an error message in daemon.log for kdm:

> kdm: :0[5402]: Hung in XOpenDisplay(:0), aborting
kdm: :0[5402]: Cannot connect to :0, giving up
kdm[5391]: Display :0 cannot be opened

Not sure if this is a display card problem, but just to mention it ... it is a Nvidia Quadro FX 570M.

Has anyone else run into the same issue?  If so, any ideas what the issue might be?

Thanks.

---

### Post by dentaku65 on 2008-07-05
Try to boot in recovery mode (when the machine boots press esc to get in the grub menu); then the sistem will show you a window menu choose: **xfix** the system reconfigure xorg (it takes 10 seconds), then reboot the machine.

---

### Post by backdoor on 2008-07-06
Thanks dentaku65.  I had already tried that and it did not make any difference.  The xorg file in any case is the same from the original installation.

---

### Post by vinced on 2008-07-06
I looked on the thinkwiki page for your laptop.
[http://www.thinkwiki.org/wiki/Install_Ubuntu_Hardy_Heron_on_a_T61p]("http://www.thinkwiki.org/wiki/Install_Ubuntu_Hardy_Heron_on_a_T61p") 
It mentions a problem with video hanging after suspend, and a few other issues with the Nvidia driver. You might be able to solve your issue from their instructions.
Vince

---

