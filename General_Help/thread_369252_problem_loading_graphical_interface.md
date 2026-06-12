---
title: "problem loading graphical interface"
date: 2007-02-24
forum: General Help
---

### Post by Sumbarino on 2007-02-24
i installed Ubuntu Linux within the last hour for the first time, i went through the install reboot my computer went to load ubuntu from the hard drive and it gave me this error message:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

I have a pentium core 2 duo @ 2.00GHz, intel mobile chipset 945GM, Intel® Graphics Media Accelerator 950

someone please help me

---

### Post by taurus on 2007-02-24
<Ctr><Alt>F2 and log in with your username and passoword.  Then, run

```
sudo dpkg-reconfigure xserver-xorg
```
And if you are not sure about a question, just use the default.  And pick **vesa** as a driver for your graphic card.

Reboot and see what happens to X this time.

```
shutdown -r now
```

---

### Post by Sumbarino on 2007-02-24
Thanks, ill try it right now

---

