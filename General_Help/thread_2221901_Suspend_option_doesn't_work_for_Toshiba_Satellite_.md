---
title: "Suspend option doesn't work for Toshiba Satellite LP500"
date: 2014-05-04
forum: General Help
---

### Post by DorelXD on 2014-05-04
Hello! I have just bought a Toshiba Satellite LP500, and I succesfully installed Ubuntu 12.04 LTS. However, there is a big problem that really annoys me. The **suspend **option isn't functionable! Yes, I did search on Google for a possible solution but I couldn't find any that works for me. Let me describe briefly the problem: after I click suspend, the Laptop is indeed starting the suspend mode. If I close the lid, nothing happens, this also bugs me. The problem appears when I want to log in again. I type my password, hit enter and then the screen turns black and stays that way.  I tried this solution: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug) , which did nothing. So, there is a possible fix for this? I'm really upset because now I have a laptop with big potential ,but I can't use it properly on Ubuntu. I really want to escape the 'Windows Syndrome', and use Ubuntu, but with these kind of problems I can't do it! Can somebody help me! Thank you!

---

### Post by squakie on 2014-05-04
Hibernate, and to some degree suspend, have been a little difficult in Ubuntu for quite some time.  I honestly don't fuss with it anymore.  Todays OS's boot so fast that it really defeats the purpose of suspend or hibernate.

---

### Post by DorelXD on 2014-05-05
Maybe you're right! But I really look forward for a fix to this problem, because this really bothers me. So, can I do something about it?

---

### Post by squakie on 2014-05-06
Probably not much.  I would suggest doing a net search with:

ubuntu satellite lp500 suspend

and see if anything pops up there.

---

### Post by DorelXD on 2014-05-07
Unfortunately I had no luck :( .

---

### Post by squakie on 2014-05-07
I'll try to keep this post in mind in case I see someone else has or will have solved this problem.

---

### Post by nknwn on 2014-05-08
While the newest laptops and computers start reasonably quickly there are many of us out here who may wish to use Ubuntu on an older laptop. Sleep (suspend) and hibernate are very useful features for these computers.

 I prefer to hibernate this very recently purchased Windows 8.1 computer. I have it set to hibernate when I hit the power button and also when I close the lid.

---

### Post by Toz on 2014-05-08
@DorelXD, can you post back some more information about your computer (open a terminal window, run the commands and post back the results)? Specifically:

1. Your current kernel boot parameters:
```
cat /proc/cmdline
```

2. Info about your video card(s):
```
lspci -k | grep -iA2 VGA
```

3. After a suspend attempt and after you have recovered the computer:
```
cat /var/log/syslog | grep PM:
```

4. The contents of your /var/log/pm-suspend.log file. The best way to do this is to install a program called pastebinit, look for it in the software centre or from the terminal:
```
sudo apt-get install pastebinit
```
...then run the following command:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

---

### Post by martin48 on 2014-06-12
hi, i have the same problem with Toshiba L845 (i7 - 6gb ram - Ati Radeon HD 7670M)
here you are my info

1) [COLOR=#000000][FONT=Ubuntu Mono]cat /proc/cmdline[/FONT][/COLOR] ```
BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic.efi.signed root=UUID=80498f02-8962-4085-81f7-7e01fbc494fc ro quiet splash intel_pstate=enable vt.handoff=7
```

2) [COLOR=#000000][FONT=Ubuntu Mono]lspci -k | grep -iA2 VGA [/FONT][/COLOR]```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series]
    Subsystem: Toshiba America Info Systems Radeon HD 7670M
    Kernel driver in use: fglrx_pci
```

3) [COLOR=#000000][FONT=Ubuntu Mono]cat /var/log/syslog | grep PM: [/FONT][/COLOR]```
Jun 12 14:06:07 amrras-pc kernel: [26065.449511] PM: Syncing filesystems ... done.
Jun 12 14:06:07 amrras-pc kernel: [26065.622868] PM: Preparing system for mem sleep
Jun 12 14:06:07 amrras-pc kernel: [26065.626065] PM: Entering mem sleep
Jun 12 14:06:07 amrras-pc kernel: [26067.633907] PM: suspend of devices complete after 2004.591 msecs
Jun 12 14:06:07 amrras-pc kernel: [26067.634043] PM: late suspend of devices complete after 0.133 msecs
Jun 12 14:06:07 amrras-pc kernel: [26067.714415] PM: noirq suspend of devices complete after 80.246 msecs
Jun 12 14:06:07 amrras-pc kernel: [26067.714950] PM: Saving platform NVS memory
Jun 12 14:06:07 amrras-pc kernel: [26068.444990] PM: Restoring platform NVS memory
Jun 12 14:06:07 amrras-pc kernel: [26068.693737] PM: noirq resume of devices complete after 126.706 msecs
Jun 12 14:06:07 amrras-pc kernel: [26068.693859] PM: early resume of devices complete after 0.097 msecs
Jun 12 14:06:07 amrras-pc kernel: [26070.908575] PM: resume of devices complete after 2211.286 msecs
Jun 12 14:06:07 amrras-pc kernel: [26070.908808] PM: Finishing wakeup.
Jun 12 14:06:33 amrras-pc kernel: [26086.779240] PM: Syncing filesystems ... done.
Jun 12 14:06:33 amrras-pc kernel: [26086.971373] PM: Preparing system for mem sleep
Jun 12 14:06:33 amrras-pc kernel: [26086.974586] PM: Entering mem sleep
Jun 12 14:06:33 amrras-pc kernel: [26089.000481] PM: suspend of devices complete after 2022.619 msecs
Jun 12 14:06:33 amrras-pc kernel: [26089.000613] PM: late suspend of devices complete after 0.130 msecs
Jun 12 14:06:33 amrras-pc kernel: [26089.081069] PM: noirq suspend of devices complete after 80.330 msecs
Jun 12 14:06:33 amrras-pc kernel: [26089.081591] PM: Saving platform NVS memory
Jun 12 14:06:33 amrras-pc kernel: [26089.811608] PM: Restoring platform NVS memory
Jun 12 14:06:33 amrras-pc kernel: [26090.060365] PM: noirq resume of devices complete after 126.737 msecs
Jun 12 14:06:33 amrras-pc kernel: [26090.060487] PM: early resume of devices complete after 0.097 msecs
Jun 12 14:06:33 amrras-pc kernel: [26092.316165] PM: resume of devices complete after 2252.185 msecs
Jun 12 14:06:33 amrras-pc kernel: [26092.316396] PM: Finishing wakeup.
Jun 12 14:18:28 amrras-pc kernel: [26797.639468] PM: Syncing filesystems ... done.
Jun 12 14:18:28 amrras-pc kernel: [26797.814320] PM: Preparing system for mem sleep
Jun 12 14:18:28 amrras-pc kernel: [26797.817489] PM: Entering mem sleep
Jun 12 14:18:28 amrras-pc kernel: [26799.840782] PM: suspend of devices complete after 2021.006 msecs
Jun 12 14:18:28 amrras-pc kernel: [26799.840910] PM: late suspend of devices complete after 0.126 msecs
Jun 12 14:18:28 amrras-pc kernel: [26799.903929] PM: noirq suspend of devices complete after 62.951 msecs
Jun 12 14:18:28 amrras-pc kernel: [26799.904445] PM: Saving platform NVS memory
Jun 12 14:18:28 amrras-pc kernel: [26800.634089] PM: Restoring platform NVS memory
Jun 12 14:18:28 amrras-pc kernel: [26800.866712] PM: noirq resume of devices complete after 110.600 msecs
Jun 12 14:18:28 amrras-pc kernel: [26800.866832] PM: early resume of devices complete after 0.096 msecs
Jun 12 14:18:28 amrras-pc kernel: [26803.149108] PM: resume of devices complete after 2279.881 msecs
Jun 12 14:18:28 amrras-pc kernel: [26803.149339] PM: Finishing wakeup.
Jun 12 14:31:55 amrras-pc kernel: [27601.110206] PM: Syncing filesystems ... done.
Jun 12 14:31:55 amrras-pc kernel: [27601.272487] PM: Preparing system for mem sleep
Jun 12 14:31:55 amrras-pc kernel: [27601.275738] PM: Entering mem sleep
Jun 12 14:31:55 amrras-pc kernel: [27603.282638] PM: suspend of devices complete after 2004.668 msecs
Jun 12 14:31:55 amrras-pc kernel: [27603.282753] PM: late suspend of devices complete after 0.113 msecs
Jun 12 14:31:55 amrras-pc kernel: [27603.345078] PM: noirq suspend of devices complete after 62.257 msecs
Jun 12 14:31:55 amrras-pc kernel: [27603.345616] PM: Saving platform NVS memory
Jun 12 14:31:55 amrras-pc kernel: [27604.075193] PM: Restoring platform NVS memory
Jun 12 14:31:55 amrras-pc kernel: [27604.296832] PM: noirq resume of devices complete after 111.508 msecs
Jun 12 14:31:55 amrras-pc kernel: [27604.296948] PM: early resume of devices complete after 0.095 msecs
Jun 12 14:31:55 amrras-pc kernel: [27606.616146] PM: resume of devices complete after 2316.768 msecs
Jun 12 14:31:55 amrras-pc kernel: [27606.616307] PM: Finishing wakeup.
```

4) [COLOR=#000000][FONT=Ubuntu Mono]pastebinit /var/log/pm-suspend.log [/FONT][/COLOR]```
http://paste.ubuntu.com/7634767/
```

Thanks

---

### Post by martin48 on 2014-06-12
i found a workaround...
these are the devices on my toshiba:

1) acpitool -w 

```
   Device    S-state      Status   Sysfs node  ---------------------------------------
  1. P0P1      S4    *disabled
  2. GLAN      S0    *disabled
  3. EHC1      S3    *enabled   pci:0000:00:1d.0
  4. EHC2      S3    *enabled   pci:0000:00:1a.0
  5. XHC      S3    *enabled   pci:0000:00:14.0
  6. HDEF      S0    *disabled  pci:0000:00:1b.0
  7. RP01      S4    *disabled  pci:0000:00:1c.0
  8. RP02      S4    *disabled
  9. PXSX      S4    *disabled
  10. FRES      S0    *disabled
  11. RP03      S0    *disabled  pci:0000:00:1c.2
  12. PXSX      S4    *disabled  pci:0000:08:00.0
  13. RP04      S4    *disabled  pci:0000:00:1c.3
  14. PXSX      S4    *enabled   pci:0000:09:00.0
  15. ATHE      S4    *disabled
  16. RP05      S4    *disabled
  17. PXSX      S4    *disabled
  18. RP06      S4    *disabled
  19. PXSX      S4    *disabled
  20. RP07      S4    *disabled
  21. PXSX      S4    *disabled
  22. RP08      S4    *disabled
  23. PXSX      S4    *disabled
  24. PEG0      S4    *disabled  pci:0000:00:01.0
  25. PEGP      S4    *disabled
  26. PEG1      S4    *disabled
  27. PEG2      S4    *disabled
  28. PEG3      S4    *disabled
  29. LID      S4    *enabled 

```

2) then i change device 3 and 4 with:
sudo acpitool -W 3
sudo acpitool -W 4

(i found them using lspci | grep USB)


```
   Device    S-state      Status   Sysfs node  ---------------------------------------
  1. P0P1      S4    *disabled
  2. GLAN      S0    *disabled
  3. EHC1      S3    *disabled  pci:0000:00:1d.0
  4. EHC2      S3    *disabled  pci:0000:00:1a.0
  5. XHC      S3    *enabled   pci:0000:00:14.0
  6. HDEF      S0    *disabled  pci:0000:00:1b.0
  7. RP01      S4    *disabled  pci:0000:00:1c.0
  8. RP02      S4    *disabled
  9. PXSX      S4    *disabled
  10. FRES      S0    *disabled
  11. RP03      S0    *disabled  pci:0000:00:1c.2
  12. PXSX      S4    *disabled  pci:0000:08:00.0
  13. RP04      S4    *disabled  pci:0000:00:1c.3
  14. PXSX      S4    *enabled   pci:0000:09:00.0
  15. ATHE      S4    *disabled
  16. RP05      S4    *disabled
  17. PXSX      S4    *disabled
  18. RP06      S4    *disabled
  19. PXSX      S4    *disabled
  20. RP07      S4    *disabled
  21. PXSX      S4    *disabled
  22. RP08      S4    *disabled
  23. PXSX      S4    *disabled
  24. PEG0      S4    *disabled  pci:0000:00:01.0
  25. PEGP      S4    *disabled
  26. PEG1      S4    *disabled
  27. PEG2      S4    *disabled
  28. PEG3      S4    *disabled
  29. LID      S4    *enabled 

```

3) Now, i can suspend

I dont know why it is happening, but it is the only thing i could do.
Now i need to make this changes permanent.

Anyone can help me with this? or a better solution?

Thanks in advance!!!

---

