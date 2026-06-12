---
title: "Mouse clicks stop working for no reason but logging off/on fixes it"
date: 2021-03-10
forum: General Help
---

### Post by mike248 on 2021-03-10
I'm running Kubuntu 20.04 with all updates. 

At random times I can't click anything with my mouse or trackball.  I can move it fine but nothing is highlighted when the pointer is over top of it.  I can use the keyboard just fine during this so I just save whatever's open and then log off.  Once logged off (on the sign in page) the pointer clicks just fine and then upon logon it works again.   I also have virtual machines open sometimes when this happens and the mouse doesn't work in them either (until logging off/on).  

I am using a Logitech M570 and Ergo MX trackball along with the K350 keyboard and they all use the same USB receiver. 

I'd really like to be able to get the mouse working w/o logging off/on and was wondering if there is a way to specifically restart the mouse like restarting networking or similar things.

---

### Post by HermanAB on 2021-03-10
The mouse is handled by Xorg (or Wayland) and logging in/out restarts Xorg.

---

### Post by mastablasta on 2021-03-11
M570 is wireless, perhaps it goes (incorrectly) into power saving mode or something? i am not into wireless as they just drain batteries and usually don't bring much to the table.

in any case i would use a separate receiver.

---

