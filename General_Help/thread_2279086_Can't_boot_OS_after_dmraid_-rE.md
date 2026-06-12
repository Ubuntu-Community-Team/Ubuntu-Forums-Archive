---
title: "Can't boot OS after dmraid -rE"
date: 2015-05-20
forum: General Help
---

### Post by rwx--- on 2015-05-20
I have a laptop running Windows 8.1, but wanted to dual-boot Ubuntu. I created a bootable USB, however when I tried to install Ubuntu, it showed an empty partition table. After some research, I found that the problem was my 32GB SSD used for caching WIndows, and that dmraid -rE /dev/sda command should fix the problem. But after a reboot, it turns out that my computer cannot boot. I get an error 

"Windows failed to start. A recent hardware or software change might be the cause. File: \BCD Status: 0xc0000034" and that I should insert installation media to repair Windows. 

So I insert Windows installation USB, and restart, but it gives me the same error. Then I insert the Ubuntu bootable USB, but still get the error. So I mash the esc key after turning my laptop on, and get into Startup menu, and press F10 for BIOS setup, and I still get the same error (insted of BIOS setup) 

I've tried burning Ubuntu ISO to couple USB drives, and tried every USB port on my laptop. Also, everytime I turn on my laptop, the light on my USB drive flashes for couple of seconds, so I'm guessing something is being read.

So after the dmraid -rE /dev/sda command, I cannot boot into Windows, I cannot boot Ubuntu from USB drive, and I cannot access BIOS settings. Does anyone know what I broke, and how could I possibly fix it?

---

### Post by rwx--- on 2015-05-20
ok, seems I was able to fix it. I removed the HDD, and connected it to another PC. I got some errors about the drive being corrupted and what not, but I deleted all the partitions and formatted the drive. Then I connected the drive back to my laptop, inserted a bootable USB, and was able to install Ubuntu without any problems. 
I'm still curious how I was able to mess up my computer to the point that I couldn't access BIOS settings, or boot anything from USB drive, so any explanations would be appreciated.

---

