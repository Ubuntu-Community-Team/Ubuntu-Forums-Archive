---
title: "Thunar doesn't open removable media folder if there's spaces"
date: 2023-05-13
forum: General Help
---

### Post by ardouronerous on 2023-05-13
I'm running Xubuntu 22.04.

As you can see from the screenshot, my USB flash drive is named "USB DISK" and upon mount, Thunar doesn't want to open the USB folder, complaining that no directory exists because of the spaces.


Here's a screenshot from gnome-disks:


Is there anyway to fix this?

Thanks.

**UPDATE 1**: It's not just my USB that's being affected by this, but my whole  filesystem. As a test, I've made a folder called "My Stuff" on my home  directory and when I try to right click and "Open with File Manager,"  the same error happens:


**UPDATE 2**: I figured out a workaround to this issue:

I created a bash script and saved in it **/home/ardouronerous/.local/bin/thunar**.

```
#!/bin/bash
/usr/bin/thunar "$*"
```

This seems to have fixed the issue, not sure why it was an issue to begin with though.

---

### Post by idmbe on 2023-05-13
Hello,

Is USB new one ? 
Did you format it before ?
Did USB contains any files ?
Did you check it with other system ?

---

### Post by ardouronerous on 2023-05-13
> **idmbe said:**
> Hello,

Is USB new one ? 
Did you format it before ?
Did USB contains any files ?
Did you check it with other system ?

I bought this last year, and yes I formatted it and that was the name given to it after format. There's personal files in it. And I don't have any other OS to try it on.

BTW, this issue also happens in Xubuntu 20.04, I just upgraded to 22.04 last month.

---

### Post by aljames2 on 2023-05-13
It is better practice to avoid spaces in all naming conventions… files, directories, links, etc.  I use separator characters such as underscores or dashes if I want readability in a name.  Also, some words may be interpreted differently by the OS when it is a reserved keyword that means something different to the system.  USB may be one of those, not sure.

---

### Post by #&amp;thj^% on 2023-05-13
> **aljames2 said:**
> It is better practice to avoid spaces in all naming conventions&#8230; files, directories, links, etc.  I use separator characters such as underscores or dashes if I want readability in a name.  Also, some words may be interpreted differently by the OS when it is a reserved keyword that means something different to the system.  USB may be one of those, not sure.
+1
Does Gparted see it?

---

### Post by idmbe on 2023-05-13
plugin USB then type:
```
lsusb
```

then:
```
dmesg | grep -i USB
```

and share results with us

---

### Post by ajgreeny on 2023-05-13
What output do you get from command```
ls /media/$USER/
```when that USB disk is attached and mounted.

---

### Post by ardouronerous on 2023-05-13
Sorry, I should I have been clearer, while Thunar gives out the "**no such file or directory**" error, I can still manually get to the USB directory directly from Thunar, the problem only happens when I first plug in the USB or if I try to access the flash drive from gnome-disks.

> **idmbe said:**
> plugin USB then type:
```
lsusb
```

then:
```
dmesg | grep -i USB
```

and share results with us

Here's the result of **lsusb**:

```
lsusb
Bus 001 Device 002: ID 8087:8001 Intel Corp. Integrated Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 009: ID 090c:2000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Disk
Bus 002 Device 006: ID 2109:2813 VIA Labs, Inc. VL813 Hub
Bus 002 Device 004: ID 05c8:0374 Cheng Uei Precision Industry Co., Ltd (Foxlink) HP EliteBook integrated HD Webcam
Bus 002 Device 008: ID 2357:0109 TP-Link TL-WN823N v2/v3 [Realtek RTL8192EU]
Bus 002 Device 005: ID 093a:2533 Pixart Imaging, Inc. Gaming Mouse
Bus 002 Device 003: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 002 Device 002: ID 1a2c:212a China Resource Semico Co., Ltd USB Keyboard
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I think it's "**Bus 002 Device 009: ID 090c:2000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Disk**".

The result of **dmesg | grep -i USB**:

```
dmesg | grep -i USB
dmesg: read kernel buffer failed: Operation not permitted
```

> **1fallen said:**
> +1
Does Gparted see it?

I don't have GParted installed, but gnome-disks sees it.

> **ajgreeny said:**
> What output do you get from command```
ls /media/$USER/
```when that USB disk is attached and mounted.

Here's the result of **ls /media/$USER/**

```
ls /media/$USER/
'USB DISK'
```

---

### Post by ardouronerous on 2023-05-13
UPDATE:

It's not just my USB that's being affected by this, but my whole filesystem. As a test, I've made a folder called "My Stuff" on my home directory and when I try to right click and "Open with File Manager," the same error happens:

---

### Post by idmbe on 2023-05-13
That mean you should access as root to show results:
```
dmesg | grep -i USB
dmesg: read kernel buffer failed: [COLOR=#ff0000]Operation not permitted[/COLOR]
```
and to access as root type:
```
sudo su
```
then password

----
Ok now type this to see the permissions and users on the folder:
```
ls -la /home
```

---

### Post by ardouronerous on 2023-05-13
> **idmbe said:**
> That mean you should access as root to show results:
```
dmesg | grep -i USB
dmesg: read kernel buffer failed: Operation not permitted
```
and to access as root type:
```
sudo su
```
then password

----
Ok now type this to see the permissions and users on the folder:
```
ls -la /home
```

Thanks, but I'm not sure if this is related to my problem anymore though since it's not my USB is the problem, it's Thunar.


As you can see from the screenshot, as a test, I've created a folder on my home directory called "My Stuff". When I try to "Open with File Manager," it's the same result, error opening folder because of the spaces in "My Stuff".

---

### Post by ardouronerous on 2023-05-13
> **idmbe said:**
> Ok now type this to see the permissions and users on the folder:
```
ls -la /home
```

This is the result of **ls -la /home**:

```
ls -la /home
total 12
drwxr-xr-x  3 root       root       4096 Apr 23 08:52 .
drwxr-xr-x 20 root       root       4096 Apr 23 08:51 ..
drwxr-x--- 26 ardouronerous ardouronerous 4096 May 14 09:15 ardouronerous
```

---

### Post by idmbe on 2023-05-13
then try to install libexo-2-0 if you using xubuntu maybe something missing:
```
sudo apt install libexo-2-0
```

i hope it's fix after that

---

### Post by ardouronerous on 2023-05-13
> **idmbe said:**
> then try to install libexo-2-0 if you using xubuntu maybe something missing:
```
sudo apt install libexo-2-0
```

i hope it's fix after that

It's installed already. So, it's not that.

---

### Post by ardouronerous on 2023-05-13
I figured out a workaround to this issue:

I created a bash script and saved in it **/home/ardouronerous/.local/bin/thunar**.

```
#!/bin/bash
/usr/bin/thunar "$*"
```

This seems to have fixed the issue, not sure why it was an issue to begin with though.

---

### Post by aljames2 on 2023-05-14
That seems to be tricking the system to like the space in the device name.  Not the long-term implications of always having that in the background.  Others will know more on the viability of this tactic.

I would be curious if you have a separate USB with no data on it, and you label it the same as you have on your production usb, except replace the space with an underscore.  Would that work without having the script?

Adding:  Do not relabel your data usb until you first have a backup of it.  Using the wrong command can destroy your data.  If needed, we can help you if you decide you want to relabel the device.

---

### Post by #&amp;thj^% on 2023-05-14
I'm curious as to how this all cropped up in the first place.
Would be nice to see your ".bashrc" file as well...
And if you remove your added script " /home/ardouronerous/.local/bin/thunar."
Then insert your "USB DRIVE" and then run:
```
thunar -q; thunar .

```
And:
```
ls /media/$USER/
1TB-BU  2TB_Back-up  Back-ups

```

---

### Post by ardouronerous on 2023-05-14
Found the culprit.

It was an hold over from my 20.04 backup, I backed up my home folder from 20.04 and I made a bash script for File Manager that had this code in it:

```
/usr/bin/thunar '$*'
```

So, I guess when I made my new bash script it overrode the previous bash script.

---

### Post by ajgreeny on 2023-05-15
I'm still not able to figure out why you needed to make any changes, eg, a bash script, in order to get thunar working as it would normally.

Aside from that, it does point out the advisability of making sure all file and folder names are free of empty spaces; it becomes second nature very quickly to add an underscore or dash rather than a space.

---

