---
title: "can not mount windows partitions"
date: 2017-10-18
forum: General Help
---

### Post by miodragmilincic on 2017-10-18
Hi, I'm kinda new to Linux, need some help. Have dual boot Ubuntu/Win10, when restart from Windows into Ubuntu I can access C: and D: (Windows NTFS partitions), but when I shut down Windows and boot Ubuntu, no access to those partitions.
This is what I get when click on "400 GB Volume" which D: partition with data
[IMG]https://prnt.sc/gyvz6k[/IMG][https://prnt.sc/gyvz6k](https://prnt.sc/gyvz6k)

---

### Post by leunam12 on 2017-10-18
Disable hibernation in windows.

[https://support.microsoft.com/en-hk/help/920730/how-to-disable-and-re-enable-hibernation-on-a-computer-that-is-running](https://support.microsoft.com/en-hk/help/920730/how-to-disable-and-re-enable-hibernation-on-a-computer-that-is-running)

---

### Post by miodragmilincic on 2017-10-26
I did, and fast start-up(or whatever it's called), now I can access D: drive, but not C:
[http://i.prntscr.com/NM2-O622Qo_GH2oY6OgR5g.png](http://i.prntscr.com/NM2-O622Qo_GH2oY6OgR5g.png)

---

### Post by westie457 on 2017-10-26
Boot into Windows and open an 'Administrator Command Prompt' type and run. ```
chkdsk /r c:
```
Follow the on screen instructions.

---

### Post by miodragmilincic on 2017-10-26
thx bro, will try

---

### Post by miodragmilincic on 2017-10-27
> **westie457 said:**
> Boot into Windows and open an 'Administrator Command Prompt' type and run. ```
chkdsk /r c:
```
Follow the on screen instructions.

I did it, and now it's not even listed in the left menu (C: drive)

---

