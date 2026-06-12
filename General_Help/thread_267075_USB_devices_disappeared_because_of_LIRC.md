---
title: "USB devices disappeared because of LIRC?"
date: 2006-09-28
forum: General Help
---

### Post by lerrup on 2006-09-28
Everything has been going fine on my mythbox and tried to make lirc begin at startup.

I used the following command from the wiki:

sudo update-rc.d lirc defaults

This produced an error message that lirc was not installed.

I then tried sudo update-rc.d lircd defaults as sudo lircd is the command I needed to type into make lirc work.

After restarting neither my usb keyboard or mouse work although they are recognised as being connected there is no input accepted from them in the x server or the console.

How do I reverse the command to try and have lirc start from booting up.  Also irw does not work any more....

(I can ssh into the mythbox)

---

### Post by lerrup on 2006-09-28
> **lerrup said:**
> Everything has been going fine on my mythbox and tried to make lirc begin at startup.

I used the following command from the wiki:

sudo update-rc.d lirc defaults

This produced an error message that lirc was not installed.

I then tried sudo update-rc.d lircd defaults as sudo lircd is the command I needed to type into make lirc work.

After restarting neither my usb keyboard or mouse work although they are recognised as being connected there is no input accepted from them in the x server or the console.

How do I reverse the command to try and have lirc start from booting up.  Also irw does not work any more....

(I can ssh into the mythbox)

...and the backend doesn't start automatically now as it used to.

---

