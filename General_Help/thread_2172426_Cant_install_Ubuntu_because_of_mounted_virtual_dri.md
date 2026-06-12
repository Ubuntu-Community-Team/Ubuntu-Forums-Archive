---
title: "Cant install Ubuntu because of mounted virtual drive"
date: 2013-09-04
forum: General Help
---

### Post by KidneyBean on 2013-09-04
I am unable to install any version of Ubuntu because of a mounted virtual drive that I can't disappear from my system. 

In Windows, I went into the device manager and manually uninstalled the virtual drive. After restarting the system however, the virtual drive keeps coming back. 

The point where I get stuck in terms of the Ubuntu install is right after I choose whether I want to install Ubuntu alongside Windows or pick from other install options. I'm then presented with a pop up that informs me of the inability to install because of the mounted drive that just won't seem to go away.

---

### Post by KidneyBean on 2013-09-05
Ok, so I managed to fully get rid of the virtual drive that I thought was causing the issue. However, the same error occurs during install.

Here's the official spit-out I get on my screen:

> The installer needs to commit changes to partition tables, but cannot do  so becaue partitions on the following mount points could not be  unmounted:

/cdrom

The bad thing is that I done did a little Googling and found that several others have had the same issue, but no one with 13.04. 

So far, none of the limited suggestions I've found do the trick. 

I am running an Acer Aspire s3 ultrabook in case it matters.

---

### Post by Impavidus on 2013-09-06
I don't know much about Windows, but I don't think a Windows virtual drive can influence Ubuntu in any way.

Before you install, could you check which partitions are mounted? You can open a terminal and use```
mount
```
And i assume you didn't mount anything manually during the live session, did you? Do you install from a dvd or from a USB memory? Is there anything in your optical disc drive? Do you have any other applications running, that might prevent a filesystem from being unmouted? The mention of */cdrom* suggests an optical disc is mounted.

---

### Post by KidneyBean on 2013-09-06
Hmm, good suggestion about checking what is mounted via the terminal before install. I'll report back in a few with findings.

---

