---
title: "deleting Windows need to change Boot to Ubuntu 13:10, how do I do it?"
date: 2013-08-05
forum: General Help
---

### Post by Bob1950 on 2013-08-05
I am deleting Windows 7 and need to set up Ubuntu 13.10 to boot without the dual boot setup.  How do I do it?

Thanks,  ;)

---

### Post by grahammechanical on 2013-08-05
How many hard disks do you have and which drive is Ubuntu on? If there is only one drive then it would be sda. So, boot into Ubuntu and run

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

That will put Grub into the MBR of sda. Once you have removed Windows run again

```
sudo update-grub
```

to remove any reference to Widows in the Grub menu.

Regards.

---

### Post by Bob1950 on 2013-08-05
I have one partitioned hard drive.  Ubuntu is on SDA2.

> **grahammechanical said:**
> How many hard disks do you have and which drive is Ubuntu on? If there is only one drive then it would be sda. So, boot into Ubuntu and run

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

That will put Grub into the MBR of sda. Once you have removed Windows run again

```
sudo update-grub
```

to remove any reference to Widows in the Grub menu.

Regards.

---

