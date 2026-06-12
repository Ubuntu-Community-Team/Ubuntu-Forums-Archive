---
title: "Errors at boot - where do I look ?"
date: 2020-05-22
forum: General Help
---

### Post by oygle on 2020-05-22
This morning when I booted up, it came up with the grub options screen for some reason. I selected the default, then some message , I think it was about "AVI" or similar. Do I look in .xsession-errors or will thie message be in some log file ?

---

### Post by Bashing-om on 2020-05-22
oygle; Hey -

> 
.xsession-errors or will thie message be in some log file

Have a read:
```

journalctl -b -0 ##shows messages from the current boot
journalctl -b -1 ##from the previous boot, if you want to compare

```
joirnalctl has many switches for filtering for specific purposes.

[INDENT]hope this helps
[/INDENT]

---

### Post by oygle on 2020-05-22
> **Bashing-om said:**
> 
Have a read:
```

journalctl -b -0 ##shows messages from the current boot
journalctl -b -1 ##from the previous boot, if you want to compare

```
joirnalctl has many switches for filtering for specific purposes.

Great, thanks for the tip there "Bashing-om". I ran the command for today o/p to a file, then the same for yesterday. Way too many differences, mostly date/time of course. But I noticed the size for yesterday was 170K and the size for today was 340K , so comparing and it is a heap of commands from Baloo. For example ..

> May 23 08:11:23 oygle-Inspiron-3542 baloo_file[1324]: KDE Baloo File Indexer has reached the inotify folder watch limit. File changes will be ignored.

So the doc at [https://loggedfixes.com/tech/software/ubuntu/kde-baloo-file-indexer-has-reached-the-inotify-folder-watch-limit-file-changes-will-be-ignored/](https://loggedfixes.com/tech/software/ubuntu/kde-baloo-file-indexer-has-reached-the-inotify-folder-watch-limit-file-changes-will-be-ignored/) was helpful ..

```
$ balooctl status
```

> Baloo File Indexer is running
Indexer state: Idle
Total files indexed: 297,910
Files waiting for content indexing: 0
Files failed to index: 0
Current size of index is 430.94 MiB

```
cat /proc/sys/fs/inotify/max_user_watches
```

> 8192

so maybe I need to set inotify watchers to a big number ?? I pasted the output of the **journalctl** command for today at [https://paste.ubuntu.com/p/zC4FM5QKtv/](https://paste.ubuntu.com/p/zC4FM5QKtv/)

Thanks for your help.  :)

---

### Post by oygle on 2020-05-22
Is the **answer** provided at [https://askubuntu.com/questions/1137733/baloo-running-amok-kubuntu-19-04](https://askubuntu.com/questions/1137733/baloo-running-amok-kubuntu-19-04) the correct method to fix this ?

---

### Post by Bashing-om on 2020-05-22
oygle; Well -

I do not run KDE and have no experience with baloo. I so refrain from a comment :)

As to your log file there shows some things you might want to address:
> 
- /etc/thermald/thermal-conf.xml
- sysfs write failed /sys/devices/virtual/powercap/intel-rapl/intel-rapl:0/enabled
- config: unknown key 'ethernet.cloned-mac-address' in section [device-mac-addr-change-wifi] of file '/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf'
- mpd.service: Failed with result 'exit-code'. >> Failed to start Music Player Daemon.
- Giving up on [https://database.clamav.net](https://database.clamav.net)... >> !Update failed for database: main


However, they are all beyond the scope of this thread - If you require assistance with any then open new thread(S).
 
[INDENT][INDENT]see, reading is good
[/INDENT][/INDENT]

---

### Post by oygle on 2020-05-22
> **Bashing-om said:**
> As to your log file there shows some things you might want to address:

Okay thanks, I will follow those up.  Thanks for your help.

---

### Post by Bashing-om on 2020-05-22
oygle; Welcome as always -
However, I did little to help. But, a look over the shoulder is sometimes a good thing.

-the process of learning-

---

