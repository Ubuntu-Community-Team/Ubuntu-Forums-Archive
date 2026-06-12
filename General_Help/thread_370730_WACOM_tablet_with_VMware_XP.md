---
title: "WACOM tablet with VMware XP"
date: 2007-02-26
forum: General Help
---

### Post by jdtate101 on 2007-02-26
I recently bought a wacom tablet to use with photoshop CS2. I use CS2 inside a vmware machine (running vmware server on ubuntu) which is XP pro. I have setup the xorg.conf file so that wacom is recognized correctly and will do the correct pad scaling for my screen, AND pressure sensitivity in GIMP/INKSCAPE etc.. (ie linux aps). This is fine and works well. I can also add the tablet as a USB device to my XP image where it is recognized and restricted to use just inside the vmware (works flawlessly)

I still have two small niggles left which I'm hoping people here can help with:

1) When I reconnect the USB powered wacom, it behaves like a mouse, but not properly setup for pad size etc...and won't behave as it should until the xorg server is restarted (ie logout, then cntl-alt-backspace, then log back in), then it's fine. Is there any way to avoid this restart of the x server????

2) When finished using the tablet in XP I disconnect it logically from the vmware machine, and control returns to linux. Ususally it will disconnect/reconnect to the USB bus at this stage. This means it gets a different resource number, and will NOT show up as available for vmware (as a device that can be connected). The only way to solve this is to restart the vmware services with:

/etc/init.d/vmware restart

Upon which it is again visable to be connected. Anyway around this???

The above are small niggles, but I would be greatful if anyone had any ideas???

TA

J

---

### Post by jwilkins on 2007-05-16
Check out 
[http://www.vmware.com/community/thread.jspa?messageID=562879&#562879](http://www.vmware.com/community/thread.jspa?messageID=562879&#562879)

---

### Post by jwilkins on 2007-05-16
and 
[http://www.vmware.com/community/thread.jspa?messageID=637668](http://www.vmware.com/community/thread.jspa?messageID=637668)

---

### Post by fragos on 2007-05-16
Wacom driver gets confused if the tablet isn't plugged in when you startup.

---

