---
title: "Installing Soundcard"
date: 2008-03-21
forum: General Help
---

### Post by ed3120 on 2008-03-21
I just bought a new soundcard (Chaintech AV-710) to replace my old onboard sound.  I disabled the onboard in the BIOS and after the boot, my sound isn't working.

Is there something that I need to do to tell Ubuntu to start using the new soundcard?  I never configured the onboard sound....it just worked after the Ubuntu install.

I'm running Mythbuntu 8.04 Alpha 4

---

### Post by ibuclaw on 2008-03-21
Firstly, is your hardware connected properly, devices all turned on?

Secondly, does your user have the right permissions to use the audio devices?

Thirdly, do you get any error messages when you try to do anything with the sound preferences, such as "GStreamer plugin error" or "Device does not exist". Something along those terms.

Lastly:
Type this in the terminal:
```
 lspci 
```

I'll see if I can help you through this :)

Regards
Iain

---

### Post by StOoZ on 2008-03-21
try reading :
[http://techpatterns.com/forums/about932.html]("http://techpatterns.com/forums/about932.html")

---

### Post by ed3120 on 2008-03-21
lspci found my soundcard...

01:08.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)


I'm logging in with the same user that I used to, so I assume it has access to the sound.

---

### Post by ed3120 on 2008-04-10
I still can't get this working.  Can anyone suggest a next step?

---

