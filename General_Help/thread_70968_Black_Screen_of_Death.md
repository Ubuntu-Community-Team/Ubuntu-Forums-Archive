---
title: "Black Screen of Death"
date: 2005-10-01
forum: General Help
---

### Post by HeyYoTyson on 2005-10-01
I am new to the Ubuntu and Linux and am trying to boot from the 5.10 live CD on a gateway M275 tablet PC. I have 1.24 GB RAM and 1.7 GHz Intel Pentium M. My graphics controller is intel 82852/82855 GM/GME. 

Anyway, when I boot up I get thru the selection of the language options, etc. and the loading proceedure gets all the way to setting up the monitor ("the screen may go blank") and then the screen goes black and stays black. I can see that the hard drive and cd drive are working for a while and I even hear a few seconds of startup music and then.... nothing. I have let my computer sit for half an hour and still I have the black screen. What can I do?

Also, I have tried to do the VGA=766 thing, but I get an error and Ubuntu doesn't start up.

---

### Post by John.Michael.Kane on 2005-10-01
try the 5.04 live cd. let us know if you get the same issue
also you can try this type  linux archive-copier/copy=false vga=792 press enter

---

### Post by HeyYoTyson on 2005-10-01
Ok... never mind. I let the live cd boot up until I heard the sound and then I pushed Fn-F3 (which is the LCD/CRT mode change button) and the main screen turn on. This computer has two graphics controllers which I think may be the problem. 

Now I have a new problem... How do I get onto the internet from ubuntu?




By the way... thanks so much for your quick reply!!!:razz:

---

### Post by John.Michael.Kane on 2005-10-02
if your using ethernet then click system > admin>networking activate the network cards you want to use ie: wifi or line base. if your using pppoe then type sudo pppoeconf in the term, for wifi theres howto's on the forum for setting them up..

---

### Post by boyfromthedwarf9 on 2006-06-16
I know the thread is dead, but for anyone else who needs it, press FN+F3.  I had the same problem with Fedora Core 5, I'm using Dapper now without this problem, my best guess is that the OS gets confused, and is outputting on some other channel.

---

