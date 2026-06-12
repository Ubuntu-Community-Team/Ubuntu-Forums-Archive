---
title: "Ubuntu 18.04 Bionc Gksudo No More"
date: 2018-05-13
forum: General Help
---

### Post by Redalien0304 on 2018-05-13
Trying to Launch Aptik via Gksudo Aptik,cannot do that anymore since gksudo was Removed.
What are the Alternatives to gksudo?? Also to launch a Program Via GUI not in Terminal??

---

### Post by Frogs Hair on 2018-05-13
The following is a safe alternative.

```
sudo -H appname
``` Example: ```
sudo -H nautilus
```

---

### Post by kerry_s on 2018-05-13
pkexec is the new gksudo

---

### Post by monkeybrain20122 on 2018-05-13
> **kerry_s said:**
> pkexec is the new gksudo

It doesn't work without going through some[ ridculous hoops]("https://ubuntuforums.org/showthread.php?t=2225832"). This just encourages people to abuse sudo if it takes that much work to edit a config file.

sudo -H from Frogs Hair is the best solution.

---

### Post by HermanAB on 2018-05-14
Well, there is no reason for gksudo etc if you want to permanently enable a program to run as root.  Set the thing as SUID root with "chmod u+s filename" and get it on with your life.

---

