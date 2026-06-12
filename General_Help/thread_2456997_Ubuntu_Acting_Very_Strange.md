---
title: "Ubuntu Acting Very Strange"
date: 2021-01-23
forum: General Help
---

### Post by akslnrdn on 2021-01-23
Hello everyone,

I am using ubuntu 18.04. Did not experience issue until today. O.S started to act very strange. Opening tabs.. also deleting the text that i am typing right now. My desktop icons and folders gone (dissappared). Folders almost freezing. I tried to update but did not worked. Is it related something to hardware or software ? The last thing that i did was, copying large files from portable hdd to my computer (temporary)... And the laptop disk now is almost %90 used. I thought that the disk full capacity makes the problem. I have deleted some files but the the problem still exist. Please help me. Thanks in advance.

System Software / Hardware Information


Hardware:
Processor: Intel Core i7-6700HQ @ 3.50GHz (8 Cores), Motherboard: ASUS G752VT v1.0, Chipset: Intel Xeon E3-1200 v5/E3-1500, Memory: 16384MB, Disk: 1000GB HGST HTS541010A9, Graphics: NV124 3072MB, Audio: Realtek ALC668, Network: Realtek RTL8111/8168/8411 + Intel Wireless 7265


Software:
OS: Ubuntu 18.04, Kernel: 5.4.0-62-generic (x86_64), Desktop: GNOME Shell 3.28.4, Display Driver: modesetting 1.20.8, OpenGL: 4.3 Mesa 20.0.8, File-System: ext4, Screen Resolution: 1920x1080


```
labs@labs-G752VT:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  2.2M  1.6G   1% /run
/dev/sda4       366G   25G  323G   8% /
tmpfs           7.8G  271M  7.6G   4% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/loop0       56M   56M     0 100% /snap/core18/1932
/dev/loop1      162M  162M     0 100% /snap/gnome-3-28-1804/128
/dev/loop3      163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop2      384K  384K     0 100% /snap/gnome-characters/570
/dev/loop4      2.5M  2.5M     0 100% /snap/gnome-calculator/826
/dev/loop5      1.0M  1.0M     0 100% /snap/gnome-logs/100
/dev/loop7      143M  143M     0 100% /snap/slack/35
/dev/loop8      147M  147M     0 100% /snap/code/51
/dev/loop6      216M  216M     0 100% /snap/wine-platform-5-stable/13
/dev/loop9       98M   98M     0 100% /snap/core/10577
/dev/loop10     181M  181M     0 100% /snap/telegram-desktop/2315
/dev/loop11     2.3M  2.3M     0 100% /snap/gnome-system-monitor/148
/dev/loop12     384K  384K     0 100% /snap/gnome-characters/550
/dev/loop15     147M  147M     0 100% /snap/opera/106
/dev/loop18     2.5M  2.5M     0 100% /snap/gnome-calculator/748
/dev/loop14     176M  176M     0 100% /snap/postman/129
/dev/loop16      33M   33M     0 100% /snap/chromium-ffmpeg/17
/dev/loop17      98M   98M     0 100% /snap/core/10583
/dev/loop19     179M  179M     0 100% /snap/telegram-desktop/2198
/dev/loop13     146M  146M     0 100% /snap/slack/36
/dev/loop20     147M  147M     0 100% /snap/opera/105
/dev/loop21     219M  219M     0 100% /snap/gnome-3-34-1804/66
/dev/loop24     1.0M  1.0M     0 100% /snap/gnome-logs/81
/dev/loop23     2.3M  2.3M     0 100% /snap/gnome-system-monitor/145
/dev/loop22     176M  176M     0 100% /snap/postman/130
/dev/loop28      78M   78M     0 100% /snap/termius-app/61
/dev/loop27     218M  218M     0 100% /snap/gnome-3-34-1804/60
/dev/loop25      56M   56M     0 100% /snap/core18/1944
/dev/loop26     338M  338M     0 100% /snap/wine-platform-runtime/200
/dev/loop30     304M  304M     0 100% /snap/wine-platform-5-stable/16
/dev/loop29     144M  144M     0 100% /snap/code/52
/dev/loop33     338M  338M     0 100% /snap/wine-platform-runtime/206
/dev/loop31      62M   62M     0 100% /snap/core20/875
/dev/loop32      62M   62M     0 100% /snap/core20/904
/dev/loop34      65M   65M     0 100% /snap/gtk-common-themes/1514
/dev/loop35      65M   65M     0 100% /snap/gtk-common-themes/1513
/dev/sda2       1.9G  175M  1.6G  11% /boot
/dev/sda1       487M  6.2M  480M   2% /boot/efi
/dev/sda5       545G  273G  245G  53% /home
tmpfs           1.6G   20K  1.6G   1% /run/user/121
tmpfs           1.6G   28K  1.6G   1% /run/user/1000



```

Here is my desktop screenshot. Icons and folders are disappeared. As you can see some of the options of mouse (right click) are not available. And more and more other stuff that i cannot describe here.

[ATTACH=CONFIG]287796[/ATTACH]

---

### Post by grahammechanical on 2021-01-23
I doubt if the cause is lack of hard disc space. I see root ( / ) = 323G available and /home = 245G available. Try opening System Monitor and check how much memory is being used and if the CPU cores have a high usage.

Regards

---

### Post by QIII on 2021-01-23
@akslnrdn

Please do not post large inline image files or links to large image files in img tags.  Believe it or not in this day and age, many of our users have slow internet connections and data limits.  Large images can take a long time to download and may actually cost users in extra fees.  Use a thumbnail and let other users choose whether or not to expand them.

If you need to include an image, please use the attachment facility provided by the paperclip icon above the text entry box.  This will add an expandable thumbnail to your post.

---

### Post by akslnrdn on 2021-01-24
Got you. I promise that will pay attention. Thank you.

---

### Post by akslnrdn on 2021-01-24
```
CPU usage: 5-15 %Memory usage: 3.5GIB / 15.6GIB
SWAP: 0B / 2.8GB
368 PROCESS
```

---

