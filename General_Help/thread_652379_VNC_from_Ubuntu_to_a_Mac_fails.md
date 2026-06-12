---
title: "VNC from Ubuntu to a Mac fails"
date: 2007-12-28
forum: General Help
---

### Post by opus_az on 2007-12-28
Hi...

VNC fails when connecting from Ubuntu to a Mac. 

Connecting with Windows to the same Mac works fine, and Ubuntu can ping the Mac.

I tried $ vncviewer xxx.xxx.xxx.xxx. After entering the password the screen flashes then returns me to the terminal showing "VNC autentication succeeded" plus several lines ending with "ShmCleanup called".

I also tried Ubuntu's Terminal Services Client, with the IP address and setting the protocol to VNC. It prompts me for the password then returns an error with all the same text of the vncviewer.

Any suggestions?

Ubuntu 7.04 and Leopard.

TIA

---

### Post by opus_az on 2007-12-28
Sorry, nevermind. I got it, but let me know if this isn't the right way.

This succeeded: $ xtightvncviewer xxx.xxx.xxx.xxx

And this allowed the TS Client to succeed too: update-alternatives --set vncviewer /usr/bin/xtightvncviewer.

It's never fun when my google-fu works but is just a few minutes too slow.

Thanks anyway, and have a happy new year!

---

