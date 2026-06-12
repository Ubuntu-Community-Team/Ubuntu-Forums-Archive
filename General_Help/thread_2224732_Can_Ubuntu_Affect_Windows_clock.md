---
title: "Can Ubuntu Affect Windows clock?"
date: 2014-05-17
forum: General Help
---

### Post by daniell59 on 2014-05-17
I have Ubuntu 12.04 64 on one HD and Vista on the other one. I have no clock problems on Ubuntu, but when I boot up Windows the clock has the wrong time. The minutes are correct, but it is several hours fast. I heard it suggested that Linux is somehow interfering with the windows clock. Is this plausable? Yes, I just changed the CMOS battery. Any insight into this problem will be appreciated.

---

### Post by Mark Phelps on 2014-05-17
BOTH Windows and Linux can change the SYSTEM clock -- which is what they are both probably using.  The way to have them both have the same time is to stop Ubuntu from using UTC -- which it uses by default. But when this is the case, the times reported are usually off by several hours, not several minutes.

---

### Post by Impavidus on 2014-05-17
Open the file **/etc/default/rcS** in a text editor with root permission. There will be a line with **UTC=yes**. Change it into **UTC=no** and save the file.

Both Linux and Windows use the same system clock. Windows assumes it's set to local time, Linux assumes it's set to UTC.

---

### Post by daniell59 on 2014-05-17
So what do I do?

---

### Post by daniell59 on 2014-05-17
> **Impavidus said:**
> Open the file **/etc/default/rcS** in a text editor with root permission. There will be a line with **UTC=yes**. Change it into **UTC=no** and save the file.

Both Linux and Windows use the same system clock. Windows assumes it's set to local time, Linux assumes it's set to UTC.

Thanks, I will now have to learn text editing in Linux.

---

### Post by pfeiffep on 2014-05-17
@daniell59, you might try to use gedit (or whatever text editor installed on your linux system)

```
gksudo gedit  /etc/default/rcS
``` here's the section you'l want to change 
```
# assume that the BIOS clock is set to UTC time (recommended)
UTC=no
```

The '#' symbol defines a comment; simply replace no with yes

---

### Post by daniell59 on 2014-05-18
> **pfeiffep said:**
> @daniell59, you might try to use gedit (or whatever text editor installed on your linux system)

```
gksudo gedit  /etc/default/rcS
``` here's the section you'l want to change 
```
# assume that the BIOS clock is set to UTC time (recommended)
UTC=no
```

The '#' symbol defines a comment; simply replace no with yes

I checked it. It already says yes.

---

### Post by The Cog on 2014-05-18
You need to change it to say "UTC=no". 
Only root can change that file, so you need to run the editor as root. This command will do the trick:
```
gksudo gedit /etc/default/rcS
```

---

### Post by daniell59 on 2014-05-18
> **The Cog said:**
> You need to change it to say "UTC=no". 
Only root can change that file, so you need to run the editor as root. This command will do the trick:
```
gksudo gedit /etc/default/rcS
```

Thanks for your help. It is now clear to me. One question. I very rarely use Windows. Would I be better off making the change there? Are there any disadvantages that I will experience in Ubuntu after making the change?

---

### Post by Mark Phelps on 2014-05-18
> I very rarely use Windows. Would I be better off making the change there? 

Basically, no. Why? Because the next time you boot into Windows, it will reset the clock because Windows and Linux are using different timekeeping schemes.

If you fix it in Linux, then it will be the same for both Windows and Linux.

---

### Post by Luke M on 2014-05-18
This page may be helpful:

[http://www.cl.cam.ac.uk/~mgk25/mswish/ut-rtc.html](http://www.cl.cam.ac.uk/~mgk25/mswish/ut-rtc.html)

---

### Post by daniell59 on 2014-05-18
Thanks a lot. That did it.

---

