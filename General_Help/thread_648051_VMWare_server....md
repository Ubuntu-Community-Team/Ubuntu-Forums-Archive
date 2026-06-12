---
title: "VMWare server..."
date: 2007-12-23
forum: General Help
---

### Post by Moonfrost on 2007-12-23
I'm having an issue with VMWare server...I had installed before VMWare server to run a specific application which is only available for Windows so I had to use a virtual machine for that...I made a virtual machine with a hdd image of 10gb...the problem is I've found a perfect replacement for the appication on LInux so I don't need Windows anymore. So I uninstalled VMWare server and I thought the virtual machine and hdd image would be deleted upon removal of program...turns out they didn't so I have 10gb less of space! I've tried to locate the folder to which the Virtual machine and hdd image were installed but couldn't find them everywhere! so I had to re-install the program to tell me where the heck was the virtual machine installed to...now, I deleted the virtual machine successfully but I still can't delete the most important thing to delete...the hdd image...does anybody know where does VMWare server install it's hdd images too? I looked everywhere and can't find it. The program doesn't give me the option to delete it!

By the way, I'm using Gutsy...

---

### Post by seshomaru samma on 2007-12-23
mine is installed in /var/lib/vmware

---

### Post by Moonfrost on 2007-12-23
> **seshomaru samma said:**
> mine is installed in /var/lib/vmware

Yeah thanks, already solved the issue and got my 10gb back! thanks anyway...

---

