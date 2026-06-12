---
title: "ATI Catalyst 7.11 for Linux release"
date: 2007-11-24
forum: General Help
---

### Post by HugeLoad on 2007-11-24
As it was reported [here]("http://tuxenclave.wordpress.com/2007/11/23/ati-catalyst-711-linux-released/") 

> "A new version of the ATI/AMD Linux display driver was released last night for both x86 and x86_64 platforms. This release is a bit special, as it includes support for Ubuntu 7.10. Moreover, starting with this version, the ATI Catalyst software suite does not support the Linux kernel 2.4, XFree86 4.3 software and workstation hardware"

Drivers can be downloaded [here]("http://ati.amd.com/support/driver.html")

1. Has anyone given the new release drivers a shot under Gutsy?
2. Is this likely to be an automatix update item?

The problem is that my workstation is a production machine, so I don't dare really screw around with it because downtime due to borked display drivers etc would be catastrophic. Hence my question(s).

Note to self: build a frankenputer to test stuff like this
Additional Note to self: soon OK?

---

### Post by melojo on 2007-11-24
I found the new driver to be slugish under Gutsy especially when running FireFox.  Does anyone have a suggestion to fix this?  I also found out that if you are running the Xgl server my system seems to crawl.  I uninstalled Xgl and its better.

---

### Post by rbmorse on 2007-11-24
7.11 works fine for me on an R580 (X1950XTX).  

Firefox does not drag.  Compiz (dektop effects) are now supported directly (no longer need to load XGL) and work fine (wobbly winders and all) and the not-a-benchmark glxgears reports around 11,000 fps. 

Video playback in a window flickers if the playback engine is using Xv, This is noted on the Compiz FAQ wiki and their recommendation to switch the playback engine to X11 cures the problem for me. 

Installation was nominal, I just followed the guide in the sticky section of the multimedia and video fourm.  

I've used Envy to install the FGLRX download in the past with success, but I don't know if Envy has been updated to accommodate the 7.11 driver package, yet.

---

### Post by melojo on 2007-11-24
if I don't install xgl server ubuntu will not enable desktop affects.  Tells me that composite extensions not available.  Any suggestions?

---

### Post by melojo on 2007-11-24
I did find a new setting under system-preferences-GL destop.  But when I check the box for GL destop it flickers a couple of times then says I can keep settings.  When I click keep settings and exit then go back to it GL Desktop is unchecked.  Any Ideas?  Also for some reason I can't generate distribution specific package using the arguments for the install.

---

### Post by melojo on 2007-12-01
well the only way i get the latest ATI drivers to work with compiz is to install xgl server but don't enable destop effects thru ubuntu.  I have a setting under system prefernces called GL desktop(I am assuming this setting comes from ati drivers) and can enable it.  Compiz runs slower for me with the latest ATI drivers.  I have read the post above that says you don't need xgl server because ati has built in aiglx, but like I said the only way I could get desktop effects to work was to install xgl server

---

### Post by Loophole on 2007-12-06
> Video playback in a window flickers if the playback engine is using Xv, This is noted on the Compiz FAQ wiki and their recommendation to switch the playback engine to X11 cures the problem for me.

I'm also having this issue, can anyone tell me how to change the playback engine in movie player or flv


> well the only way i get the latest ATI drivers to work with compiz is to install xgl server but don't enable destop effects thru ubuntu. I have a setting under system prefernces called GL desktop(I am assuming this setting comes from ati drivers) and can enable it. Compiz runs slower for me with the latest ATI drivers. I have read the post above that says you don't need xgl server because ati has built in aiglx, but like I said the only way I could get desktop effects to work was to install xgl server 

I had the same problem when I uninstalled xserver-xgl. I managed to fix it by editing the xorg.conf file

change composite = "0"
to         composite - "1"

now everything is working. Have you tried this yet?

---

