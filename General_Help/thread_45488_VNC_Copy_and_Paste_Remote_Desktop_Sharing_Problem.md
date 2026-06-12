---
title: "VNC Copy and Paste Remote Desktop Sharing Problem"
date: 2005-06-30
forum: General Help
---

### Post by Devi0s on 2005-06-30
I enabled Remote Desktop to my Ubuntu system via System -> Preferences -> Remote Desktop.

I then connected to my Ubuntu system with the TightVNC viewer running on WindowsXP Pro.  I was unable to copy and paste text from my Windows system to the Ubuntu system.  I was also unable to copy and paste text from my Ubuntu system to my Windows system.

I also tried the RealVNC viewer  for WindowsXP Pro.  Again, I was unable to copy and paste text from my Windows system to the Ubuntu system.  Again, I was also unable to copy and paste text from my Ubuntu system to my Windows system.

A friend who is new o Ubuntu experienced the same problem.

Could someone please tell me how to get text copy and paste working between these two systems over VNC?

This is a feature I can absolutely not live without; especially since I can not type.  It would be a shame if I had to re-install WindowsXP on my Ubuntu machine simply because the Remote Desktop Client is able to copy and paste and the VNC sharing option in Ubuntu is not.

I really appreciate any help that you all are able to provide.  Thanks.

---

### Post by intangible on 2005-06-30
Unfortunately, "vino" (which is what the Remote Desktop feature uses) does not seem to support copy and pasting properly.  However, you are not lost :D,  You just need to use an alternate vnc server.

x11vnc seems to do what you want, you get it by adding the universe repositories ([http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories))  It also performs much much better than vino and has many more configuration options.
By default it runs without a password, so make sure you get it setup properly to ask for one.    If you need help making it start automatically with a script, let me know.

Also, the best VNC client and server for Windows is "UltraVNC" ([http://ultravnc.sf.net)](http://ultravnc.sf.net)).  You should try it out.

---

### Post by Devi0s on 2005-06-30
Thank you for confirming that I am not crazy.  I was starting to doubt myself.  \\:D/ 

In any case, I installed the x11vnc package, and yes, I'd love some help making it work automatically and functioning with a password identically to the way Vino does the same.  I suppose step one is to diable vino.

Mind posting the remaining steps here?  I am sure the community would benefit from this information.

I could also use some help installing autocutsel, if you agree that I need it to accomplish the clipboard synchronization that I am looking for.

---

### Post by Devi0s on 2005-06-30
I was able to get everyhting working.  I posted how I did it here:
[http://ubuntuforums.org/showthread.php?p=235746&posted=1#post235746](http://ubuntuforums.org/showthread.php?p=235746&posted=1#post235746)

intangible posted an alternative using vnc4server instead of x11vnc here:
[http://ubuntuforums.org/showpost.php?p=220338&postcount=1](http://ubuntuforums.org/showpost.php?p=220338&postcount=1)

Here's where my information came from:
[http://www.karlrunge.com/x11vnc/#faq-display-manager](http://www.karlrunge.com/x11vnc/#faq-display-manager)

---

### Post by intangible on 2005-06-30
Here's a complete howto for running x11vnc for each individual log in session in place of Ubuntu's "Remote Desktop"  I also included instructions for autocutsel :D

[http://www.ubuntuforums.org/showthread.php?p=236053](http://www.ubuntuforums.org/showthread.php?p=236053)

---

