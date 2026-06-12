---
title: "Why doesnt windows 10 want to mount linux made ntfs drive?"
date: 2019-04-03
forum: General Help
---

### Post by iamtheeggman2 on 2019-04-03
Hi,

I've googled this but cant find an answer, I just keep on getting general partition create advice, anyway, there were two ntfs drives made while linux ubuntu was running and for some reason windows 10 wont mount them. Is this malicious windows behaviour to stop them from being easily read?

Thanks in advance

---

### Post by yancek on 2019-04-03
> there were two ntfs drives made while linux ubuntu was running

Do you mean 'drives' as in physical drives or 'drives' in windows speak meaning partitions on one drive?  How did you create the ntfs filesystems?  Using windows/Ubuntu?  Have you assigned a drive letter to the ntfs partitions in windows?

---

### Post by SeijiSensei on 2019-04-03
Usually I use

```
sudo mkfs -t ntfs [device]
```

in the rare case I need to create an NTFS drive.  [device] is something like /dev/sdb1, the first partition (1) on the second hard drive (b).

---

### Post by jdeca57 on 2019-04-03
> **iamtheeggman2 said:**
>  ... and for some reason windows 10 wont mount them. Is this malicious windows behaviour to stop them from being easily read?

Personally I'm certain there is no evil behaviour here but simply a question of declaring the drives in Windows, However, even if I still use Windows It has been a while since I dual booted (I use separate PC's) and I can't give a concrete answer how to solve this Windows question.

---

### Post by iamtheeggman2 on 2019-04-05
Hi,

The ntfs drive is a partition on a hdd, the partition was made in ubuntu, however when in windows 10 if you go to computer mangement you cannot assign it a drive letter or mount it, as those options are greyed out. Curiously, one of the two ntfs partions are avaiable for assigning a drive letter. Does you need to asign a drive letter to one before the next one? I wouldnt have thought so.

---

### Post by oldfred on 2019-04-05
Can you run chkdsk from Windows on the NTFS partition?

It used to be that testdisk created the XP version of NTFS. But since Windows 7 the NTFS partition boot sector structure was revised (boot using bootmgr not ntldr). And even if not bootable partition it may need newer structure. Chkdsk will update it, if run from a newer version of Windows.

---

### Post by rbmorse on 2019-04-05
> **iamtheeggman2 said:**
> Hi,

The ntfs drive is a partition on a hdd, the partition was made in ubuntu, however when in windows 10 if you go to computer mangement you cannot assign it a drive letter or mount it, as those options are greyed out. Curiously, one of the two ntfs partions are avaiable for assigning a drive letter. Does you need to asign a drive letter to one before the next one? I wouldnt have thought so.

The disk manager (diskmgmt.msc) may need administrator level permissions to assign drive letters.

---

### Post by iamtheeggman2 on 2019-04-06
Hi, curiously i was able to assign a drive lletter to one of the ntfs partitions, though wanted to mount the other one because thats where my data is. anyway, i stil cant mount the second ntfs partiton. curiously windows refers tot he olinux partiotion as "healthy" even thoguh it obviosly cant read it lol.

---

### Post by yancek on 2019-04-06
> curiously windows refers tot he olinux partiotion as "healthy" even thoguh it obviosly cant read it lol.

Nothing really 'curious' about it as it is by design of microsoft.  You can't read any data on a Linux partition without first installing some third party software designed for that purpose.

Have you run chkdsk on windows as suggested?  What happens when you try to assign a drive letter?  As suggested above, are you doing this as administrator?

---

