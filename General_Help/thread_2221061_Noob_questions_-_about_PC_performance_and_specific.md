---
title: "Noob questions - about PC performance and specifications."
date: 2014-04-30
forum: General Help
---

### Post by altjx on 2014-04-30
I've been running Windows 8.1 for quite awhile now, and haven't had any issues whatsoever with performance even one bit. However, yesterday I just installed Ubuntu 14.04 so that I could dual boot. In Ubuntu, I'm noticing all kinds of weird things look very abnormal, but I have no clue.

For example, I'm noticing that several things are using a lot of memory for things, and it doesn't make any sense at all. Here's some information pertaining to my computer's specifications:

```

Processor: Intel(R) Core(TM) i7-3770K CPU @ 3.50GHz
Memory: [COLOR=#3A3A3A][FONT=verdana] [/FONT][/COLOR][16GB (2 x 8GB) DDR3]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231606")
HD1: Samsung 256GB SSD
Graphics Card: [COLOR=#3A3A3A][FONT=verdana] [/FONT][/COLOR][EVGA 02G-P4-2670-KR GeForce GTX 670 2GB 256-Bit GDDR5]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130782")

```

Also, I wanted to mention that during my installation yesterday, I didn't choose to install a swap partition (if that's the correct way to explain it), so I have 0 swap memory and 0 used (obviously). Not sure if this contributes to the issue or not, but I just wanted to mention it just in case.

I have 4GB, and 2 processors (2 cores per processor) allocated to a specific VM because it was running very sluggish before, but the information provided by top is just bothering me because it seems like it's using much more than it actually should. Here's an output by top:

```
top - 10:30:34 up 12:00,  2 users,  load average: 1.94, 1.75, 1.19top - 10:31:55 up 12:02,  2 users,  load average: 1.49, 1.62, 1.19
Tasks: 286 total,   2 running, 283 sleeping,   0 stopped,   1 zombie
%Cpu(s):  5.2 us, 10.7 sy,  0.0 ni, 83.9 id,  0.1 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  16314884 total, 16125704 used,   189180 free,  4101476 buffers
KiB Swap:        0 total,        0 used,        0 free.  8434192 cached Mem


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                   
 8001 user     20   0 6552728 1.546g 1.511g S  78.6  9.9   5:34.95 vmware-vmx                                                                
 4380 user     20   0 2532588 298176  23584 S   0.0  1.8   7:55.81 dropbox                                                                   
 1108 root      20   0  839912 285032 159028 S  14.6  1.7  14:55.83 Xorg                                                                      
 4999 user     20   0 1640496 259400  13088 S   3.7  1.6  23:40.02 chrome                                                                    
 2168 user     20   0 1171892 232880  57912 S   4.6  1.4  19:51.53 chrome                                                                    
31911 user     20   0 1677976 205968  60572 S   6.6  1.3   6:00.88 compiz                                                                    
 5026 user     20   0 1121640 181248  27628 S   0.0  1.1   1:43.76 chrome                                                                    
 5072 user     20   0 1090520 171256  26576 S   1.3  1.0   5:15.49 chrome                                                                    
29862 user     20   0 1219176 166956  26540 S   1.7  1.0   0:26.57 shutter                                                                   
 2330 user     20   0 1055292 144288  18912 S   0.3  0.9   2:21.73 chrome                                                                    
 4187 user     20   0 1012896 143844  49588 S   0.0  0.9   0:23.51 vmware                                                                    
 4603 user     20   0 1876408 143724 117520 S   0.3  0.9   0:52.65 nautilus                                                                  
 4921 user     20   0 1085336 141820  24604 S   0.0  0.9   0:21.89 chrome                                                                    
 5720 user     20   0 1065172 130596  33500 S   0.7  0.8   0:09.79 chrome                                                                    
 4988 user     20   0 1076596 126616  28212 S   0.0  0.8   0:47.47 chrome                                                                    
 4943 user     20   0 1064280 119852  26316 S   0.0  0.7   0:12.49 chrome                                                                    
 4932 user     20   0 1103880 118688  26096 S   0.3  0.7   0:49.13 chrome                                                                    
 7635 user     20   0 1023312  94044  25696 S   0.0  0.6   0:04.32 chrome                                                                    
 1903 user     20   0  807260  89572  70656 S   0.3  0.5   0:16.91 hud-service                                                               
23195 user     20   0 1021584  87280  27264 S   0.0  0.5   0:19.52 chrome                                                                    
 5680 user     20   0 1291912  85924  32076 S   5.3  0.5   3:25.48 pidgin                                                                    
 2335 user     20   0  981024  54164  19676 S   0.0  0.3   0:05.89 chrome                                                                    
12669 user     20   0  397048  49136  33736 S   0.0  0.3   0:18.07 vmware-tray                                                               
 2070 user     20   0  965124  46684   8536 S   0.0  0.3   0:00.17 evolution-calen                                                           
 2308 user     20   0  988936  46588  18440 S   0.0  0.3   0:47.42 chrome                                                                    
 2326 user     20   0  962448  46056  18932 S   0.0  0.3   0:01.77 chrome                                                                    
 8059 user     20   0  849016  43416  21120 S   1.0  0.3   0:02.28 /usr/bin/termin                                                           
 2346 user     20   0  959224  41732  16476 S   0.0  0.3   0:01.52 chrome                                                                    
 2340 user     20   0  959516  39800  16792 S   0.0  0.2   0:02.21 chrome                                                                    
 7879 user     20   0  450324  38544  17712 S   0.0  0.2   0:00.36 apport-gtk                                                                
 2321 user     20   0  959224  38416  15788 S   0.0  0.2   0:02.83 chrome                                                                    
 4663 user     20   0  292696  38400  30676 S   0.0  0.2   0:00.30 vmware-unity-he
```

---

### Post by altjx on 2014-04-30
Also, I just closed out VMware Workstation and according to "free -m", there's approximately 14GB of memory still being used. The only thing I fired up when I turned on the computer this morning are Google Chrome (w/ Facebook, Twitter, Instagram, Linkedin, and Pandora going) and Pidgin. I can't figure out why this would mean 14GB on Ubuntu and 2GB on Windows :\

---

### Post by deadflowr on 2014-04-30
In free -m, look at the line -/+buffers/cache.
That should show what the system is really using and has free to be used.

---

### Post by altjx on 2014-04-30
> **deadflowr said:**
> In free -m, look at the line -/+buffers/cache.
That should show what the system is really using and has free to be used.

Thanks. It's showing around the same thing (with just Chrome and Pidgin open):

```
user@ubuntu:$ free -m
             total       used       free     shared    buffers     cached
Mem:         15932      13821       2111        166       3422       6431
-/+ buffers/cache:       3966      11965
Swap:            0          0          0
user@ubuntu:$ free -mh
             total       used       free     shared    buffers     cached
Mem:           15G        13G       2.0G       166M       3.3G       6.3G
-/+ buffers/cache:       3.9G        11G
Swap:           0B         0B         0B



```

Any ideas?

EDIT: Ahh... Gotcha. That makes sense. I appreciate it!

---

### Post by deadflowr on 2014-04-30
You can also look at the program System Monitor > Resources.
By far easier to understand.

---

### Post by altjx on 2014-04-30
> **deadflowr said:**
> You can also look at the program System Monitor > Resources.
By far easier to understand.

Thanks man! :)

---

