---
title: "Fun with deleting on of 2 partitions"
date: 2022-11-12
forum: General Help
---

### Post by raleigh3 on 2022-11-12
I started out with 2 partitions with versions UM 18.04 and 20.04.

I used os-uninstaller and deleted the partition with UM 18.04.

It now  boots into UM 20.04 which is what I want.

But it now has a dev/sda1 and dev/sda2.

It looks like dev/sda1 has UM 20.04 on it which is working.

There is a large directory called deleted_os. It contains files from my 18.04 version.

What do I do now?

Thanks.

[ATTACH=CONFIG]291245[/ATTACH][ATTACH=CONFIG]291246[/ATTACH]

---

### Post by oldfred on 2022-11-12
[https://askubuntu.com/questions/1440430/0s-uninstaller-and-removing-one-of-two-partitions](https://askubuntu.com/questions/1440430/0s-uninstaller-and-removing-one-of-two-partitions)

Last install normally is the default boot system.
But if removing a system, you need to reinstall grub from system you want to keep first to make sure it is default boot.

---

