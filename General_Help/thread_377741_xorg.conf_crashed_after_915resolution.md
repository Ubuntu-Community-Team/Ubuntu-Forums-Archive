---
title: "xorg.conf crashed after 915resolution"
date: 2007-03-06
forum: General Help
---

### Post by samjaynes on 2007-03-06
In the process of trying to resolve the Intel 915GM video card issue, I ran the reconfigure for x-server and ctl-alt-bksp and it did not come back.  I shut the laptop down, and rebooted, and after the login screen, it just went black, and then back to the login screen.  I finally got it to a terminal and cp'd by xorg.conf back-up file... Whew!

I have the i915GM video card on a Dell D610 laptop.  I am trying to use the native resolution of 1024x768 on the screen itself, and 1280x1024 on the Dell 1905FS monitor I have attached through a port replicator DMI.

When I ran the reconfigure x-server, I accepted all the defaults until I until I was able select my preferred resolutions (as instructed by a thread on this site).  

Any suggestions on how to resolve this issue... I am not looking for some fancy widescreen format, just 1280x1024 on a monitor that I know supports it, and higher.

P.S.  What about the frequency rates, and RAM questions in reconfig?

---

