---
title: "Any changes I make kills network connetcion on next reboot"
date: 2021-05-03
forum: General Help
---

### Post by granyte on 2021-05-03
I have installed Ubuntu 20.04 set up with a dual boot with Win 10. If I add/remove software or do any updates I lose access to the internet if I reboot the computer. The only way to get the internet back is to boot into Windows and then log back in to Ubuntu.
If I restart Ubuntu without making any changes I can log back in and have access to the internet. If I restart Ubuntu without making any changes and boot into Ubuntu from a USB stick I am without internet again and do not get it back until I boot into windows. I unplugged my current drives and plugged in an old hard drive and did a clean install of Ubuntu without dual boot and the problem was still there. I tried Ubuntu 20.10 and there was not change.
When I lose the internet I have found out my machine was not assigned an IP address and I can not ping my router. I have turned off Fast Startup in windows and on my motherboard.

---

### Post by cevanwells on 2021-05-04
Can you provide more information about your hardware? A good place to start might be the make/model of the computer as well as the output from the lspci and dmesg commands. For example:

```
user@hostname:~$ lspci -vnn >> lspci.txt
user@hostname:~$ dmesg >> dmesg.txt
```

Then just attach the two files that were created (lspci.txt and dmesg.txt in your home folder) to your next post.

Thanks,
Chris

---

### Post by granyte on 2021-05-04
Hardware I am using:
Gigabyte B450M DS3H
AMD Ryzen 5 3600
16 GB Ram
Crucial MX500 1TB
MSI Radeon RX 580
2 BenQ GW2760 Monitors

I have also noticed that if after making changes I do not shut down properly but simple hit the reset button on the computer, when I boot back into Ubuntu I still have internet. If I then shut down properly and boot back into Ubuntu I am without internet again.

---

