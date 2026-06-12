---
title: "[SOLVED] sansa sandisk e250 mp3 player"
date: 2007-06-29
forum: General Help
---

### Post by uroskriznar on 2007-06-29
Is sansa sandisk e250 mp3 player compatible with Ubuntu? When I connected it through USB it doesn't seem to show up anywhere.

---

### Post by eggdeng on 2007-06-29
Type ```
dmesg | tail
``` in a terminal just after you connect the device and post the output.

---

### Post by tater_3001 on 2007-06-29
id you have the rhapsody one it needs to be rhapsody mode

---

### Post by uroskriznar on 2007-07-01
dmesg | tail

[   46.456488] Bluetooth: RFCOMM ver 1.8
[   46.814069] eth0: link up.
[   46.918545] eth0: link down.
[   51.940770] eth0: link up.
[   61.893807] [drm] Setting GART location based on new memory map
[   61.893820] [drm] Loading R300 Microcode
[   61.893869] [drm] writeback test succeeded in 1 usecs
[   65.236532] eth0: no IPv6 routers present
[13384.072369] usb 3-5: new high speed USB device using ehci_hcd and address 2
[13384.207628] usb 3-5: configuration #128 chosen from 1 choice

---

### Post by uroskriznar on 2007-07-01
What is Rhapsody mode?

---

### Post by Songwind on 2007-07-01
I have the 260.  If you want it to show up as a drive, then under the system settings on the MP3 player it needs to be in MSC mode, not MTP mode.  MSC lets it be mounted and read/written as a standard USB drive.  MTP must use the Microsoft Transfer Protocol (or something like that) and its implementation in Linux leaves a lot to be desired in terms of robustness and speed.

---

### Post by uroskriznar on 2007-07-01
Thank you very much. Problem solved.

---

### Post by uroskriznar on 2007-07-01
Two more questions. Does anyone know how to add Sansa media player to Amarok as a new device, and why do the tags edited in Amarok not work properly on the Sansa media player?

---

### Post by Songwind on 2007-07-01
Add it as a "Generic Media Player" and it should work fine.

I don't know about the tags - it works for me.

---

### Post by uroskriznar on 2007-07-02
What should I write as the preconnect command (mount %d) and

---

### Post by uroskriznar on 2007-07-02
the postdisconnect command (eject %d) in Amarok?

---

### Post by Songwind on 2007-07-02
I left mine blank.

---

### Post by strabes on 2007-07-02
Amarok is not the best tag editor. Use easytag to write the id3 v2 tags and erase the v1.x tags by unchecking "Write ID3v1.x tag" in the preferences. This was the only way I was able to get it to read my tags correctly. For some reason if your files have both v2 and v1 tags then it seems the e200 won't read any of the tags.

---

### Post by uroskriznar on 2007-07-06
Thanks guys. I am now using easytag and my sansa seems to be working in amarok and ubuntu.

---

### Post by ebash on 2007-07-26
I also have a Sansa player and noticed that some MP3 tags can be read. After further investigation I found out that there are three types of MP3 tags ID3 v1, v2.3 and 2.4. The Sansa player is only able to understand ID3 tags v1 and v2.3. Gstreamer, the library used by amarok and sound-juicer can tag MP3 only in v1 and v2.4. Other software is able to encode in v2.3, for instance EasyTags can do it.

I got annoyed by this and I started writing a gstreamer plugin that adds v2.3 tags. I have submitted the code to gstreamer and it's up for review, luckily it will be one day included in gstreamer. In the meanwhile you can try to compile the plugin in your own.

To compile the plugin download the three patches and follow the instructions in the bugzilla comments:
[http://bugzilla.gnome.org/show_bug.cgi?id=459226](http://bugzilla.gnome.org/show_bug.cgi?id=459226)

---

