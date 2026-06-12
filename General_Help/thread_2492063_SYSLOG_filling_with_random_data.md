---
title: "SYSLOG filling with random data"
date: 2023-10-29
forum: General Help
---

### Post by Kenzo on 2023-10-29
Ubuntu 20.04.6 LTS
Intel® Core&#8482; i5-8600 CPU @ 3.10GHz × 6 

The system was idle. Suddenly the disk drive became very active. SYSLOG was filling up with hundreds entries of ...

 ```
gnome-software[2969]: ignoring percentage 99% -> 95% as going down...
 gnome-software[2969]: ignoring percentage 99% -> 97% as going down...
 gnome-software[2969]: ignoring percentage 99% -> 95% as going down...
 gnome-software[2969]: message repeated 2 times: [ ignoring percentage 99% -> 95% as going down...]
 gnome-software[2969]: ignoring percentage 99% -> 98% as going down...
 gnome-software[2969]: ignoring percentage 99% -> 95% as going down...
 gnome-software[2969]: ignoring percentage 99% -> 98% as going down...
 gnome-software[2969]: ignoring percentage 99% -> 96% as going down...
 gnome-software[2969]: ignoring percentage 99% -> 98% as going down...
 gnome-software[2969]: ignoring percentage 99% -> 96% as going down...
 gnome-software[2969]: ignoring percentage 99% -> 98% as going down...
 gnome-software[2969]: ignoring percentage 99% -> 96% as going down...
 gnome-software[2969]: message repeated 3 times: [ ignoring percentage 99% -> 96% as going down...]
 gnome-software[2969]: ignoring percentage 99% -> 97% as going down...
 gnome-software[2969]: message repeated 4 times: [ ignoring percentage 99% -> 97% as going down...]
 gnome-software[2969]: ignoring percentage 99% -> 98% as going down...
 gnome-software[2969]: message repeated 5 times: [ ignoring percentage 99% -> 98% as going down...]

(date/time/UID removed)

```
Any idea what is causing that?

---

### Post by MAFoElffen on 2023-10-29
'gnome-software' checking for updates... Normal.

Please edit your last post, to add Code Tag around your raw output... See the CODE Tags link in my Signature line. "Forum Posting policy" = #3 in the "Posting Guidelines" link in Signature line.

---

### Post by Kenzo on 2023-10-30
Thanks very much for your reply
Are you suggesting it is caused by "gnome-software' checking for updates"? You may be correct but this is the first time I have seen it in the logs.
Regarding tags, this is text output from the log file. Its not [code].  If I tagged it as [code] wouldn't that give a wrong impression?
Thanks again

---

### Post by kinddolphin8827 on 2023-10-30
It could possibly be that your hard disk drive is coming to the end of it mean time between failure specification which  means that you might want to consider  taking backups of you important data. I'd suggest that you opt for a hard drive that is either market towards those that are gamer or a high performance applications like graphics design or video production which may cost a little more than consumer aimed hard drives but  that higher costs is worth it if you use your computer regularly and need the reliability of near 99.9% uptime.

---

### Post by Kenzo on 2023-10-30
Thanks for your suggestion.

---

### Post by Doug S on 2023-10-30
> **Kenzo said:**
> Regarding tags, this is text output from the log file. Its not [code].  If I tagged it as [code] wouldn't that give a wrong impression?No. It merely formats it properly. All experienced users here use code tags around log text.

---

### Post by Holger_Gehrke on 2023-10-30
One thing to note: gnome-software will **not** stop running when you close its window (no, that's not a bug, it's intentional). So if you're sure you are not going to do any further installations or removal of software you need to kill it from the command line ('pkill gnome-software' has always worked for me ...).

Holger

---

### Post by ajgreeny on 2023-10-30
So that you can see the difference in text layout I have added Code Tags to your original post.
To add them to your own posts in future see **Code-Tags** in my signature below and please use for all terminal output that you copy back here to a thread.

---

### Post by Kenzo on 2023-11-17
Thank you. That is very helpful. Now I understand.

---

