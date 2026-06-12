---
title: "Bootup problem"
date: 2014-12-05
forum: General Help
---

### Post by Old Newcomer on 2014-12-05
I had Ubuntu 12.04 and Windows XP dual booted on a Dell GX270 desktop computer.
Had been using in Ubuntu and had just closed all programs but computer at idle.
Was hit by a short sharp power cut.
Computer will boot up in Windows but not Ubuntu.
Cannot retrieve information from Ubuntu.
Can someone offer a solution please?

---

### Post by eight.coffee.beans on 2014-12-05
Have you tried booting from Ubuntu USB/CD and see if you can access Ubuntu partition?
If not, then try it and see if you can repair automatically the partition by reinstalling Ubuntu.

---

### Post by Old Newcomer on 2014-12-05
Thank you for the reply, I will try that but I don't want to lose my information on that partition.

---

### Post by eight.coffee.beans on 2014-12-05
> **Old Newcomer said:**
> Thank you for the reply, I will try that but I don't want to lose my information on that partition.

You won't lose your information as long as you don't install OS on that partition or format it.
Browsing with Ubuntu USB should not make any data-loss.

---

### Post by Old Newcomer on 2014-12-06
Sorry to say this problem is now beyond my capabilities.
Computer seems to have died altogether.
Thanks for help.

---

### Post by oldfred on 2014-12-06
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Old Newcomer on 2014-12-10
Hello All,
thank you for your help in this matter, but as Iam a computer dummy it got beyond me.
I took my hard drive to a retired computer repairer yesterday and after some time found my files imbedded in the Windows file system and recovered my data.
Still using Ubuntu on a different computer.

Happy Christmas to everyone,  Neil.

---

