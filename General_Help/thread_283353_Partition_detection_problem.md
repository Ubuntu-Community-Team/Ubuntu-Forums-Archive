---
title: "Partition detection problem"
date: 2006-10-24
forum: General Help
---

### Post by napster7 on 2006-10-24
Hi

I have installed ubuntu on my laptop. I have a partition which i formatted in windows. Ubuntu is not recongnizing that partion. When i click on the properties of that file it shows that as a desktop configuration file. It is not mounting that partition. can someone help me to make this work?

Thanks

---

### Post by kidders on 2006-10-24
Hi there,

What filesystem does Ubuntu see? What happens when you try to mount it manually from a terminal window?

---

### Post by Kateikyoushi on 2006-10-24
You can mount it by following these steps. [LINK]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

If you get stuck copy here the output of this comand.

```
sudo fdisk -l
```

---

### Post by napster7 on 2006-10-24
Thanks for your help guys...i am able to mount it now...jus followed those steps.

thanks a lot

---

