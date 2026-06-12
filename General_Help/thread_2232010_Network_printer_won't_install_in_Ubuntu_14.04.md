---
title: "Network printer won't install in Ubuntu 14.04"
date: 2014-06-29
forum: General Help
---

### Post by Soundislate1 on 2014-06-29
Hi, 

I recently installed Ubuntu 14.04, so now I'm dual booting 12.04 and 14.04. I have a Canon PIXMA MG5250 printer that works in 12.04, but I can't install it in 14.04. If I add it the URL used in 12.04 (cnijnet:/88-87-17-87-D6-1E) in the printer install wizard and choose the correct driver, I get the error message «client-error-not-possible» after clicking forward in the last step. If I try to detect network printers in 12.04, both the location and type of printer is found, but in 14.04 I get nothing. Does anyone have an idea what's going on and how to fix it?

I also tried copying /etc/cups/printers.conf from the old distro to the new and rebooting. This caused the printer to show up in "Printers", but printing gave an error message. (I undid it all, but if the error message is of interest, I can redo it.) 

It seems that the printer is set up correctly in the network, but I cant make it work in 14.04. Any ideas?

---

### Post by philinux on 2014-06-29
In 14.04 open the Printers app from dash or system settings. Then mouse to top and click view. Check that discovered printers is ticked.

---

### Post by Soundislate1 on 2014-06-29
> **philinux said:**
> In 14.04 open the Printers app from dash or system settings. Then mouse to top and click view. Check that discovered printers is ticked.

Yup, it was already ticked

---

### Post by philinux on 2014-06-29
My network printer is attached to a desktop pc and I setup this laptop running 14.04 to use it. It's device uri is shown like this.

ipps://user1-desktop.local:631/printers/Stylus-Photo-R200

Make and model states Remote Printer

Location is user1-desktop

---

### Post by Soundislate1 on 2014-06-29
This printer is set up differently: it has wifi, so it logs on to the network. I'm not sure cnijnet means, but the number after it is the MAC adress as far as I know.

---

### Post by Bucky Ball on 2014-06-29
In that case, if the printer is on the network, you shouldn't have to add the IP manually. Printing>Add Printer>Network Printer. Wait a bit and it should pop up with the networked printer if both your printer and computer are on the same network. Then, just follow your nose. You will need to install the drivers for the printer if you are not offered the driver for it in the procedure that follows.

My printer is a wifi network printer and I have never needed to manually add the IP. You want a static IP on the printer, though, as if not, when you turn the printer on and off again it may not be assigned the same IP and therefore your machine will default to the wrong IP when printing.

PS: If you'd rather do this directly through a CUPS GUI, open a web browser and put 'localhost:631' into the address bar. You can add, delete, and do a heap of other things with your printer there.

Good luck.

---

### Post by Soundislate1 on 2014-06-29
Hi, 

Thanks for your replies and help! I finally figured it out: I had to download drivers for network printing from Canon. I'd forgotten that I did that two years ago when I set up the printer last, I thought that was pretty much a blast from the past.

Sorry to bother you with a rookie mistake, cheers!

---

