---
title: "PC Crashing"
date: 2013-10-12
forum: General Help
---

### Post by TimEnid on 2013-10-12
How can i find out what is causing my PC to crash. about 10 minutes after i boot up and start working, the PC freezes and i have to reboot. I am not sure what the cause is or how to figure out why its happening. I did a Memtest and everything was fine on that front. Any suggestions?

---

### Post by whitesmith on 2013-10-12
What version of Ubuntu? To find out run and post results of:```
uname -a
```

---

### Post by TimEnid on 2013-10-12
> **whitesmith said:**
> What version of Ubuntu? To find out run and post results of:```
uname -a
```

```
Linux tim 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 20:03:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by whitesmith on 2013-10-12
OK. Your kernel is up to date and hosted on a relatively fast system. I think you have a number of things to rule out. Has this problem persisted ever since installation of the OS? If not, what did you do right before it first appeared? The system logs are your best friend in a case like this.

---

### Post by TimEnid on 2013-10-12
Its been happening for about 2 weeks now. I'm getting the feeling it has something to do with Chrome, it seems be open everytime i crash. Where can i get system logs from?

---

### Post by Sef on 2013-10-12
> [COLOR=#000000]I'm getting the feeling it has something to do with Chrome,[/COLOR][COLOR=#000000]  

How did you download Chrome?  You could try installing it and see if the problem still occurs.

[/COLOR]> [COLOR=#000000]Where can i get system logs from?[/COLOR]

[http://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located](http://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located)

---

### Post by TimEnid on 2013-10-12
im using chromium. whats the best way to install it?

---

### Post by whitesmith on 2013-10-12
Easiest for Chromium: go through Ubuntu Software Center. Note that Chrome and Chromium aren't quite the same. Chromium is 100% open-szource.

---

