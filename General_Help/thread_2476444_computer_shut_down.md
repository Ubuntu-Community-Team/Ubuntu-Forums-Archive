---
title: "computer shut down"
date: 2022-06-26
forum: General Help
---

### Post by vermontgirl on 2022-06-26
I am new to this forum so bear with me.  I just started using Ubuntu and if I am reading the newspaper or playing a game my computer just shuts off.  When I restart it I have to open it up in recovery mode and I can be on the computer for about a half hour to an hour and it will shut down again.

---

### Post by TheFu on 2022-06-27
The description is a little too vague for anyone to help.  Act like we are 5 yrs old and explain EXACTLY what you mean. Please.

Computers shouldn't lock up or shutdown unless we tell them to do that.
```
$ uptime
 09:58:22 up 8 days,  1:44, 
```

That computer has been running a little over 8 days.  Some patches on Saturday had me reboot most of my other systems, so they haven't been 'up' as long:
```
$ uptime
 09:59:32 up 2 days,  1:12, 
```
is for my main desktop, but it is very stable and only reboots/shuts down at my request unless there is a hardware problem.

Hardware issues are often logged, so we just need to look at the log files.  If you web-search for "ubuntu logs", there are articles to explain where they are and how to search them.  Don't have your eyes gloss over. Reading logs is something you must do, unless you want to pay someone $100/hr to do it for you.

---

### Post by cyberkingdom on 2022-06-28
Sounds possible you could be having a hardware issue. Cant promise anything but computers don't just turn off.

---

### Post by ajgreeny on 2022-06-28
Is this a desktop or laptop?

Could it be overheating and shutting down to avoid hardware damage?
Laptops overheating is quite common and usually obvious particularly if used on your knees/lap.

---

### Post by TheFu on 2022-06-28
The latest Linux kernels, including what Ubuntu uses have added an OOM feature to close programs when memory is tight.  Previously, it was decided by kernel developers  that checking whether a memory request was possible or not was too slow to actually be performed. Their solution was to always return "OK" - for any memory allocation request. After reading how much faster a computer was that worked in this way, I have to say, I agree. It was a huge difference in performance and as long as we didn't allow low memory situations to happen, there weren't any issues.

Anyway, [https://www.omgubuntu.co.uk/2022/06/ubuntu-22-04-systemd-oom-killing-apps](https://www.omgubuntu.co.uk/2022/06/ubuntu-22-04-systemd-oom-killing-apps) tries to explain the issue in 22.04. Appears the big complaint is that the OOM system kills large programs, but doesn't provide any visual clue to users. The application is just gone.

I doubt this is related to a computer deciding to cleanly shutdown, if that's what is happening. We still don't know.

---

