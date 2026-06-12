---
title: "LibreOffice Impress freezes my system"
date: 2020-02-19
forum: General Help
---

### Post by bswilson on 2020-02-19
On my Ubuntu 18.04.4 LTS system, every time I open LibreOffice Impress (version 6.0.7.3), my entire system freezes. I can't kill the GUI and must hard reboot by power cycling. There's a thread from 2011 ([https://ubuntuforums.org/showthread.php?t=1699131&highlight=LibreOffice+Impress+freezes+system](https://ubuntuforums.org/showthread.php?t=1699131&highlight=LibreOffice+Impress+freezes+system)) that recommends increasing memory. I will try that momentarily, but wanted to get this post in first.

Has anyone else experienced this?

---

### Post by bswilson on 2020-02-19
Wow. I just learned that my Libreoffice version is WAAAAY out of date! I just installed 6.4.0.3, so hopefully that will fix my problem. Will report back.

```
bswilson@doctordre:~$ libreoffice --version
LibreOffice 6.4.0.3 4c008856d7f83292dc6823d3bed76200cc9a2ba2

```

---

### Post by bswilson on 2020-02-19
Well, that did not work either. Can anyone guide me on how to troubleshoot this situation? For now I've removed Libreoffice completely.

---

### Post by dragonfly41 on 2020-02-19
Interesting. I see that in Ubuntu 18.04 I have this version.
libreoffice --version
LibreOffice 6.0.7.3 00m0(Build:3)

I am downloading version 6.4 right now to try it.

---

### Post by CelticWarrior on 2020-02-19
How exactly do you want someone to troubleshoot after you uninstalled it? I guess you can still read the logs and that alone may have some clues. But nothing else can be done.

I suggest posting your hardware specifications, namely the graphics card and driver version if manually installed.

---

### Post by Impavidus on 2020-02-20
The version of Libreoffice on any Ubuntu release is frozen a short time before that Ubuntu is released, so Ubuntu 18.04 has Libreoffice 6.0.7. Ubuntu 19.10 has Libreoffice 6.3.2. Important bugfixes however get applied to the version in the repositories. That's the idea behind stability and it works like that for most software in the official Ubuntu repositories. If you want the most recent version, I suggest you try a PPA. I believe Libreoffice has a reliable PPA available.

---

### Post by ajgreeny on 2020-02-20
It would appear that your problem is not specifically related to a problem of your LO version but something more basic, perhaps in the user configuration for LO.

With nothing of LO running try renaming the configuration folder in ~/.config/libreoffice then restarting LO.

Incidentally I have been using the LO PPA for several years now with no problems.
All info about installing that PPA is at [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa)

---

### Post by mastablasta on 2020-02-20
open it via teminal to see any errors popping up. well the last error will be on frozen screen.

---

