---
title: "value with df command"
date: 2008-02-26
forum: General Help
---

### Post by doc_holiday on 2008-02-26
When typeing "df -h" I get:

/dev/sda5  size: 243GB   used: 227GB  avail:3GB Use%99

Where is the rest of my diskspace gone?

---

### Post by pointone on 2008-02-26
A portion of your disk space is reserved for various reasons.

[http://boncey.org/2006_11_18_reclaiming_ext3_disk_space](http://boncey.org/2006_11_18_reclaiming_ext3_disk_space)

---

### Post by taurus on 2008-02-26
Check your trash bin.

```
du -h ~/.Trash
```
Also, check your /var too to make sure you don't have those log files filling up your disk space.

```
sudo du -h /var
```

---

