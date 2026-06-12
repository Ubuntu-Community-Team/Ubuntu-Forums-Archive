---
title: "Booting after resizing partition is convoluted"
date: 2021-08-05
forum: General Help
---

### Post by taangle on 2021-08-05
Hello, bit of a newb here. I have a dual-booted system (Windows 10/Ubuntu 18.04) and recently gave Ubuntu more space on my SSD (freed up space on Windows, used GParted on live USB to increase Ubuntu's partition). This initially worked, and I was able to boot into Ubuntu and see the new space. However, next time I booted the system, I found myself stuck in emergency mode with a message about the superblock mount time being in the future. After trying a few things, the message about the superblock stopped appearing but I still couldn't get out of emergency mode. I discovered a utility called [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") and decided to give it a whirl. I really wish I had not, because since running Boot-Repair Ubuntu sometimes can't boot on the first try. It gets stuck at the logo screen for my motherboard, but if I REISUB then the system gets a little further - back to emergency mode. I missed the original pastebin from Boot-Repair, but here is the BootInfo summary that I had it make after the fact: [Ubuntu Pastebin]("https://paste.ubuntu.com/p/2KPfY5zqjN/").

I discovered a workaround to successfully leave emergency mode by running ```
mount -a
``` before I run ```
exit
```

I have read that mount -a should give some info that would help debug the problem, but it gives no output at all.

So here is where I currently am if I want to use Ubuntu normally:
1) turn on PC
2) select Ubuntu from GRUB menu
3) REISUB if stuck at motherboard logo then select Ubuntu at GRUB again
4) use workaround to leave emergency mode.

Any troubleshooting suggestions that can be given for getting rid of steps 3 and 4 would be appreciated.

---

### Post by oldfred on 2021-08-05
From line 103 which is same as
sudo efibootmgr -v

BootOrder: 0004,0002,0000,0001,0003

And 0004 is your flash drive.
So it looks like by default UEFI tries to boot flash drive, fails and should go to 0002 which is Ubuntu.
Better to have 0002 as default.

Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 2,0,1,2,4
see also 
man efibootmgr

If HP or a few others, the change in boot order using efibootmgr does not work.
You have to go into UEFI settings and on boot tab, change order there.

---

