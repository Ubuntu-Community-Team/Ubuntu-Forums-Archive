---
title: "Read Ntfs partition in edgy"
date: 2006-11-23
forum: General Help
---

### Post by Arbiter on 2006-11-23
Hi all,

i just purchased a new laptop (Acer Aspire 5672WLMi) and dual booted Windows XP Pro and Ubuntu 6.10.  So far I haven't been able to read my NTFS windows partition in Ubuntu.  I can mount it, but when I try and access it, it gives me an access denied message.  How can I circumvent this?

Thanks

---

### Post by taurus on 2006-11-23
Did you mount it by hand?  What are the output of these comands from a terminal then?

Applications -> Accessories -> Terminal:

```
sudo fdisk -l
cat /etc/fstab
df -l
```

---

### Post by TigerWolf on 2006-11-23
It all depends how you mount it. Try this - 
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
or 
[http://ubuntuforums.org/archive/index.php/t-1886.html](http://ubuntuforums.org/archive/index.php/t-1886.html)

---

