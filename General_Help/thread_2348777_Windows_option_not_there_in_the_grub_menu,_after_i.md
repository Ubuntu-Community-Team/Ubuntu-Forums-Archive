---
title: "Windows option not there in the grub menu, after installing Ubuntu"
date: 2017-01-07
forum: General Help
---

### Post by yasmeenahmed on 2017-01-07
I am new to Ubuntu. I installed Ubuntu after partitioning. However option to boot into Windows has disappeared. I tried 
[HTML]     http://askubuntu.com/questions/210914/grub-does-not-show-a-windows-8-option-after-dual-boot [/HTML]
After running ```
 sudo update-grub
``` Inthe terminal, I get this as output
```
Found Windows 8 (loader) on /dev/sda1
``` , which should give Windows in the grub menu, but it doesn't. Please help!

---

### Post by yancek on 2017-01-07
A common problem with windows 8/Linux is not installing both systems UEFI or not installing both MBR.  The result of doing that is one system boots, the other fails.  Try running the boot repair software which you can get and download to Ubuntu.  Select the option to Create BootInfo Summary rather than trying repairs and post a link to the output here and you should get some suggestions.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You could also review the Ubuntu documentation on dual booting UEFI at the link below and compare that to what you did during your install.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

