---
title: "How do I debug the desktop effects?"
date: 2008-05-31
forum: General Help
---

### Post by FFighter on 2008-05-31
Hello,

For some unknown reason (I suspect on of the last bulk of updates), desktop effects stopped working on my system (Hardy). 

My video card is an Intel Mobile Integrated Graphics Controller. It used to work fine with desktop effects until I booted into the machine this morning.

However, the feedback (feedback?) sent to the user when you try to enable the desktop effects and it fails is at least offensive, if not a joke:

"Desktop effects couldn't be enabled."

Oh! That's very, very helpful. Thanks for the info.

I'm the kind of person that likes to go and research on why something happened, find its roots and solve it. Howewer, how am I supposed to do ti with such clues given by Ubuntu? For everything there must be a first step. So, mine had to be posting this message.

I hope someone could help me. How do I find any clues on why the desktop effects couldn't be enabled?

Thanks,

Marcelo.

---

### Post by FuturePilot on 2008-05-31
What is the output of
```
compiz --replace
```
Also, this could be of help
[http://ubuntuforums.org/showthread.php?t=799070]("http://ubuntuforums.org/showthread.php?t=799070")

---

### Post by FFighter on 2008-05-31
```
 compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 0c) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

It says XGL is not present, but I have not installed it before and compiz was working fine. Strage.

EDIT: Here's the output of the compiz-check script:

```

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

Thanks for the help.

---

