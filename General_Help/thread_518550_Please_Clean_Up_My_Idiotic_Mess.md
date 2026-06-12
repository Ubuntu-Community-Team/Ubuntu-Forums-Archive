---
title: "Please Clean Up My Idiotic Mess"
date: 2007-08-06
forum: General Help
---

### Post by professorchaos on 2007-08-06
I was messing around in administrative stuff, and I unchecked something about a graphical login manager, and the desktop disappeared, leaving me with a CLI list of services that have started. When rebooting, the loading screen with the logo and progress bar is shown, followed by that same list of started services, and I am unable to do anything but type. I am a very stupid person, please help me.

---

### Post by aidanr on 2007-08-06
```
sudo /etc/init.d/gdm start
```

then re-enable the service

---

### Post by professorchaos on 2007-08-06
> **aidanr said:**
> ```
sudo /etc/init.d/gdm start
```

then re-enable the serviceThanks, but that did nothing. I probably shouldn't have used the term "CLI", because commands do nothing. Just the basic all-black background with white shell font text.

---

### Post by aidanr on 2007-08-06
try switching to another tty eg. ctrl+alt+F6, log in and then type that command
or try booting into recovery mode

---

### Post by professorchaos on 2007-08-06
*sniff* I love you. Really I do.

---

