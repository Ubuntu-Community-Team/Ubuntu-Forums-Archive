---
title: "boot problem with GRUB"
date: 2007-08-19
forum: General Help
---

### Post by Nehvrook on 2007-08-19
Okay. This is a strange one.

I've had Ubuntu and Windows dual booting on this PC for a while now, and everything was fine. Windows was installed onto a 120Gb SATA hard drive and Ubuntu onto a 160Gb IDE hard drive. Everything was good untill the SATA cable snapped. I got a new cable and I expected to turn it on to be exactly as it was.

But instead neither Ubuntu or Windows would boot. I eventually figured that to get Ubuntu to boot I had to point grub to h0,0 . But I have no idea why this is. Because Ubuntu should be (And always was) at h1,0 and windows was at h0,0

So I have Ubuntu booting but Windows won't boot. 
I left the location of windows as h0,0 and I get "Invalid or unsupported executable format"t.  So I changed it to h1,0 thinking that somehow they had swapped. But that gives me "Starting up" like it should but then nothing happens. It just sits there flashing a cursor.

So somehow it seems the locations of the drives have been swapped? And Windows is un-bootable

I'm really confused so does anyone have any idea's?

---

### Post by Qu4k3R on 2007-08-19
I don't know what is your windows partition no.
have you try'ed any more partition ?
I mean
something like as h1,1 h1,2 ..

Hope this helps...

What are your boot options ?

---

### Post by logos34 on 2007-08-19
> **Nehvrook said:**
> So I have Ubuntu booting but Windows won't boot. 

I left the location of windows as h0,0 and I get "Invalid or unsupported executable format"t.  So I changed it to h1,0 thinking that somehow they had swapped. But that gives me "Starting up" like it should but then nothing happens. It just sits there flashing a cursor.

So somehow it seems the locations of the drives have been swapped? And Windows is un-bootable

Edit device.map and your windows entry in menu.lst:

**gksudo gedit /boot/grub/device.map**

Change your linux drive to '(hd0)' and the windows drive to '(hd1)'.

**gksudo gedit /boot/grub/menu.lst**

Add map lines to your windows entry like this:

> title		Windows XP
root		(hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
savedefault
makeactive
chainloader	+1

---

### Post by Nehvrook on 2007-08-20
Thanks logos. That worked. Windows is booting as it should now :D

Now I'm just wondering why on earth this happened? And how it happened? XD

---

### Post by logos34 on 2007-08-20
> **Nehvrook said:**
> Thanks logos. That worked. Windows is booting as it should now :D

Now I'm just wondering why on earth this happened? And how it happened? XD

From your initial description it sounds like the bios boot priority got switched somehow so that the ide became the first boot disk.  But when that happens--XP disk going frm first to second in boot order--you need to add some special parameters to the windows entry in your grub config files, otherwise it refuses to start up.  

More about that here:

**['Changing the Boot Disk']("http://www.linux-mag.com/id/1529/")**
[URL="http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands"]
'Chainloading Windows using map commands' [/URL]

---

