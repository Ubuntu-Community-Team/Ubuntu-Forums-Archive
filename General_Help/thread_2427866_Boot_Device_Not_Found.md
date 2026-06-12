---
title: "Boot Device Not Found"
date: 2019-09-26
forum: General Help
---

### Post by ahooperjr on 2019-09-26
Hi all. I had Ubuntu and Windows 10 dual both installed on my HP laptop and I decided that I wanted to get rid of Windows entirely so I tried to delete it with os-uninstaller package.However it rendered my computer unable to boot into Ubuntu. When I start it it says: *Boot device not found. Please install an operating system on your hard disk. Hard Disk - (3F0)F2 System Diagnostics. *Did I accidentally delete GRUB? How can I fix this problem?

---

### Post by Rubi1200 on 2019-09-27
Hi and welcome to the forums :-)

Best thing right now is to boot the computer with the liveCD/USB and then run the boot info summary report (see first link in my signature).

Do not attempt to repair, just run the report and post here please.

Thanks.

---

### Post by yancek on 2019-09-27
More info as recommended above will be needed.  What is os-installer and from which OS did you run it?  Generally, you simply format the partition rather than "uninstall" an operating system.  On your HP, do you have an option using the Esc key to "boot from EFI file" and if so can you select and boot Ubuntu with it?

---

### Post by ahooperjr on 2019-09-30
Thanks! Sorry for the delay, here is the report.

[http://paste.ubuntu.com/p/wfQ2NJvtXJ/](http://paste.ubuntu.com/p/wfQ2NJvtXJ/)

---

### Post by ahooperjr on 2019-09-30
Hi, thanks for responding and sorry for the delay.

I tried to remove Windows using this guide [https://help.ubuntu.com/community/OS-Uninstaller]("https://help.ubuntu.com/community/OS-Uninstaller")

Yes, I see the option to boot from EFI file but when I press enter it says "No Valid File System Available".

This is my boot info summary report. 
[http://paste.ubuntu.com/p/wfQ2NJvtXJ/]("http://paste.ubuntu.com/p/wfQ2NJvtXJ/")

---

### Post by dan3712 on 2019-12-31
Hi. I'm having this same problem with an HP. Were you able to resolve the problem? 

Thank you, 
Dan

---

### Post by oldfred on 2020-01-01
@dan3712
Probably best to start your own thread. Include brand/model number, UEFI or BIOS install & video card chip. And post link to your Summary Report. They expire in a month or two, so OP's is not available anymore to see exactly his details.

HP typically only boots "Windows Boot Manager" by description. But if no Windows,  you can may have ubuntu use that description to boot. Details buried somewhere in link in my signature and:
       Sony, HP & others workarounds:
[https://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win](https://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win)

If you post your details in your thread, we can give more specific instructions.

---

### Post by dan3712 on 2020-01-01
@oldfred
Thank you. I appreciate the post and your patience.

Dan

---

