---
title: "Your computer  does noy have enough memory"
date: 2018-12-22
forum: General Help
---

### Post by Andres1967 on 2018-12-22
hI, I'm a die hard ubuntu fan (I only use Ubuntu in my laptop, don't even have a separate windows partition), yet I'm noy very technical. I got this message today: Your computer does not have enough free memory to automatically analyze the problem.....' I have 8GB RAM and a 18.10 installation.
I browsed through forums and for a similar problem a user was asked to run:
free -m
```
df -h
df -iWhich I did. Here are the results:

andres@andres-ThinkPad-X230:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3,8G     0  3,8G   0% /dev
tmpfs           768M  1,9M  766M   1% /run
/dev/sda3        15G   10G  3,8G  73% /
tmpfs           3,8G   56M  3,7G   2% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           3,8G     0  3,8G   0% /sys/fs/cgroup
/dev/loop0      3,8M  3,8M     0 100% /snap/gnome-system-monitor/57
/dev/loop3      141M  141M     0 100% /snap/gnome-3-26-1604/74
/dev/loop9      174M  174M     0 100% /snap/spotify/28
/dev/loop5      5,0M  5,0M     0 100% /snap/canonical-livepatch/50
/dev/loop7      7,5M  7,5M     0 100% /snap/canonical-livepatch/54
/dev/loop11      35M   35M     0 100% /snap/gtk-common-themes/818
/dev/loop10      15M   15M     0 100% /snap/gnome-logs/45
/dev/loop13     4,8M  4,8M     0 100% /snap/canonical-livepatch/49
/dev/loop14      35M   35M     0 100% /snap/gtk-common-themes/808
/dev/loop15      13M   13M     0 100% /snap/gnome-characters/139
/dev/loop1       43M   43M     0 100% /snap/gtk-common-themes/701
/dev/loop16     2,3M  2,3M     0 100% /snap/gnome-calculator/238
/dev/loop17     2,3M  2,3M     0 100% /snap/gnome-calculator/260
/dev/loop2       90M   90M     0 100% /snap/core/6034
/dev/loop8       89M   89M     0 100% /snap/core/5897
/dev/loop4      174M  174M     0 100% /snap/spotify/26
/dev/loop6      174M  174M     0 100% /snap/spotify/24
/dev/sda4       317G  162G  139G  54% /home
/dev/sda1       488M  111M  342M  25% /boot
tmpfs           768M   60K  768M   1% /run/user/1000
/dev/loop18      90M   90M     0 100% /snap/core/6130
andres@andres-ThinkPad-X230:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
udev             976953    607   976346    1% /dev
tmpfs            982574   1094   981480    1% /run
/dev/sda3        960992 284344   676648   30% /
tmpfs            982574    130   982444    1% /dev/shm
tmpfs            982574      5   982569    1% /run/lock
tmpfs            982574     18   982556    1% /sys/fs/cgroup
/dev/loop0          747    747        0  100% /snap/gnome-system-monitor/57
/dev/loop3        27631  27631        0  100% /snap/gnome-3-26-1604/74
/dev/loop9        23724  23724        0  100% /snap/spotify/28
/dev/loop5           35     35        0  100% /snap/canonical-livepatch/50
/dev/loop7           35     35        0  100% /snap/canonical-livepatch/54
/dev/loop11       27345  27345        0  100% /snap/gtk-common-themes/818
/dev/loop10        1720   1720        0  100% /snap/gnome-logs/45
/dev/loop13          31     31        0  100% /snap/canonical-livepatch/49
/dev/loop14       27298  27298        0  100% /snap/gtk-common-themes/808
/dev/loop15        1598   1598        0  100% /snap/gnome-characters/139
/dev/loop1        36056  36056        0  100% /snap/gtk-common-themes/701
/dev/loop16        1269   1269        0  100% /snap/gnome-calculator/238
/dev/loop17        1269   1269        0  100% /snap/gnome-calculator/260
/dev/loop2        12810  12810        0  100% /snap/core/6034
/dev/loop8        12808  12808        0  100% /snap/core/5897
/dev/loop4        23724  23724        0  100% /snap/spotify/26
/dev/loop6        23724  23724        0  100% /snap/spotify/24
/dev/sda4      21127168 133949 20993219    1% /home
/dev/sda1         32768    315    32453    1% /boot
tmpfs            982574     41   982533    1% /run/user/1000
/dev/loop18       12810  12810        0  100% /snap/core/6130
```

---

### Post by wildmanne39 on 2018-12-22
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by pqwoerituytrueiwoq on 2018-12-23
Can you post the output of this?
```
top -n1 -o %MEM
```

---

### Post by oldos2er on 2018-12-23
You posted output from df -h, not free -m; may we see free -m output?

---

### Post by basilisk.zaiser on 2018-12-25
hello, I'm new to Ubuntu, recently installed consumed 1.4 gb, after a week goes by 4.4 gb, the truth I have not installed programs that demand a lot of Ram, how could reduce consumption?

```
top - 23:02:25 up  6:22,  1 user,  load average: 0,79, 0,71, 0,90
Tareas: 220 total,   1 ejecutar,  219 hibernar,    0 detener,    0 zombie
%Cpu(s):  9,1 usuario,  6,5 sist,  0,0 adecuado, 83,1 inact,  0,0 en espera,  0,
MiB Mem :   7868,2 total,    718,9 libre,   4302,5 usado,   2846,7 búfer/caché
MiB Intercambio:   1765,8 total,   1764,3 libre,      1,5 usado.   2968,4 dispon

  PID USUARIO   PR  NI    VIRT    RES    SHR S  %CPU  %MEM     HORA+ ORDEN      
16730 yanko     20   0 2645032 688628 136328 S   0,0   8,5  36:31.94 Web Conte+ 
 3205 yanko     20   0 2802556 459740 176220 S  11,8   5,7  56:26.95 firefox    
 3413 yanko     20   0 1794356 348836  91560 S   0,0   4,3   2:56.23 WebExtens+ 
 2624 yanko     20   0 3578564 255144 102608 S  17,6   3,2  23:01.34 gnome-she+ 
20741 yanko     20   0 1865172 209156 112344 S   0,0   2,6   0:08.09 thunderbi+ 
 3135 yanko     20   0 1253840 202280  54460 S   0,0   2,5   7:16.24 gnome-sof+ 
 4683 yanko     20   0 1928880 193476 111248 S   0,0   2,4   9:16.93 Web Conte+ 
21329 yanko     20   0 1454756 171960 120700 S   0,0   2,1   0:08.49 Web Conte+ 
 2418 yanko     20   0 1082744 130732 100764 S   0,0   1,6  27:16.04 Xorg       
 2062 root      20   0  462112 103320  13812 S   0,0   1,3   0:34.50 packageki+ 
 2907 yanko     20   0  823432  50928  39676 S   0,0   0,6   0:00.25 evolution+ 
 5555 yanko     20   0  640916  49084  33568 S   0,0   0,6   0:00.81 seahorse   
  266 root      19  -1  108036  43704  42636 S   0,0   0,5   0:02.43 systemd-j+ 
21497 yanko     20   0  638448  37868  28164 S   0,0   0,5   0:00.33 gnome-ter+ 
 3558 yanko     20   0  610608  31272  25672 S   0,0   0,4   0:00.11 deja-dup-+ 
 2715 yanko     20   0  603380  30480  25024 S   0,0   0,4   0:00.20 goa-daemon 
 1019 root      20   0  779176  30428  17700 S   0,0   0,4   0:09.17 snapd      

 total usado libre compartido búfer/caché disponible
Memoria:        7868        4588         420         306        2859        2675
Swap:          1765           1        1764


yanko@Bunker:~$ df -h
S.ficheros     Tamaño Usados  Disp Uso% Montado en
udev             3,9G      0  3,9G   0% /dev
tmpfs            787M   1,7M  786M   1% /run
/dev/sda1         37G   8,3G   27G  24% /
tmpfs            3,9G    50M  3,8G   2% /dev/shm
tmpfs            5,0M   4,0K  5,0M   1% /run/lock
tmpfs            3,9G      0  3,9G   0% /sys/fs/cgroup
/dev/loop0        35M    35M     0 100% /snap/gtk-common-themes/818
/dev/loop1       2,3M   2,3M     0 100% /snap/gnome-calculator/260
/dev/loop2       2,3M   2,3M     0 100% /snap/gnome-calculator/238
/dev/loop5       3,8M   3,8M     0 100% /snap/gnome-system-monitor/57
/dev/loop3       141M   141M     0 100% /snap/gnome-3-26-1604/74
/dev/loop7        13M    13M     0 100% /snap/gnome-characters/139
/dev/loop8        90M    90M     0 100% /snap/core/6130
/dev/loop9       141M   141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop11       88M    88M     0 100% /snap/core/5662
/dev/loop4        13M    13M     0 100% /snap/gnome-characters/124
/dev/loop6        15M    15M     0 100% /snap/gnome-logs/45
/dev/loop10       43M    43M     0 100% /snap/gtk-common-themes/701
/dev/sda4        878G   2,3G  831G   1% /home
/dev/sda2        923M   113M  747M  14% /boot
/dev/sda3        953M   7,3M  945M   1% /boot/efi
tmpfs            787M   100K  787M   1% /run/user/1000
```

---

### Post by lisati on 2018-12-25
Please use CODE tags when quoting terminal/command-line output, it helps preserve formatting and can make posts easier to read. This can be done by placine [noparse]```
 at the start of terminal output, and 
```[/noparse] at the end.

---

### Post by wildmanne39 on 2018-12-25
Hello and welcome to the forum basilisk.zaiser, please start your own thread so you can get the help you deserve and do not post in someone else's.

Thanks

---

