---
title: "Problem with dual boot"
date: 2017-03-18
forum: General Help
---

### Post by zeca77 on 2017-03-18
Hello guys: I had both windows 7 and ubuntu on my pc, installed in a dual boot. I found some issues with my ubuntu installation, so i ran boot-repair. After that, i found my ubuntu quite faster, but my windows 7 completely disappeared. I have a product key for my windows, but its a System locked pre-instalation, so i cant use it to re-install my windows. Can anyone help me? I really need my windows 7 running because besides having ubuntu, i still need it. I think that probably windows 7 didn't disappear, because all the files are still there, but when usually I could boot and choose windows 7, now i cant, it only shows ubuntu. 
Thanks for the help anyway :p

---

### Post by yancek on 2017-03-18
If you ran boot repair, you should have selected the option to "Create BootInfo Summary" and posted a link to the output here so others can view it.  Do that now and post the link as it will provide more information and someone should be able to suggest something.

---

### Post by zeca77 on 2017-03-18
[http://paste2.org/yWM0vnXY](http://paste2.org/yWM0vnXY)

---

### Post by oldfred on 2017-03-18
Have you run?
sudo update-grub

Part of the issue may be that your Windows is essentially full. It shows 94% used.
Windows NTFS prefers 30% free and at 10% free you just about cannot run a defrag as you have so little working room.
Grub only boots working Windows, so if it does not find it, it may need chkdsk, or you left it hibernated.
Then you may need to repair your Windows using your Windows repair disk's repair console.

You may be able to temporarily reinstall a Windows boot loader and use f8 to get into internal repair console. 
Then after Windows is fixed reinstall grub to MBR using Boot-Repair or command line.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)


 f8 to get to repair install screen, if you can start to boot
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[https://support.microsoft.com/en-us/kb/927392/](https://support.microsoft.com/en-us/kb/927392/)

---

