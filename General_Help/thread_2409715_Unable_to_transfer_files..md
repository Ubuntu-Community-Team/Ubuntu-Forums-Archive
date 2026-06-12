---
title: "Unable to transfer files."
date: 2019-01-05
forum: General Help
---

### Post by silvaas on 2019-01-05
I'm having a problem whenever i try to transfer files to any pendrive, it starts well but it hangs at the end, usually near 97%, i've tried fat and ntfs and still doesn't work. Any help is appreciated.

---

### Post by clementc on 2019-01-05
Hi [**[COLOR=#000000]silvaas[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115592"),

Can you please open a Terminal window (Ctrl + Alt + T) and run the following commands:

```
sudo nano /etc/sysctl.conf
```

Add the following two lines at the end of the file:

```
vm.dirty_background_ratio = 5
vm.dirty_ratio = 10
```

Save the changes by pressing Ctrl + X, then Y and Enter.

Finally, run the following command and try transferring files from/to your flash drive again (no need to reboot your system):

```
sysctl -p
```

---

### Post by silvaas on 2019-01-06
It worked, thanks! Could you breakdown these commands you've listed, what they do to the system?

---

### Post by silvaas on 2019-01-06
[COLOR=#000000]It worked, thanks! Could you breakdown these commands you've listed, what they do to the system?[/COLOR]

---

### Post by clementc on 2019-01-06
Hi [**[COLOR=#000000]silvaas[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115592"),

According to the [man page]("http://man7.org/linux/man-pages/man5/sysctl.conf.5.html"), sysctl.conf is a simple file containing sysctl values to be read in and set by sysctl. [sysctl]("http://man7.org/linux/man-pages/man8/sysctl.8.html") is used to modify kernel parameters at runtime. According to [this page]("https://www.cyberciti.biz/faq/linux-kernel-tuning-virtual-memory-subsystem/") (and for lack of better words), vm.dirty_background_ratio contains a percentage of total system memory, the number of pages at which the pdflush background writeback daemon will start writing out dirty data. vm.dirty_ratio contains a percentage of total system memory, the number of pages at which a process which is generating disk writes will itself start writing out dirty data. sysctl -p just reloads the sysctl.conf settings in memory (live changes) so that you do not need to reboot your system for them to be applied.

So essentially what these commands do is to tell the system when (at what percentage) to write to the disk rather than caching too much data in memory. Dirty data refers to data cached in memory but not yet written to disk.

Hope this helps.

---

