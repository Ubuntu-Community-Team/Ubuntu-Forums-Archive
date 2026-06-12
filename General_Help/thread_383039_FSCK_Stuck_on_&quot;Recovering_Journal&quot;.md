---
title: "FSCK Stuck on &quot;Recovering Journal&quot;"
date: 2007-03-12
forum: General Help
---

### Post by scott_ttocs46 on 2007-03-12
Hi all,

     One of my machines running ubuntu had a sudden power off. I could not mount one of the disks after rebooting. The disk that I can no longer mount is an ext3 disk.

I ran this:

```


administrator@zeus:~$ sudo fsck -v -p /dev/hdg1
Password:
fsck 1.38 (30-Jun-2005)
/dev/hdg1: recovering journal



```

Fsck is stuck. However, the pc is not frozen.

Am I doing something wrong? Is the check suppose to take longer than an hour or two?

Thanks,
Scott

---

### Post by scott_ttocs46 on 2007-03-12
This drive has severely critical information stored on it. Does anyone have a starting point or any ideas?

---

### Post by scott_ttocs46 on 2007-03-12
dmesg | tail yields:

```

[17193096.632000] hdg: lost interrupt
[17193126.632000] hdg: lost interrupt
[17193156.632000] hdg: lost interrupt
[17193186.632000] hdg: lost interrupt
[17193216.632000] hdg: lost interrupt
[17193246.632000] hdg: lost interrupt
[17193276.632000] hdg: lost interrupt
[17193306.632000] hdg: lost interrupt
[17193336.632000] hdg: lost interrupt
[17193366.632000] hdg: lost interrupt


```

---

### Post by scott_ttocs46 on 2007-03-12
The problem somehow corrected itself. Other posts suggest that the drive was overheated. I took off the server case and let it cool.

---

