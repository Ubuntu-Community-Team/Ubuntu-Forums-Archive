---
title: "Control Characters in Xorg.conf"
date: 2007-06-17
forum: General Help
---

### Post by Robbyx on 2007-06-17
I copied and pasted some code into xorg.conf and ended up with control characters in xorg.conf. Thereafter xorg.conf would not load.  For some reason I could not use the command line sudo gedit xorg.conf if x server has not loaded. In order to get the xorg.conf file edited I had to gedit it from the live cd. 

Was there a command line that I could have used from the system that had not loaded the graphic display manager and thus avoided the need to keep loading the live CD?

---

### Post by PaulFr on 2007-06-17
**sudo nano /etc/X11/xorg.conf** or **sudo vim /etc/X11/xorg.conf** come to mind. nano and vim are command line editors that work in terminals or consoles. Thus they do not need X-Windows or gdm. I personally prefer vim / vi, but nano might be easier to learn.

---

### Post by charleseddy on 2007-06-17
Right, for the long term, vim is the best choice, as it's powerful, flexible, and functional.  If you'd like to learn more about how to use vim, an excellent tutorial is available [here]("http://www.apmaths.uwo.ca/~xli/vim/vim_tutorial.html").

ce

---

### Post by Robbyx on 2007-06-19
Thank you both for your helpful replies.

Robin

---

