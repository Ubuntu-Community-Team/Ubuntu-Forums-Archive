---
title: "BOOT &quot;random&quot; time destroyed"
date: 2024-07-07
forum: General Help
---

### Post by megsoconnor on 2024-07-07
I need to know what is the real problem, my ssd ? a software usage shoot my boot ?
i already post a thread on it, and i resolve it twice, but the problem spawn randomly. specially after launching discord client.... i haven't the pb when i use the web client of discord.
see the pastebin from, the two problem period, if you understand where is the problem.

[https://paste.ubuntu.com/p/smnFPfx8jh/](https://paste.ubuntu.com/p/smnFPfx8jh/)
[https://paste.ubuntu.com/p/yRzcGfn4Bg/](https://paste.ubuntu.com/p/yRzcGfn4Bg/)

i am passing from a working boot a day , to a rescue boot mode the day after.... The installed advanced boot option from my 6.8.x-36 kernel work when i use it. But refuse to load the same default boot...
some times if i disconnect the Ethernet cable it boot normally. why at boot time my pc want to get something to the web ? seems to be a boot corruption. By what ?

thanks to your returns.

---

### Post by tea for one on 2024-07-07
With reference to the second report [https://paste.ubuntu.com/p/yRzcGfn4Bg/](https://paste.ubuntu.com/p/yRzcGfn4Bg/), the following entries in /etc/fstab (lines 215 & 216) do not display any corresponding disks in the fdisk -l output (line 125)
```
UUID=7EDB4CBE3BA423B2 /media/megs/DATA ntfs-3g rw,auto,users,exec,nls=utf8,umask=002,gid=100,uid=1000    0   0
UUID=2E8082E28082B03F /media/megs/PeekBox ntfs default,auto,umask=002,gid=100,uid=1000    0   0
```
Your boot configuration seems to be looking for disks which are not present.
I suggest removing these two lines from /etc/fstab.

Any improvement in the boot process?

---

### Post by megsoconnor on 2024-07-08
yep, i put noauto to peekbox line instead of auto, that resolve the pb at this time.
I can understand the boot is morre longer, But i do not understand why it trying to boot on a usb dis prio than the habitual one.....

---

