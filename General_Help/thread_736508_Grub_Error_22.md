---
title: "Grub Error 22"
date: 2008-03-26
forum: General Help
---

### Post by James.Dedon on 2008-03-26
I recently created a new partition and installed Ubuntu 8.04 alongside 7.10 on my Dell inspiron 9100.  After realizing that I couldn't get my wireless up and running in 8.04 I decided to delete the partition...  This was a mistake i guess because the MBR was pointing to that partition's **menu.list**.  Now I get an error 22 and can boot neither partition.  I did some looking around and can find nothing to help me redirect the MBR back to the Gusty partition, everything I have found is for recovering windows.   Any ideas?

Thanks in advance.

---

### Post by James.Dedon on 2008-03-26
I solved it by following the instructions[ here.]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by kyphi on 2008-03-26
To restore GRUB:

Get to a command line either via your initial boot screen or use a live CD.

```
sudo grub
find /boot/grub/stage1
```  this will return a value such a (hdx,y)
```
root (hdx,y)
```  substitute the values for x and y found in the last command
```
setup (hd0)
```  note 0 is the number)
```
quit
```
exit
Reboot

---

