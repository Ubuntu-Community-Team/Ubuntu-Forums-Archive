---
title: "Terminal as a download window of firefox, is it possible?"
date: 2008-05-25
forum: General Help
---

### Post by ma_nkooo on 2008-05-25
Friends I want to use my ubuntu terminal as download window of firefox, is it possible? if yes then how to do that!
I am using ubuntu 7.10 & firefox 2.0.0.6

---

### Post by ma_nkooo on 2008-05-26
no reply guys!!!

---

### Post by neymac on 2008-05-27
I didn't figure out what you mean, but you can start the download at Firefox, open its downloads window, select cancel download, right click the mouse, copy download link. Then open a terminal type on it:
wget -c 
and paste the copied link, then you can close Firefox and the download will continue at the terminal.
If the connection breaks, you just press up arrow and press enter that the download will be resumed at the stoped point (the option -c is for resume download).

The file will be saved at the current directory shown at the terminal screen.

---

### Post by muximus on 2008-05-27
u could also use the firefox extension flashgot.. and select wget as the default download manager. In your terminal you might have to do a 
$wget fg in order to see it.. dunno exactly why you would want to do this by the way.. try gwget as well..

---

### Post by ma_nkooo on 2008-05-27
> **neymac said:**
> I didn't figure out what you mean, but you can start the download at Firefox, open its downloads window, select cancel download, right click the mouse, copy download link. Then open a terminal type on it:
wget -c 
and paste the copied link, then you can close Firefox and the download will continue at the terminal.
If the connection breaks, you just press up arrow and press enter that the download will be resumed at the stoped point (the option -c is for resume download).

The file will be saved at the current directory shown at the terminal screen.

> **muximus said:**
> u could also use the firefox extension flashgot.. and select wget as the default download manager. In your terminal you might have to do a 
$wget fg in order to see it.. dunno exactly why you would want to do this by the way.. try gwget as well..
thank you, i wanted the same as you guys told me, thanks again for your help,
regards

---

