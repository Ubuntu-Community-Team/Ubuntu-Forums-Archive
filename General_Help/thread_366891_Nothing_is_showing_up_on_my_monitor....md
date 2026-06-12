---
title: "Nothing is showing up on my monitor..."
date: 2007-02-21
forum: General Help
---

### Post by Pikestaff on 2007-02-21
So I'm trying to put Kubuntu onto my desktop because it works so well on my laptop, but when I try to boot up the LiveCD I get a bunch of different colored lines on my monitor and a message pops up that says "Input Signal Out of Range: Change Settings to 1280x1024 60Hz"... then the screen goes blank.  I hear the startup sound and everything so I assume everything else is working but I don't know how to get visuals :( 

Safe Graphics Mode does not do anything to help the problem, and as far as I am aware, my settings are already 1280x1024 and 60Hz.

I'm using a flatscreen monitor and an NVIDIA GeForce 6800 XT graphics card, if that matters... and the same thing happens whether I put in the Dapper or Edgy LiveCD.  Please help!

---

### Post by cookfromfrozen on 2007-02-21
Hello

Try downloading the "alternate install" CD of Kubuntu instead.  That uses a text-based installer, so it's not as pretty looking as the LiveCD and might be a little harder to use, but it will help you install Kubuntu.

[http://www.kubuntu.org/download.php](http://www.kubuntu.org/download.php)

(Select a mirror and choose the "Other installation options" option to download the alternate CD.)

During the installation, you may be asked to set what resolutions you want Kubuntu to use, so you could pick a setting you know works (like 1024x768).  If it doesn't and if the display still won't come up after installation, post back.  You will probably need to edit your display configuration (the Xorg.conf file) to stop Kubuntu using the resolution that the monitor doesn't support.

Hope this helps.

---

### Post by Pikestaff on 2007-02-21
Thank you for the response... would installing from the LiveCD under a different resolution work as well, so I don't have to download the alternate install CD?  I ask because I've found out that I can get it running if I boot from the very start under 1024x768 at 30Hz, and it runs fine then (except that there is no cursor, which makes things quite difficult)...

If I install it like this, will there be a way to fix the resolution later and get myself a cursor by editing the xorg.conf file like you said?

---

### Post by Pikestaff on 2007-02-21
I just wanted to say I've figured this out... I managed to get Kubuntu installed and then because it still was having problems with the monitor, I booted it up in Recovery mode and reconfigured xorg (I saw how to do this in another thread) and it works now!!

Thank you for your advice cookfromfrozen, it gave me the idea to install it under a different resolution. :)

---

