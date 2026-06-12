---
title: "display running process of firefox.."
date: 2008-02-13
forum: General Help
---

### Post by Mia_tech on 2008-02-13
how do I display the running process of firefox without running top and having to find the firefox-bin 


thanks

---

### Post by vambo on 2008-02-13
If you mean the pid, then as follows

```
ps -e | grep firefox
```

---

### Post by Mia_tech on 2008-02-13
thanks what I needed....

and how could I find the process that is using more memory.... the memory on my pc is running low, and I have 1G of memory... some process is hugging my memory

---

### Post by vambo on 2008-02-13
```
top -p <pid>
```

---

### Post by tangibleorange on 2008-02-13
In general, there are two commands to find out system memory usage. Try
> top

for a command-line based overview, or in GNOME, it's:
> gnome-system-monitor

I'm afraid I don't know what it is in KDE. I suppose you could try kde-system-monitor...

---

### Post by Mia_tech on 2008-02-13
> **tangibleorange said:**
> In general, there are two commands to find out system memory usage. Try


for a command-line based overview, or in GNOME, it's:


I'm afraid I don't know what it is in KDE. I suppose you could try kde-system-monitor...

for KDE is KSysGuard

---

