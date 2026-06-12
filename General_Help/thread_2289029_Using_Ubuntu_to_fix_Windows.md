---
title: "Using Ubuntu to fix Windows?"
date: 2015-07-31
forum: General Help
---

### Post by Colo2 on 2015-07-31
Hello everyone..

Recently my Windows refused to boot, went around in a restart loop after Windows loads. - Trying to open that drive in another Windows machine, Microsoft very kindly let me know that my drive needs to be formatted before I could use it. - As a last resort, the ubuntu liveusb went in, and surprise surprise, i click the drive and it opens, showing me all of my files.

The question is, is there a way to fix NTFS with Ubuntu, as clearly Windows is unable to help me. 

Tom.

---

### Post by yancek on 2015-07-31
> The question is, is there a way to fix NTFS with Ubuntu, as clearly Windows is unable to help me. 


Not likely, especially this type of problem.  There are a lot of members here who do use windows so if you posted some info on what happened immediately prior to this happening, any changes made, etc.  If it doesn't do anything on another windows system I would not have much hope.  Can you boot into a recovery or safe mode on windows and perhaps run chkdsk?  If you can see the folders/files, you should at least be able to save your data to another drive.

---

### Post by oldfred on 2015-07-31
Most Windows fixes cannot be done from Linux. A few can.

Best to see details, but usually best to have a Windows repairCD or flash drive.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by NathanRodriguez on 2015-07-31
First try backing up your important files using the live CD to see if they are readable. Then you can try some specialized ntfs file system repair tool.

---

### Post by Colo2 on 2015-08-01
Thanks for your answers ;) 

I have managed to transfer the integrity of my files over to a new disk using the ubuntu livecd. I'm condemning the broken disk. How is it that Ubuntu can handle Windows' filesystem better than Windows can?

Thank you Ubuntu :D

---

