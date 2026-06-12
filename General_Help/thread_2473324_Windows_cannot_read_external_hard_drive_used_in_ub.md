---
title: "Windows cannot read external hard drive used in ubuntu"
date: 2022-03-31
forum: General Help
---

### Post by palmgrower on 2022-03-31
I have an NTFS external hard drive that I have used exclusively in ubuntu for years. When I connect it to Windows 10, I cannot read the files. Would there be a simple solution? Thank you.

---

### Post by colin-i on 2022-04-01
If the disk is mounted fine, have you tried with check disk? Right click on the disk, Properties, Tools, Check.

---

### Post by ActionParsnip on 2022-04-01
What file system are you using on the USB storage?

---

### Post by ActionParsnip on 2022-04-01
Before you unplug it physically, do you use the safe remove feature in the OS before yanking the cable out?

---

### Post by yancek on 2022-04-01
>  I have an NTFS external hard drive that I have used exclusively in ubuntu for years. 

I don't know the purpose of using a foreign (windows) filesystem on a Linux OS but the suggestions above are good.  Do you see any warning/error messages when you try to access the drive partition(s)?  Have you run chkdsk in windows on the drive partitions(s)?

---

### Post by ActionParsnip on 2022-04-01
If you are using the drive in Ubuntu then why not use a Linux file system (like Ext4). Does the drive show up OK in disk manager in Windows? Can you run a full chkdsk from there?

---

### Post by palmgrower on 2022-04-01
I have 2 laptops and 2 desktops. Desktops are ubuntu and laptops are windows. This particular external hard drive (NTFS) has been used with a desktop. When I connect it to Laptop 1, it doesn't get recognized. But Laptop 2 reads and plays the files (music, video, etc) in it. I am going to follow your advice and run checkdisk and will report back. Thank you.

---

### Post by yancek on 2022-04-02
>  When I connect it to Laptop 1, it doesn't get recognized. But Laptop 2 reads and plays the files (music, video, etc) in it 

So both laptop 1 and laptop 2 are windows.  Given this information, it doesn't seem logical that it is the drive that is the problem if it works as expecxted on laptop 2 but rather a configuration or other problem with the OS on laptop 1.  Which windows version do you have on either/both laptops?i

---

### Post by palmgrower on 2022-04-05
Both laptops have Windows 10. I investigated the issue a little further. Settings > Device Manager > Disk Drives > Samsung xxxx1234 > Properties > Events > Device not migrated. The device is recognized but drive letter is not assigned. Solution was Properties > Volume > Populate. The drive now gets a letter assigned and all works well. Thank you.

---

