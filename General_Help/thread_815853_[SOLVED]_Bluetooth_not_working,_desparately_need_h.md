---
title: "[SOLVED] Bluetooth not working, desparately need help!!!"
date: 2008-06-02
forum: General Help
---

### Post by Kissell on 2008-06-02
I travel a lot internationally and therefore have a great need for VoIP services as a cheap way to do international calling.  However, ever since I switched my laptop to Ubuntu I have been unable to get my Motorola H700 bluetooth headset to work. :(  (I can still use VoIP but I have to use the built-in microphone, and that's really not very good.)

I have tried every fix and forum suggestion I could find, and it still doesn't work.  I'm running Ubuntu 8.04 x64.  

Currently, under bluetooth preferences in the GUI, I see the Motorola H700 in the bonded devices and it's trusted.  In the services tab it's listed as an audio service and as an input service.

However, I can't use it anywhere...  for instance, when I go to SYSTEM - PREFERENCES - MULTIMEDIA SYSTEMS SELECTOR, it doesn't show up under the list of possible devices, and none of my programs like my VoIP software (ekiga) sees it as an audio device.  Now, I'm fairly new to linux and I've never used it with linux before, so maybe I'm just missing a piece of information.  

But, when I do > hidd --connect 00:6C:B7:47:01:4F

I get: > Can't get device information: Success

So even though it shows up in the GUI of bluetooth preferences, I don't think it's really connected, and nothing I've read has been able to help.

---

### Post by can8dnSix on 2008-06-04
[http://ubuntuforums.org/showthread.php?t=786640](http://ubuntuforums.org/showthread.php?t=786640)

---

### Post by eret anika on 2008-11-29
Simply your linux have no bluetooth drivers for running devices.

Go to the system and than administrator and than hardware options click on bluetooth option and click to download drivers and than restart your PC.

---

### Post by gambling on 2009-01-14
have installed the bluesoleil bluetooth dongle, paired my 6265 to it, configured the bluetooth DUN modem with the extra string command, run successful modem query and then tried the bluetooth dial-up-networking dialing #777.
My phone dials #777 via bluetooth but then drops the connection, my laptop then giving error 678: could not connect to the remote host.
I have removed Nokia PC Suite, reinstalled bluetooth, restarted 20 times and I still get this error. Callcentre gives me the same settings already available in threads here and are of no help. My RConnect is active.

---

### Post by clegends on 2009-06-15
This post is marked solved, could you please tell us how you did it? Similar issues. Thanks.

~dinky

---

