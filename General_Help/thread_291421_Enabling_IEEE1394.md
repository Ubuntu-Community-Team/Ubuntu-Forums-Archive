---
title: "Enabling IEEE1394"
date: 2006-11-02
forum: General Help
---

### Post by hemple on 2006-11-02
Irun Ubuntu Dapper Drake 6.06. and I have just downloaded Kino to export some video from my Panasonic Camcorder via IEEE1394 port. but the following error message is formulating...."The IEEE 1394 Subsystem is not loaded;all IEEE 1394 options are disabled." and when i try to capture video through the same method the following appears, "WARNING:raw1394 kernel module not loaded or failure to read/write/dev/ra..."

i have no idea what to do to enable the firewire port. anyone have any suggestions??

thanks for your time.

---

### Post by jo.angel on 2006-11-10
I had the same problem. Ubuntu, as it has  got a different root concept, does think that you are just a user., not root. To change the access and (hopefully enable the module)
try this:

---close kino
---open shell
---enter [COLOR="Red"]gksudo nautilus [/COLOR](this opens nautilus with root rights)
---find the module raw1394 in nautilus
---rightclick it
---change permissions, so you can access it as "normal user"
---open kino and check again

Hope it works out for you, it did for me. But I still cant get kino running as the audio "stutters". This might be because kino apparently accepts only oss, not alsa.

Good luck mate

Jo

---

