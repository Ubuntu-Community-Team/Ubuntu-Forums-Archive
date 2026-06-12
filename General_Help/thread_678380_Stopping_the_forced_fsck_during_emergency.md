---
title: "Stopping the forced fsck during emergency"
date: 2008-01-25
forum: General Help
---

### Post by wersdaluv on 2008-01-25
I am aware that I can increase the number of boots when forced fsck comes out and that I can shut my computer down. I also can sudo touch /fastboot to instruct my computer not to fsck when I boot again. 

It's just that, there are emergency cases when I immediately need my computer and the forced fsck comes out. In times like that, the forced fsck is very annoying.

In windows, there's a press any key to bypass the forced fsck. AFAIK, there is no such feature in Linux. Is there? If so, can you tell me how to do it? :D If not so, what can we do? :D

:KS

---

### Post by accatagon on 2008-01-25
Ctrl+c(default method of killing processes in terminal)  might work. I vaguely remember doing that in Debian, but Debian is not Ubuntu, and it is only vaguely. You will also have to put up with the temporary freeze before it actually tells you fsck is doing it's thing.

---

### Post by wersdaluv on 2008-01-25
> **accatagon said:**
> Ctrl+c(default method of killing processes in terminal)  might work. I vaguely remember doing that in Debian, but Debian is not Ubuntu, and it is only vaguely. You will also have to put up with the temporary freeze before it actually tells you fsck is doing it's thing.

Btw, if ctrl+c actually works, people must take not that they should stop fsck when it is already running.

---

### Post by accatagon on 2008-01-25
I tried it. It doesn't seem to work. I think it did on Debian, but I could be crazy. There is a bug report filed on this [here]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/22460"). Sorry for the misinformation.

---

### Post by y-lee on 2008-01-25
You might want to consider using [AutoFsck]("https://wiki.ubuntu.com/AutoFsck"). This goves you the option to have the disk checks occur on shutdown instead of bootup :) And addds a menu item to **System --> Administration**  called **Periodic Disk Checking** where one can set these options.

---

### Post by accatagon on 2008-01-25
You could try[ autofsck]("https://wiki.ubuntu.com/AutoFsck")

---

