---
title: "System program problem detected"
date: 2020-02-20
forum: General Help
---

### Post by Philip_Edwards on 2020-02-20
Hi Group,

I'm seeing an error message on my screen quite frequently.

System program problem detected

Then there is the option to report the problem....which I do.

Should I be worried?

Phil

---

### Post by ajgreeny on 2020-02-20
Probably not something to be very concerned about, but to give you more help we need many more details about the hardware and software you are using.

To get useful info about your hardware please show us the output of ***inxi -Fxz*** in terminal.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by CatKiller on 2020-02-20
The crash reports are stored in /var/crash if you want more insight into which application is crashing, and what information is sent. The system is supposed to only notify you once per crash, but sometimes it gets confused and tells you over and over about the same crash. In those circumstances you can simply delete the crash report to stop it from doing that.

---

### Post by cmcanulty on 2020-02-20
Or to never see the notice again go to 

```
/etc/default/apport 
``` as root and change
```
 enabled=1 to enabled=0
```

---

### Post by sdsurfer on 2020-02-20
I have been looking for an answer to this one for quite some time. The system appears to function normally after the warning, but I have found no definitive answer to the exact cause. What I can gather is that there are multiple causes for it, the first thread below links to a solution that was not my case.

Recent thread, same issue:
[https://ubuntuforums.org/showthread.php?t=2436311](https://ubuntuforums.org/showthread.php?t=2436311)

My original thread, with info from my crash logs:
[https://ubuntuforums.org/showthread.php?t=2425037](https://ubuntuforums.org/showthread.php?t=2425037)

As suggested above, logs (crash, apport, syslog) will help, but may or may not lead you to a solution.

---

### Post by Philip_Edwards on 2020-02-20
Thanks everyone,
[B][I]inxi -Fxz   couldn't get that to work.

[/I][/B]

Thanks for your help. I have the feeling that I'm over-worrying. Maybe it will be more help if I just keep sending error reports?

---

### Post by ajgreeny on 2020-02-20
What do you see when running*** inxi -Fzx***?

Just saying "couldn't get that to work" is not at all helpful.

---

