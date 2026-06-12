---
title: "Help creating an alias"
date: 2015-03-05
forum: General Help
---

### Post by mike300 on 2015-03-05
Hi everyone, I was wondering if anyone could help me out with a command quick. I have to create an alias that displays only filesystems that are mounted and contain an ext4 filesystem. Any help would be greatly appreciated

---

### Post by oldfred on 2015-03-05
Are you interested in links or bind, or an icon on desktop.

If linking:
 
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by slickymaster on 2015-03-05
File systems get mounted in **/etc/fstab** so you can```
alias name_of_alias='grep ext4 /etc/fstab'
```

---

### Post by btindie on 2015-03-05
You can get a list of _mounted_ ext4 filesystems with
```
alias name_of_alias='awk '\''$3 == "ext4" {print $0}'\'' /proc/mounts'
```

---

### Post by steeldriver on 2015-03-05
```

alias findext4mnt='findmnt -t ext4'

```
;)

---

