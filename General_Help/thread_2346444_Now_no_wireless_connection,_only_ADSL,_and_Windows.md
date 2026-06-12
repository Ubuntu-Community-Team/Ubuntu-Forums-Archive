---
title: "Now no wireless connection, only ADSL, and Windows doesn't start"
date: 2016-12-14
forum: General Help
---

### Post by rva1945 on 2016-12-14
Hi:

While in Ubuntu 12.04 LTS I went to Suspend. When I later resumed, it didn't connect to any connection, neither wireless to an wired ADSL. I went to shut down but had to press the button as it didn't shut at all.

 Now I only see the ADSL connection (it connects successfully),  but no wireless. Though in Edit Connections... it is available.

From Ubuntu I can see the W7 partition.

At reboot, I see the Grub menu but if I select Windows 7, it will never launch. Just a dark screen. A progress bar appears but for a few seconds then it disappears for ever.

What could have gone that wrong? Why W7 now doesn't launch and why the wireless connection disappeared? Of course it is working as I can connect with my phone.

I the W7 related problem can be fixed repairing the grub, is there any tutorial about this?

---

### Post by ajgreeny on 2016-12-15
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and may help us to diagnose what is going on.

---

### Post by rva1945 on 2016-12-15
> **ajgreeny said:**
> See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.     **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and may help us to diagnose what is going on.

Well. somehow the wireless connection problem is fixed. But there is an issue with Suspend, then resuming, it Ubunbu seems to hang, no connections at all, not even shut down works. I must reset the PC.

Then I installed boot-repair and this is the pastebin:

[http://paste.ubuntu.com/23636319/](http://paste.ubuntu.com/23636319/)

Thanks!

---

