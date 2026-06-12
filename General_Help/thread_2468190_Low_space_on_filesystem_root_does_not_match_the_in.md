---
title: "Low space on filesystem root does not match the indicated free space"
date: 2021-10-20
forum: General Help
---

### Post by bygeorge02 on 2021-10-20
After I upgraded to 18.04 I started to get low space on filesystem /. I partitioned my drive with 30G for / and another partition of 80G for home. This did not resolve the issue. I did not gain any space by moving home to the other partition, even though I deleted home on / after the move. Example: according to the notice on low space I only had 810M left on /. But when I look at disk analyser or files I fine that DUA shows 17G in use, but that there are files that cannot be scanned. File shows 27G used 482M free and the rest cannot be accessed or opened. I am attaching all the inquiries I did to try to find out what is going on. 
How can I find the hidden files hogging my filesystem? Unhiding files did not help any. Would I be looking for a virus? I tested the memory and found no damage. How do I solve my low space problem?




[COLOR=#000000]
```
~$ watch tail /var/log/syslog
~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G   11M  1.6G   1% /run
/dev/sda2        27G   25G  473M  99% /
tmpfs           7.8G  377M  7.5G   5% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/loop2      2.5M  2.5M     0 100% /snap/gnome-calculator/884
/dev/loop3       62M   62M     0 100% /snap/core20/1169
/dev/loop5       66M   66M     0 100% /snap/gtk-common-themes/1515
/dev/loop1      219M  219M     0 100% /snap/gnome-3-34-1804/66
/dev/loop7       71M   71M     0 100% /snap/superproductivity/1415
/dev/loop6      146M  146M     0 100% /snap/chromium/1781
/dev/loop8       94M   94M     0 100% /snap/breaktimer/33
/dev/loop4       63M   63M     0 100% /snap/empoche/34
/dev/loop9      249M  249M     0 100% /snap/zoom-client/160
/dev/sda1       511M  6.8M  505M   2% /boot/efi
/dev/loop0      141M  141M     0 100% /snap/gnome-3-26-1604/102
/dev/loop10      33M   33M     0 100% /snap/snapd/13270
/dev/loop11     167M  167M     0 100% /snap/freeplane-mindmapping/31
/dev/loop12     100M  100M     0 100% /snap/core/11743
/dev/loop14      92M   92M     0 100% /snap/clipto/21
/dev/loop13     2.5M  2.5M     0 100% /snap/gnome-calculator/826
/dev/loop16      66M   66M     0 100% /snap/gtk-common-themes/1519
/dev/loop15      81M   81M     0 100% /snap/breaktimer/32
/dev/loop18      62M   62M     0 100% /snap/core20/1081
/dev/loop19      67M   67M     0 100% /snap/tradingview/8
/dev/loop17     243M  243M     0 100% /snap/gnome-3-38-2004/76
/dev/loop20     167M  167M     0 100% /snap/freeplane-mindmapping/29
/dev/loop21      64M   64M     0 100% /snap/standard-notes/71
/dev/loop22     242M  242M     0 100% /snap/gnome-3-38-2004/70
/dev/sda3        82G   44G   35G  56% /home
/dev/loop24     258M  258M     0 100% /snap/zoom-client/159
/dev/loop23     768K  768K     0 100% /snap/gnome-characters/723
/dev/loop25     277M  277M     0 100% /snap/gimp/372
/dev/loop26     146M  146M     0 100% /snap/chromium/1772
/dev/loop27     296M  296M     0 100% /snap/vlc/2344
/dev/loop28      11M   11M     0 100% /snap/canonical-livepatch/114
/dev/loop29     150M  150M     0 100% /snap/chartgeany/12
tmpfs           1.6G   28K  1.6G   1% /run/user/121
/dev/loop30     640K  640K     0 100% /snap/gnome-logs/106
/dev/loop31     244M  244M     0 100% /snap/fakecam/102
/dev/loop33      92M   92M     0 100% /snap/clipto/22
/dev/loop32     252M  252M     0 100% /snap/brave/134
/dev/loop34      11M   11M     0 100% /snap/canonical-livepatch/105
/dev/loop36      64M   64M     0 100% /snap/standard-notes/70
/dev/loop35      56M   56M     0 100% /snap/core18/2074
/dev/loop37     768K  768K     0 100% /snap/gnome-characters/726
/dev/loop39     2.5M  2.5M     0 100% /snap/gnome-system-monitor/160
/dev/loop38     244M  244M     0 100% /snap/fakecam/104
/dev/loop40     141M  141M     0 100% /snap/gnome-3-26-1604/104
/dev/loop41     112M  112M     0 100% /snap/simplenote/544
/dev/loop42     163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop43     296M  296M     0 100% /snap/vlc/2288
/dev/loop44     112M  112M     0 100% /snap/simplenote/524
/dev/loop45     640K  640K     0 100% /snap/gnome-logs/103
/dev/loop46      68M   68M     0 100% /snap/tradingview/7
/dev/loop47     2.5M  2.5M     0 100% /snap/gnome-system-monitor/163
/dev/loop48     128K  128K     0 100% /snap/bare/5
/dev/loop49     165M  165M     0 100% /snap/gnome-3-28-1804/161
/dev/loop50     100M  100M     0 100% /snap/core/11798
/dev/loop52     130M  130M     0 100% /snap/nutty/10
/dev/loop51     250M  250M     0 100% /snap/brave/133
/dev/loop53      33M   33M     0 100% /snap/snapd/13170
/dev/loop54     219M  219M     0 100% /snap/gnome-3-34-1804/72
/dev/loop55      71M   71M     0 100% /snap/superproductivity/1360
/dev/loop56     4.9M  4.9M     0 100% /snap/zenity/18
/dev/loop57      56M   56M     0 100% /snap/core18/2128
tmpfs           1.6G  1.6M  1.6G   1% /run/user/1000
/dev/sdc1        15G  407M   15G   3% /media/george/Docs&Pics
```

```
~$ sudo find / -type f -exec du -h {} + | sort -hr | head -20

du: cannot access '/proc/31819/task/31819/fdinfo/5': No such file or directory
du: cannot access '/proc/31819/task/31819/fdinfo/10': No such file or directory
du: cannot access '/proc/31819/fdinfo/5': No such file or directory
find: ‘/run/user/1000/doc’: Permission denied
find: ‘/run/user/1000/gvfs’: Permission denied
3.9G	/home/george/Videos/meditation/Psychological Cleansing - Beautiful Relaxing Music- Peaceful Soothing- Meditation Music- Sleep Music.mp4
3.1G	/home/george/Downloads/distros/deft-8.2.iso
3.0G	/home/george/Downloads/distros/kali-linux-2020.3-live-amd64.iso
2.1G	/swapfile
2.0G	/home/george/Downloads/distros/linuxmint-20-mate-64bit.iso
1.9G	/home/george/Downloads/distros/linuxmint-20-cinnamon-64bit.iso
1.8G	/home/george/Downloads/distros/lubuntu-20.10-desktop-amd64.iso
1.2G	/home/george/Downloads/distros/tails-amd64-4.15.1.img
875M	/home/george/.thunderbird/6vpjyqcw.default-release/ImapMail/imap.gmail-1.com/[Gmail].sbd/All Mail
732M	/home/george/Downloads/distros/archlinux-2020.11.01-x86_64.iso
592M	/home/george/.thunderbird/6vpjyqcw.default-release/ImapMail/imap.gmail-1.com/[Gmail].sbd/Important
550M	/home/george/Videos/meditation/The 48 Laws of Power -in 210 mins- Director-s Cut.mp4
383M	/home/george/Videos/meditation/The Art of War Every Episode.mp4
380M	/home/george/Pictures/iphone/IMG_0260.MOV
380M	/home/george/Pictures/2014/01/28/IMG_0260.MOV
349M	/home/george/Dropbox/Educational/ThinkEconimist$$/TGC_5511_Lect01_ThinkingLikeEconomist.wmv
347M	/home/george/Videos/meditation/2 Hours Of The Greatest Stoic Quotes From The Last 2500 Years.mp4
321M	/home/george/Documents/Education/Concelled weapons/uscca-threats.zip
311M	/var/lib/clamav/daily.cld
301M	/home/george/Videos/politics/Joel Skousen 2020 Year End Analysis.mp4
```
```
george@george-Wild-Dog-Performance:~$ ^C
george@george-Wild-Dog-Performance:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G   11M  1.6G   1% /run
/dev/sda2        27G   25G  457M  99% /
tmpfs           7.8G  411M  7.4G   6% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/loop2      2.5M  2.5M     0 100% /snap/gnome-calculator/884
/dev/loop3       62M   62M     0 100% /snap/core20/1169
/dev/loop5       66M   66M     0 100% /snap/gtk-common-themes/1515
/dev/loop1      219M  219M     0 100% /snap/gnome-3-34-1804/66
/dev/loop7       71M   71M     0 100% /snap/superproductivity/1415
/dev/loop6      146M  146M     0 100% /snap/chromium/1781
/dev/loop8       94M   94M     0 100% /snap/breaktimer/33
/dev/loop4       63M   63M     0 100% /snap/empoche/34
/dev/loop9      249M  249M     0 100% /snap/zoom-client/160
/dev/sda1       511M  6.8M  505M   2% /boot/efi
/dev/loop0      141M  141M     0 100% /snap/gnome-3-26-1604/102
/dev/loop10      33M   33M     0 100% /snap/snapd/13270
/dev/loop11     167M  167M     0 100% /snap/freeplane-mindmapping/31
/dev/loop12     100M  100M     0 100% /snap/core/11743
/dev/loop14      92M   92M     0 100% /snap/clipto/21
/dev/loop13     2.5M  2.5M     0 100% /snap/gnome-calculator/826
/dev/loop16      66M   66M     0 100% /snap/gtk-common-themes/1519
/dev/loop15      81M   81M     0 100% /snap/breaktimer/32
/dev/loop18      62M   62M     0 100% /snap/core20/1081
/dev/loop19      67M   67M     0 100% /snap/tradingview/8
/dev/loop17     243M  243M     0 100% /snap/gnome-3-38-2004/76
/dev/loop20     167M  167M     0 100% /snap/freeplane-mindmapping/29
/dev/loop21      64M   64M     0 100% /snap/standard-notes/71
/dev/loop22     242M  242M     0 100% /snap/gnome-3-38-2004/70
/dev/sda3        82G   44G   35G  57% /home
/dev/loop24     258M  258M     0 100% /snap/zoom-client/159
/dev/loop23     768K  768K     0 100% /snap/gnome-characters/723
/dev/loop25     277M  277M     0 100% /snap/gimp/372
/dev/loop26     146M  146M     0 100% /snap/chromium/1772
/dev/loop27     296M  296M     0 100% /snap/vlc/2344
/dev/loop28      11M   11M     0 100% /snap/canonical-livepatch/114
/dev/loop29     150M  150M     0 100% /snap/chartgeany/12
tmpfs           1.6G   28K  1.6G   1% /run/user/121
/dev/loop30     640K  640K     0 100% /snap/gnome-logs/106
/dev/loop31     244M  244M     0 100% /snap/fakecam/102
/dev/loop33      92M   92M     0 100% /snap/clipto/22
/dev/loop32     252M  252M     0 100% /snap/brave/134
/dev/loop34      11M   11M     0 100% /snap/canonical-livepatch/105
/dev/loop36      64M   64M     0 100% /snap/standard-notes/70
/dev/loop35      56M   56M     0 100% /snap/core18/2074
/dev/loop37     768K  768K     0 100% /snap/gnome-characters/726
/dev/loop39     2.5M  2.5M     0 100% /snap/gnome-system-monitor/160
/dev/loop38     244M  244M     0 100% /snap/fakecam/104
/dev/loop40     141M  141M     0 100% /snap/gnome-3-26-1604/104
/dev/loop41     112M  112M     0 100% /snap/simplenote/544
/dev/loop42     163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop43     296M  296M     0 100% /snap/vlc/2288
/dev/loop44     112M  112M     0 100% /snap/simplenote/524
/dev/loop45     640K  640K     0 100% /snap/gnome-logs/103
/dev/loop46      68M   68M     0 100% /snap/tradingview/7
/dev/loop47     2.5M  2.5M     0 100% /snap/gnome-system-monitor/163
/dev/loop48     128K  128K     0 100% /snap/bare/5
/dev/loop49     165M  165M     0 100% /snap/gnome-3-28-1804/161
/dev/loop50     100M  100M     0 100% /snap/core/11798
/dev/loop52     130M  130M     0 100% /snap/nutty/10
/dev/loop51     250M  250M     0 100% /snap/brave/133
/dev/loop53      33M   33M     0 100% /snap/snapd/13170
/dev/loop54     219M  219M     0 100% /snap/gnome-3-34-1804/72
/dev/loop55      71M   71M     0 100% /snap/superproductivity/1360
/dev/loop56     4.9M  4.9M     0 100% /snap/zenity/18
/dev/loop57      56M   56M     0 100% /snap/core18/2128
tmpfs           1.6G  1.6M  1.6G   1% /run/user/1000

```
```
~$ sudo du --max-depth=1 --total --one-file-system /

136124	/boot
4	/mnt
9168148	/var
4	/lib64
4	/srv
332	/tmp
4	/cdrom
140	/snap
880	/root
1209424	/lib
3972248	/usr
4	/.cache
13576	/etc
16	/lost+found
12	/media
11576	/sbin
16312	/bin
4	/opt
16625972	/
16625972	total

```
```
~$ ls -lh /var/log
total 4.0K
-rw------- 1 root root 664 Oct 20 15:51 ubuntu-advantage.log
```
```
george@george-Wild-Dog-Performance:~$ journalctl --disk-usage
Archived and active journals take up 8.0M in the file system.

~
``````
$ uname -a; dpkg -l | grep linux-image
Linux george-Wild-Dog-Performance 5.4.0-87-generic #98~18.04.1-Ubuntu SMP Wed Sep 22 10:45:04 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
rc  linux-image-5.4.0-80-generic               5.4.0-80.90~18.04.1                             amd64        Signed kernel image generic
rc  linux-image-5.4.0-81-generic               5.4.0-81.91~18.04.1                             amd64        Signed kernel image generic
rc  linux-image-5.4.0-84-generic               5.4.0-84.94~18.04.1                             amd64        Signed kernel image generic
ii  linux-image-5.4.0-86-generic               5.4.0-86.97~18.04.1                             amd64        Signed kernel image generic
ii  linux-image-5.4.0-87-generic               5.4.0-87.98~18.04.1                             amd64        Signed kernel image generic
iU  linux-image-5.4.0-89-generic               5.4.0-89.100~18.04.1                            amd64        Signed kernel image generic
iU  linux-image-generic-hwe-18.04              5.4.0.89.100~18.04.79                           amd64        Generic Linux kernel image

```


```
~$ sudo du -sk /var/* | sort -n

0	/var/lock
0	/var/run
4	/var/crash
4	/var/local
4	/var/mail
4	/var/metrics
4	/var/opt
8	/var/log
4964	/var/backups
7688	/var/snap
12392	/var/spool
163588	/var/cache
636912	/var/tmp
8342572	/var/lib
```

 [/COLOR]

```
~$ watch tail /var/log/syslog
~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G   11M  1.6G   1% /run
/dev/sda2        27G   25G  473M  99% /
tmpfs           7.8G  377M  7.5G   5% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/loop2      2.5M  2.5M     0 100% /snap/gnome-calculator/884
/dev/loop3       62M   62M     0 100% /snap/core20/1169
/dev/loop5       66M   66M     0 100% /snap/gtk-common-themes/1515
/dev/loop1      219M  219M     0 100% /snap/gnome-3-34-1804/66
/dev/loop7       71M   71M     0 100% /snap/superproductivity/1415
/dev/loop6      146M  146M     0 100% /snap/chromium/1781
/dev/loop8       94M   94M     0 100% /snap/breaktimer/33
/dev/loop4       63M   63M     0 100% /snap/empoche/34
/dev/loop9      249M  249M     0 100% /snap/zoom-client/160
/dev/sda1       511M  6.8M  505M   2% /boot/efi
/dev/loop0      141M  141M     0 100% /snap/gnome-3-26-1604/102
/dev/loop10      33M   33M     0 100% /snap/snapd/13270
/dev/loop11     167M  167M     0 100% /snap/freeplane-mindmapping/31
/dev/loop12     100M  100M     0 100% /snap/core/11743
/dev/loop14      92M   92M     0 100% /snap/clipto/21
/dev/loop13     2.5M  2.5M     0 100% /snap/gnome-calculator/826
/dev/loop16      66M   66M     0 100% /snap/gtk-common-themes/1519
/dev/loop15      81M   81M     0 100% /snap/breaktimer/32
/dev/loop18      62M   62M     0 100% /snap/core20/1081
/dev/loop19      67M   67M     0 100% /snap/tradingview/8
/dev/loop17     243M  243M     0 100% /snap/gnome-3-38-2004/76
/dev/loop20     167M  167M     0 100% /snap/freeplane-mindmapping/29
/dev/loop21      64M   64M     0 100% /snap/standard-notes/71
/dev/loop22     242M  242M     0 100% /snap/gnome-3-38-2004/70
/dev/sda3        82G   44G   35G  56% /home
/dev/loop24     258M  258M     0 100% /snap/zoom-client/159
/dev/loop23     768K  768K     0 100% /snap/gnome-characters/723
/dev/loop25     277M  277M     0 100% /snap/gimp/372
/dev/loop26     146M  146M     0 100% /snap/chromium/1772
/dev/loop27     296M  296M     0 100% /snap/vlc/2344
/dev/loop28      11M   11M     0 100% /snap/canonical-livepatch/114
/dev/loop29     150M  150M     0 100% /snap/chartgeany/12
tmpfs           1.6G   28K  1.6G   1% /run/user/121
/dev/loop30     640K  640K     0 100% /snap/gnome-logs/106
/dev/loop31     244M  244M     0 100% /snap/fakecam/102
/dev/loop33      92M   92M     0 100% /snap/clipto/22
/dev/loop32     252M  252M     0 100% /snap/brave/134
/dev/loop34      11M   11M     0 100% /snap/canonical-livepatch/105
/dev/loop36      64M   64M     0 100% /snap/standard-notes/70
/dev/loop35      56M   56M     0 100% /snap/core18/2074
/dev/loop37     768K  768K     0 100% /snap/gnome-characters/726
/dev/loop39     2.5M  2.5M     0 100% /snap/gnome-system-monitor/160
/dev/loop38     244M  244M     0 100% /snap/fakecam/104
/dev/loop40     141M  141M     0 100% /snap/gnome-3-26-1604/104
/dev/loop41     112M  112M     0 100% /snap/simplenote/544
/dev/loop42     163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop43     296M  296M     0 100% /snap/vlc/2288
/dev/loop44     112M  112M     0 100% /snap/simplenote/524
/dev/loop45     640K  640K     0 100% /snap/gnome-logs/103
/dev/loop46      68M   68M     0 100% /snap/tradingview/7
/dev/loop47     2.5M  2.5M     0 100% /snap/gnome-system-monitor/163
/dev/loop48     128K  128K     0 100% /snap/bare/5
/dev/loop49     165M  165M     0 100% /snap/gnome-3-28-1804/161
/dev/loop50     100M  100M     0 100% /snap/core/11798
/dev/loop52     130M  130M     0 100% /snap/nutty/10
/dev/loop51     250M  250M     0 100% /snap/brave/133
/dev/loop53      33M   33M     0 100% /snap/snapd/13170
/dev/loop54     219M  219M     0 100% /snap/gnome-3-34-1804/72
/dev/loop55      71M   71M     0 100% /snap/superproductivity/1360
/dev/loop56     4.9M  4.9M     0 100% /snap/zenity/18
/dev/loop57      56M   56M     0 100% /snap/core18/2128
tmpfs           1.6G  1.6M  1.6G   1% /run/user/1000
/dev/sdc1        15G  407M   15G   3% /media/george/Docs&Pics

```
```
~$ sudo find / -type f -exec du -h {} + | sort -hr | head -20

du: cannot access '/proc/31819/task/31819/fdinfo/5': No such file or directory
du: cannot access '/proc/31819/task/31819/fdinfo/10': No such file or directory
du: cannot access '/proc/31819/fdinfo/5': No such file or directory
find: ‘/run/user/1000/doc’: Permission denied
find: ‘/run/user/1000/gvfs’: Permission denied
3.9G	/home/george/Videos/meditation/Psychological Cleansing - Beautiful Relaxing Music- Peaceful Soothing- Meditation Music- Sleep Music.mp4
3.1G	/home/george/Downloads/distros/deft-8.2.iso
3.0G	/home/george/Downloads/distros/kali-linux-2020.3-live-amd64.iso
2.1G	/swapfile
2.0G	/home/george/Downloads/distros/linuxmint-20-mate-64bit.iso
1.9G	/home/george/Downloads/distros/linuxmint-20-cinnamon-64bit.iso
1.8G	/home/george/Downloads/distros/lubuntu-20.10-desktop-amd64.iso
1.2G	/home/george/Downloads/distros/tails-amd64-4.15.1.img
875M	/home/george/.thunderbird/6vpjyqcw.default-release/ImapMail/imap.gmail-1.com/[Gmail].sbd/All Mail
732M	/home/george/Downloads/distros/archlinux-2020.11.01-x86_64.iso
592M	/home/george/.thunderbird/6vpjyqcw.default-release/ImapMail/imap.gmail-1.com/[Gmail].sbd/Important
550M	/home/george/Videos/meditation/The 48 Laws of Power -in 210 mins- Director-s Cut.mp4
383M	/home/george/Videos/meditation/The Art of War Every Episode.mp4
380M	/home/george/Pictures/iphone/IMG_0260.MOV
380M	/home/george/Pictures/2014/01/28/IMG_0260.MOV
349M	/home/george/Dropbox/Educational/ThinkEconimist$$/TGC_5511_Lect01_ThinkingLikeEconomist.wmv
347M	/home/george/Videos/meditation/2 Hours Of The Greatest Stoic Quotes From The Last 2500 Years.mp4
321M	/home/george/Documents/Education/Concelled weapons/uscca-threats.zip
311M	/var/lib/clamav/daily.cld
301M	/home/george/Videos/politics/Joel Skousen 2020 Year End Analysis.mp4
george@george-Wild-Dog-Performance:~$ ^C
```
```
george@george-Wild-Dog-Performance:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G   11M  1.6G   1% /run
/dev/sda2        27G   25G  457M  99% /
tmpfs           7.8G  411M  7.4G   6% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/loop2      2.5M  2.5M     0 100% /snap/gnome-calculator/884
/dev/loop3       62M   62M     0 100% /snap/core20/1169
/dev/loop5       66M   66M     0 100% /snap/gtk-common-themes/1515
/dev/loop1      219M  219M     0 100% /snap/gnome-3-34-1804/66
/dev/loop7       71M   71M     0 100% /snap/superproductivity/1415
/dev/loop6      146M  146M     0 100% /snap/chromium/1781
/dev/loop8       94M   94M     0 100% /snap/breaktimer/33
/dev/loop4       63M   63M     0 100% /snap/empoche/34
/dev/loop9      249M  249M     0 100% /snap/zoom-client/160
/dev/sda1       511M  6.8M  505M   2% /boot/efi
/dev/loop0      141M  141M     0 100% /snap/gnome-3-26-1604/102
/dev/loop10      33M   33M     0 100% /snap/snapd/13270
/dev/loop11     167M  167M     0 100% /snap/freeplane-mindmapping/31
/dev/loop12     100M  100M     0 100% /snap/core/11743
/dev/loop14      92M   92M     0 100% /snap/clipto/21
/dev/loop13     2.5M  2.5M     0 100% /snap/gnome-calculator/826
/dev/loop16      66M   66M     0 100% /snap/gtk-common-themes/1519
/dev/loop15      81M   81M     0 100% /snap/breaktimer/32
/dev/loop18      62M   62M     0 100% /snap/core20/1081
/dev/loop19      67M   67M     0 100% /snap/tradingview/8
/dev/loop17     243M  243M     0 100% /snap/gnome-3-38-2004/76
/dev/loop20     167M  167M     0 100% /snap/freeplane-mindmapping/29
/dev/loop21      64M   64M     0 100% /snap/standard-notes/71
/dev/loop22     242M  242M     0 100% /snap/gnome-3-38-2004/70
/dev/sda3        82G   44G   35G  57% /home
/dev/loop24     258M  258M     0 100% /snap/zoom-client/159
/dev/loop23     768K  768K     0 100% /snap/gnome-characters/723
/dev/loop25     277M  277M     0 100% /snap/gimp/372
/dev/loop26     146M  146M     0 100% /snap/chromium/1772
/dev/loop27     296M  296M     0 100% /snap/vlc/2344
/dev/loop28      11M   11M     0 100% /snap/canonical-livepatch/114
/dev/loop29     150M  150M     0 100% /snap/chartgeany/12
tmpfs           1.6G   28K  1.6G   1% /run/user/121
/dev/loop30     640K  640K     0 100% /snap/gnome-logs/106
/dev/loop31     244M  244M     0 100% /snap/fakecam/102
/dev/loop33      92M   92M     0 100% /snap/clipto/22
/dev/loop32     252M  252M     0 100% /snap/brave/134
/dev/loop34      11M   11M     0 100% /snap/canonical-livepatch/105
/dev/loop36      64M   64M     0 100% /snap/standard-notes/70
/dev/loop35      56M   56M     0 100% /snap/core18/2074
/dev/loop37     768K  768K     0 100% /snap/gnome-characters/726
/dev/loop39     2.5M  2.5M     0 100% /snap/gnome-system-monitor/160
/dev/loop38     244M  244M     0 100% /snap/fakecam/104
/dev/loop40     141M  141M     0 100% /snap/gnome-3-26-1604/104
/dev/loop41     112M  112M     0 100% /snap/simplenote/544
/dev/loop42     163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop43     296M  296M     0 100% /snap/vlc/2288
/dev/loop44     112M  112M     0 100% /snap/simplenote/524
/dev/loop45     640K  640K     0 100% /snap/gnome-logs/103
/dev/loop46      68M   68M     0 100% /snap/tradingview/7
/dev/loop47     2.5M  2.5M     0 100% /snap/gnome-system-monitor/163
/dev/loop48     128K  128K     0 100% /snap/bare/5
/dev/loop49     165M  165M     0 100% /snap/gnome-3-28-1804/161
/dev/loop50     100M  100M     0 100% /snap/core/11798
/dev/loop52     130M  130M     0 100% /snap/nutty/10
/dev/loop51     250M  250M     0 100% /snap/brave/133
/dev/loop53      33M   33M     0 100% /snap/snapd/13170
/dev/loop54     219M  219M     0 100% /snap/gnome-3-34-1804/72
/dev/loop55      71M   71M     0 100% /snap/superproductivity/1360
/dev/loop56     4.9M  4.9M     0 100% /snap/zenity/18
/dev/loop57      56M   56M     0 100% /snap/core18/2128
tmpfs           1.6G  1.6M  1.6G   1% /run/user/1000

```
```
~$ sudo du --max-depth=1 --total --one-file-system /

136124	/boot
4	/mnt
9168148	/var
4	/lib64
4	/srv
332	/tmp
4	/cdrom
140	/snap
880	/root
1209424	/lib
3972248	/usr
4	/.cache
13576	/etc
16	/lost+found
12	/media
11576	/sbin
16312	/bin
4	/opt
16625972	/
16625972	total
```

```
~$ ls -lh /var/log
total 4.0K
-rw------- 1 root root 664 Oct 20 15:51 ubuntu-advantage.log
```
```
george@george-Wild-Dog-Performance:~$ journalctl --disk-usage
Archived and active journals take up 8.0M in the file system.

```
```
~$ uname -a; dpkg -l | grep linux-image
Linux george-Wild-Dog-Performance 5.4.0-87-generic #98~18.04.1-Ubuntu SMP Wed Sep 22 10:45:04 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
rc  linux-image-5.4.0-80-generic               5.4.0-80.90~18.04.1                             amd64        Signed kernel image generic
rc  linux-image-5.4.0-81-generic               5.4.0-81.91~18.04.1                             amd64        Signed kernel image generic
rc  linux-image-5.4.0-84-generic               5.4.0-84.94~18.04.1                             amd64        Signed kernel image generic
ii  linux-image-5.4.0-86-generic               5.4.0-86.97~18.04.1                             amd64        Signed kernel image generic
ii  linux-image-5.4.0-87-generic               5.4.0-87.98~18.04.1                             amd64        Signed kernel image generic
iU  linux-image-5.4.0-89-generic               5.4.0-89.100~18.04.1                            amd64        Signed kernel image generic
iU  linux-image-generic-hwe-18.04              5.4.0.89.100~18.04.79                           amd64        Generic Linux kernel image

```


```
~$ sudo du -sk /var/* | sort -n

0	/var/lock
0	/var/run
4	/var/crash
4	/var/local
4	/var/mail
4	/var/metrics
4	/var/opt
8	/var/log
4964	/var/backups
7688	/var/snap
12392	/var/spool
163588	/var/cache
636912	/var/tmp
8342572	/var/lib
```

---

### Post by Impavidus on 2021-10-21
1: You've got one partially installed kernel. This blocks the package management and may cause a pileup of packages ready to be installed. On the other hand, a full filesystem may block installation of that kernel. So I can't say if this is the cause or the effect of your full filesystem. I guess it's most likely to be the effect.

2: You didn't check for any storage hiding under mountpoints. df reports 25GB on the root partition, but du only sees 16GB, which could mean that 9GB is hiding under some mountpoint, probably /home. If you boot in recovery mode or use a livedisk, you can check and cleanup. Maybe when you moved /home to its own partition, you didn't remove the hidden files and directories (those with a name starting with a dot). Or maybe you only moved the contents of /home to trash, without actually removing it. 

3: You've got 8GB of data in /var/lib. I only have 360MB there. Could you dig a little deeper there?

4: You didn't mention the type of filesystem you use. Is it the default (ext4) or something fancy, like btrfs or zfs?

---

### Post by bygeorge02 on 2021-10-26
Impavidus
Thank you for responding. I have been looking for the hidden files. I have not been able to find the extra space taken up by missing files. I can see many such files but I get the message that not all files can be opened. I have checked the packages and see that there is at least one package that needs repair. Running "apt --fix-broken install". It could not fix it. My filesystem is ext4.
This is part of what I saw.
~$ sudo du -sk /var/lib/* | sort -n
132	/var/lib/ucf
236	/var/lib/PackageKit
484	/var/lib/systemd
544	/var/lib/usbutils
624	/var/lib/gdm3
824	/var/lib/fwupd
996	/var/lib/ureadahead
4176	/var/lib/aspell
18852	/var/lib/app-info
50084	/var/lib/mlocate
75336	/var/lib/dpkg
260904	/var/lib/apt
434080	/var/lib/clamav
7493608	/var/lib/snapd
~$
I am certain that I did something wrong when I moved home. As I recall I did delete the files on the / partition. However, I vaguely recall there was some notes that may have been errors that I did not really review.
At this point am I only left with a reinstall of the OS?

---

### Post by ActionParsnip on 2021-10-27
You can clean up some with
```

sudo dpkg -P linux-image-5.4.0-80-generic linux-image-5.4.0-81-generic linux-image-5.4.0-84-generic

```

---

### Post by Impavidus on 2021-10-27
Step by step instructions to check for files hidden under the /home mountpoint:

1: From the grub menu, boot into recovery mode.
2: Select a root shell. This will not mount the /home partition.
3: Remount the filesystem in read-write mode:```
mount -rw -o remount /
```
4: Move the /home directory with its contents (if any) to /old-home:```
mv /home /old-home
```
5: Create a new /home directory:```
mkdir /home
```
6: Make sure the right permissions are set on your new /home:```
chmod 755 /home
```
7: Reboot:```
reboot
```
8: Login in your normal session and check the contents of /old-home using du or whatever tool you like.

You've got quite some stuff in /var/lib/snapd. I don't use snaps myself, so I'm not sure whether the snap images are stored there (in which case it's real storage, which you can cleanup by removing some (old) snaps) or the snaps are just mounted there (in which case it's virtual storage and df reports more than there is).

---

