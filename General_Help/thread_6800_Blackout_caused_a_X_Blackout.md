---
title: "Blackout caused a X Blackout?"
date: 2004-12-01
forum: General Help
---

### Post by dewy on 2004-12-01
2 days ago we had a black out (power only just came back on 3 hours ago) and I went to start up my ubuntu box and it was giving some kinda of error like:
*ror: Can't find/set resolution
or something similar, after the text flew past and attempted to start x (GDM) the screen went into standby. I then plugged the machine into a different monitor and had the same error/problems. I can boot the LiveCD with out troubles I just can't start my install, Has any one had this error before and if they have could you please tell me how to cure it :?:

---

### Post by jdong on 2004-12-01
Most likely, /etc/X11/XF86Config-4 has been corrupted.

Reconfigure your X-Server by running **sudo dpkg-reconfigure xfree86-server**

---

### Post by dewy on 2004-12-01
Thanks for the fast reply but how can I get Ubuntu to boot without trying to run X?

---

### Post by dewy on 2004-12-02
Ok, I have worked out how to boot into Text mode (Press ESC at grub prompt > select Diagnostic mode) I then went onto run "sudo dpkg-reconfigure xfree86-server" but I was told cannot find xfree86-server. I am just about to reinstall this machine, but I don't want to, I don't want Ubuntu to turn into windows, Format every thime something f***s up. \\:D/

---

### Post by dewy on 2004-12-02
I have just reformatted my HDD and re-installed ubuntu, I have installed xmms, libmikmod2, nvidia-glx/-settings, build-essestials xlibs-static-dev then rebooted and the machine has done the same again, could some one please help.

---

### Post by Hikaru79 on 2004-12-06
[QUOTE=dewy]Ok, I have worked out how to boot into Text mode (Press ESC at grub prompt > select Diagnostic mode) I then went onto run "sudo dpkg-reconfigure xfree86-server" but I was told cannot find xfree86-server. I am just about to reinstall this machine, but I don't want to, I don't want Ubuntu to turn into windows, Format every thime something f***s up. \\:D/[/QUOTE]

The problem is that jdong made a typo. It is not xfree86-server but rather xfree86-**x**server . One letter can make a huge difference, and it seems in this case, it drove you to reinstall Ubuntu :( I'm sorry that I didn't see this thread sooner, this could've been avoided.  #-o

---

### Post by jdong on 2004-12-11
ugh, sorry! I was at school using a Windows box at the moment, so I couldn't check the command.

---

