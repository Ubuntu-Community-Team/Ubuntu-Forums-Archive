---
title: "Ubuntu Server 12.10 - Reboots on startup"
date: 2013-04-24
forum: General Help
---

### Post by jerim79 on 2013-04-24
I had rebooted the system using shutdown -r now. It will start to load, but as soon as it displays *Starting Likewise Service Manager: lwsmd      [OK] it will reboot.                                                                                                                                                                  I am using Grub version 1.99-21ubuntu3.9.                                                                                                                                                                                                                                                                                                                    Kernel is 3.2.0-39-generic.                                                                                                                                                                                                                                                                                                                                                   I tried using recovery mode to fix any disk issues.

---

### Post by jerim79 on 2013-04-24
I was able to boot into recovery mode and dropped down to a prompt. It seems that when I go to start MySQL that is when it restarts the computer. The syslog and various MySQL logs don't show anything.

---

