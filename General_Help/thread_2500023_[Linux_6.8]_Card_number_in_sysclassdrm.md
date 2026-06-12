---
title: "[Linux 6.8] Card number in /sys/class/drm/"
date: 2024-08-19
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2024-08-19
I am running 22.04.4 LTS (i really need to get around to upgrading...)
Anyway on the kernel i was using this was returning [FONT=courier new]card0[/FONT], now on kernel [FONT=courier new]6.8.0-40-generic[/FONT] it returns [FONT=courier new]card1[/FONT]
```
ls /sys/class/drm/ | grep "^card[0-9]$"
```
Does the numbering now start at 1 or is it based on a slot number or something? i need to get [my script patched]("https://github.com/GM-Script-Writer-62850/do-it-yourself-bar/blob/master/examples/contrib/kde.diybar.amdgpu.sh"), but making it just work for me is one thing, but making it work for others is preferable

---

### Post by #&amp;thj^% on 2024-08-19
Pretty much yes, and this came about in 2023.
On 24.10 right now:
```
uname -r && ls /sys/class/drm/ | grep "^card[0-9]$"
6.10.0-15-generic
card1
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> ls -l /dev/dri/by-path/
total 0
lrwxrwxrwx 1 root root  8 Aug 19 09:57 pci-0000:05:00.0-card -> ../card1
lrwxrwxrwx 1 root root 13 Aug 19 09:57 pci-0000:05:00.0-render -> ../renderD128

```
```
ls /dev/dri/card*
/dev/dri/card1

```
```
 (ls /sys/class/drm/ | grep "^card[0-9]$" | wc -l)
1

```

---

### Post by pqwoerituytrueiwoq on 2024-08-20
thanks

---

### Post by #&amp;thj^% on 2024-08-21
If nVidia is involved that will change things:
```
(ls /sys/class/drm/ | grep "^card[0-9]$" | wc -l)
2

```
```
&#9492;&#9472;> ls /dev/dri/card*
/dev/dri/card1  /dev/dri/card2
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> ls -l /dev/dri/by-path/
total 0
lrwxrwxrwx 1 root root  8 Aug 21 12:13 pci-0000:01:00.0-card -> ../card2
lrwxrwxrwx 1 root root 13 Aug 21 12:13 pci-0000:01:00.0-render -> ../renderD129
lrwxrwxrwx 1 root root  8 Aug 21 12:13 pci-0000:05:00.0-card -> ../card1
lrwxrwxrwx 1 root root 13 Aug 21 12:13 pci-0000:05:00.0-render -> ../renderD128

```

---

