---
title: "How Do I Connect PSP To Ubuntu Feisty?"
date: 2007-12-25
forum: General Help
---

### Post by SuperMike on 2007-12-25
Anyone have any luck connecting a PSP (Playstation Portable) to Ubuntu Feisty 7.04? My daughter received one at Christmas and I couldn't get it to connect. I have two USB cables lying around because the thing didn't come with one. I had one cable for my BBerry and one for a USB hub that I bought. I also used a SanDisk Memory Stick Pro Duo 2.0GB that seems to fit nicely in the Memory Stick Pro Duo slot. I have reformatted the stick from the PSP menus.

I looked in computer:/// and didn't see the device, and don't see it on the desktop (even after a reboot). Here's the lsmod, lsusb, and dmesg output:

# lsusb

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

# lsmod | grep usb
usbcore               134280  3 ehci_hcd,uhci_hcd

# dmesg | grep usb
[   17.218403] usbcore: registered new interface driver usbfs
[   17.218432] usbcore: registered new interface driver hub
[   17.218459] usbcore: registered new device driver usb
[   17.220174] usb usb1: configuration #1 chosen from 1 choice
[   17.326771] usb usb2: configuration #1 chosen from 1 choice
[   17.434613] usb usb3: configuration #1 chosen from 1 choice
[   17.548788] usb usb4: configuration #1 chosen from 1 choice

When I do a tail -f /var/log/messages while inserting the device, nothing happens whatsoever.

Is this a lost cause? :cry:

---

### Post by mivo on 2007-12-25
Hmm, this is strange. When I connect my PSP to the PC (using an USB cable that came with the "travel pack" for the PSP), Gutsy treats the PSP like an external USB drive or a camera. I can simply access the memory card in the PSP to add/remove/change files. My PSP does use a custom firmware version, but this should not really matter. Have you had similar problems with other devices that are connected via USB, i.e. a MP3 player or a digital camera?

---

### Post by SuperMike on 2007-12-25
Well, I'm almost there. My daughter found that the USB mode is disconnected by default and you have to turn on USB mode in the settings before it acknowledges it. She then could treat it like a hard drive, but, oddly, the MP3 files she loaded from Ubuntu on it copied there, but then said Corrupt. The ones from Windows did not.

I'm going to investigate this further on a few different Ubuntu PCs at home and I suspect she may have ejected her system wrong. If not, then there might be something odd about the MP3s. Another potential is that the USB cable may have been the culprit and I can connect a different one.

P.S. I think it's lousy that Sony decided not to ship it with a tiny USB cable and wanted to charge extra for it. That's pathetic.

---

### Post by rainwalker on 2007-12-26
Make sure you unmount the PSP before you disconnect it; Ubuntu doesn't copy files over immediately as you drag them onto the PSP (I forgot why, but there was a reason)

---

### Post by SuperMike on 2007-12-26
Correction - My daughter reports now that some of the MP3s from Ubuntu copied over correctly. I'll investigate further tonight when she gives me time with the thing. It may have to do with an embedded ID3 tag or perhaps not. I'll try and see what's the difference between the MP3s that worked from Ubuntu, and those that did not. I'll let you all know.

She did unmount and wait, she says, before ejecting, but perhaps not. I'll be the judge of that when I use it tonight.

---

### Post by rainwalker on 2007-12-26
Alright, and if you need to check the tags on the songs, I recommend using tagtool (install with Synaptic)

---

### Post by SuperMike on 2007-12-26
I use a little-known feature in Beep Media Player -- you just play the song, doubleclick the scrolling title area above where it says "mono stereo" and an ID3 editor pops open. You can even edit the ID3 information even when the song is playing.

---

