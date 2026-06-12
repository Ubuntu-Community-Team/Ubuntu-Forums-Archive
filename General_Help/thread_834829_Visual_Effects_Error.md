---
title: "Visual Effects Error"
date: 2008-06-19
forum: General Help
---

### Post by Samm5506 on 2008-06-19
Whenever I try to change the Visual Effects to Extra, it says "Desktop Effects Could not be Enabled."

Here is the answer I get when I type "./compiz-check" into the terminal:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc R600 [Radeon HD 2900 Series]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


```

I am a new member to Ubuntu so don't hate me. :p

---

### Post by Happy_Man on 2008-06-19
Hmmm... what comes up when you put ```
compiz --replace
``` into the terminal?

---

### Post by Samm5506 on 2008-06-20
> **Happy_Man said:**
> Hmmm... what comes up when you put ```
compiz --replace
``` into the terminal?

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:9400 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

### Post by Samm5506 on 2008-06-20
Could anyone help?

EDIT: Nvm. I found a fix.

In the terminal i typed:
```
sudo apt-get xserver-xgl
```
Now it works. Except the effects are a little slow for some reason :/

---

