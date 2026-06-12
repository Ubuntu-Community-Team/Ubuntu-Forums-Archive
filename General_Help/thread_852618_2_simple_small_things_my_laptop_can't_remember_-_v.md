---
title: "2 simple small things my laptop can't remember - volume and brightness"
date: 2008-07-07
forum: General Help
---

### Post by earthpigg on 2008-07-07
soooo whenever i start my computer, i then open and close nvidia x server. i know the nvidia driver is up and running PRIOR to doing that because i can do all the fancy compiz stuff. my box just doesn't seem to want to remember what its brightness is set at.

also, whenever i start my computer, i have to remember to start Alsa mixer and actually click on the volume i want it to be at (can't just open, have to click)... or it thinks its supposed to be at max volume and wakes my roomates up.

both of these problems are pretty odd, no luck searching the forums for an answer so far :)

laptop
ubuntu hardy heron 64 bit
nvidia 8800 512
my sound preferences are all on "autodetect" right now, i tried a few different drivers out (including PulseAudio) and that had no effect.

thank you in advance :)

---

### Post by iaculallad on 2008-07-07
For the volume problem, try to save ALSA's settings before shutting down:

```
sudo alsactl store
```

---

### Post by earthpigg on 2008-07-07
> **iaculallad said:**
> For the volume problem, try to save ALSA's settings before shutting down:

```
sudo alsactl store
```

thanks. is there a way to do that in the GUI? cuz there is no way i am going to remember that when im setting up other computers and such...

---

### Post by iaculallad on 2008-07-07
Right-click on the Desktop and select "Create Launcher..", a new window will open and select configure the settings as:

**Type:** = Application in Terminal
**Name:** = Save Sound
**Command:** = sudo alsactl store

and click on OK button, that should create a launcher named "Save Sound" on your Desktop.

---

### Post by earthpigg on 2008-07-08
thanks, iaculallad!

any advise with the brightness issue?

---

### Post by sdennie on 2008-07-08
I'm not completely sure what you mean about brightness.  Do you mean the backlight strength of an LCD or the color brightness?  If you are using nvidia-settings to change this value.  Go to System->Preferences->Sessions and add the following command to the startup commands "nvidia-settings -l".  That will load your saved nvidia settings at login time.

---

