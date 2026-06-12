---
title: "Broad band speed monitor"
date: 2023-09-06
forum: General Help
---

### Post by satimis on 2023-09-06
Hi all

FTTH 500M connection

Please advise how to monitor/check the upload and download speeds of the broadband?

Thanks

Regards

---

### Post by grahammechanical on 2023-09-06
Open System Monitor> Processes tab.

I get confused between bits and bytes. I have seen at least one TV advert offering a high download rate but it was measured in bits per second. Which is not as fast as it seems. System Monitor uses Bytes per second. 

1x mega byte = 1,000 kilo bytes. 1x mega bit = 125 kilobytes. Mbps = Mega bits per second. Beware of confusing Mbps with MBps.

Regards

---

### Post by #&amp;thj^% on 2023-09-06
+1
Also
```
apt search speedtest
Sorting... Done
Full Text Search... Done
speedtest-cli/lunar,lunar,now 2.1.3-2 all [installed]
  Command line interface for testing internet bandwidth using speedtest.net

```

---

### Post by satimis on 2023-09-06
> **1fallen said:**
> +1
Also
```
apt search speedtest
Sorting... Done
Full Text Search... Done
speedtest-cli/lunar,lunar,now 2.1.3-2 all [installed]
  Command line interface for testing internet bandwidth using speedtest.net

```
Hi,

Thanks for your advice.

$ apt search speedtest```

Sorting... Done
Full Text Search... Done
speedtest-cli/jammy,jammy 2.1.3-2 all
  Command line interface for testing internet bandwidth using speedtest.net

```

$ apt policy speedtest-cli```

speedtest-cli:
  Installed: (none)
  Candidate: 2.1.3-2
  Version table:
     2.1.3-2 500
        500 http://hk.mirrors.thegigabit.com/ubuntu jammy/universe amd64 Packages
        500 http://hk.mirrors.thegigabit.com/ubuntu jammy/universe i386 Packages

```
Whether install speedtest-cli ?

Regards

---

### Post by #&amp;thj^% on 2023-09-06
> **satimis said:**
> 
Whether install speedtest-cli ?

Regards
Ok some choices then, speedtest-cli
```
speedtest
Retrieving speedtest.net configuration...
Testing from Unknown (146.70.112.76)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Eastlink (Wetaskiwin, AB) [8321.76 km]: 179.847 ms
Testing download speed................................................................................
Download: 29.32 Mbit/s
Testing upload speed......................................................................................................
Upload: 4.64 Mbit/s

```
Now nload
```
Device eno1 [192.168.1.159] (1/6):
================================================================================
Incoming:





                                                       Curr: 144.71 kBit/s
                                                       Avg: 162.95 kBit/s
                                                       Min: 115.20 kBit/s
                                                       Max: 281.27 kBit/s
                                                       Ttl: 164.28 MByte
Outgoing:





                                                       Curr: 15.02 kBit/s
                                                       Avg: 21.10 kBit/s
                                                       Min: 12.85 kBit/s
                                                       Max: 85.20 kBit/s
                                                       Ttl: 23.73 MByte

```
How about Net Hog:
```
NetHogs version 0.8.7-2

    PID USER     PROGRAM                    DEV         SENT      RECEIVED      
  37782 me       strawberry                 surfsh      0.488      13.112 KB/sec
      ? root     10.14.0.2:47690-185.125..              0.056       0.045 KB/sec
 153195 me       /usr/lib/firefox/firefox   surfsh      0.025       0.026 KB/sec
      ? root     unknown TCP                            0.000       0.000 KB/sec

  TOTAL                                                 0.569      13.183 KB/sec





```
All are in the repos.

---

### Post by satimis on 2023-09-06
> **grahammechanical said:**
> Open System Monitor> Processes tab.

I get confused between bits and bytes. I have seen at least one TV advert offering a high download rate but it was measured in bits per second. Which is not as fast as it seems. System Monitor uses Bytes per second. 

1x mega byte = 1,000 kilo bytes. 1x mega bit = 125 kilobytes. Mbps = Mega bits per second. Beware of confusing Mbps with MBps.

Regards
Hi,

Thanks for your advice.

Activities -> System Monitor -> Processes

How to read the output (please see attached file)

Regards

---

### Post by #&amp;thj^% on 2023-09-06
> **satimis said:**
> Hi,

Thanks for your advice.

Activities -> System Monitor -> Processes

How to read the output (please see attached file)

Regards

Instead select Performance toptab>>Network left tree

---

### Post by satimis on 2023-09-06
> **1fallen said:**
> Ok some choices then, speedtest-cli
```
speedtest
Retrieving speedtest.net configuration...
Testing from Unknown (146.70.112.76)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Eastlink (Wetaskiwin, AB) [8321.76 km]: 179.847 ms
Testing download speed................................................................................
Download: 29.32 Mbit/s
Testing upload speed......................................................................................................
Upload: 4.64 Mbit/s

```
Now nload
```
Device eno1 [192.168.1.159] (1/6):
================================================================================
Incoming:





                                                       Curr: 144.71 kBit/s
                                                       Avg: 162.95 kBit/s
                                                       Min: 115.20 kBit/s
                                                       Max: 281.27 kBit/s
                                                       Ttl: 164.28 MByte
Outgoing:





                                                       Curr: 15.02 kBit/s
                                                       Avg: 21.10 kBit/s
                                                       Min: 12.85 kBit/s
                                                       Max: 85.20 kBit/s
                                                       Ttl: 23.73 MByte

```
How about Net Hog:
```
NetHogs version 0.8.7-2

    PID USER     PROGRAM                    DEV         SENT      RECEIVED      
  37782 me       strawberry                 surfsh      0.488      13.112 KB/sec
      ? root     10.14.0.2:47690-185.125..              0.056       0.045 KB/sec
 153195 me       /usr/lib/firefox/firefox   surfsh      0.025       0.026 KB/sec
      ? root     unknown TCP                            0.000       0.000 KB/sec

  TOTAL                                                 0.569      13.183 KB/sec





```
All are in the repos.
~$ speedtest```

Retrieving speedtest.net configuration...
Testing from HGC Broadband (223.17.39.178)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by i3D.net (Hong Kong) [9.44 km]: 5.24 ms
Testing download speed..........................................................
......................
Download: 467.05 Mbit/s
Testing upload speed............................................................
..........................................
Upload: 346.28 Mbit/s

```
Upload and download not equal.

I'm suscribing FTTH 500M

nload
please refer to attached screenshot

$ apt policy nethogs```

nethogs:
  Installed: (none)
  Candidate: 0.8.6-3
  Version table:
     0.8.6-3 500
        500 http://hk.mirrors.thegigabit.com/ubuntu jammy/universe amd64 Packages
```
Wether you meant nethogs ?

Regards

---

### Post by satimis on 2023-09-06
> **1fallen said:**
> Instead select Performance toptab>>Network left tree
I couldn't find Network here, only Resources and File Systems on top menu.

How to start your version?

Regards

---

### Post by MAFoElffen on 2023-09-06
@1fallen & grahammechanical -- He might be confused, as I am now. I don't usually use the GUI gnome tools, so I started mine up to see if it matched your attachment... It doesn't (???) I'm not sure of how it is different, but I attached a screenshot.

In mine, with the tabs he describes, it would be under the Resources tab.

@1fallen --- LOL. The File System tab on mine only shows /boot/efi & /boot/grub. The two lines in my fstab. Does not recognise ZFS. What does it show on yours?

---

### Post by #&amp;thj^% on 2023-09-07
> **MAFoElffen said:**
> @1fallen --- LOL. The File System tab on mine only shows /boot/efi & /boot/grub. The two lines in my fstab. Does not recognise ZFS. What does it show on yours?
Don't forget I'm not a Gnome user, but yes  MAFoElffen is right it will look different as he shows.
@ satimis, if your still looking for what I think your after, there is another with a GUI in flatpak
```
io.github.hakandundar34coding.mini-system-monitor/x86_64/stable

```
I'll attach screenshots for both of you, one for MAFoElffen and one for you sattimis showing the App.

---

### Post by satimis on 2023-09-07
> **1fallen said:**
> Don't forget I'm not a Gnome user, but yes  MAFoElffen is right it will look different as he shows.
@ satimis, if your still looking for what I think your after, there is another with a GUI in flatpak
```
io.github.hakandundar34coding.mini-system-monitor/x86_64/stable

```
I'll attach screenshots for both of you, one for MAFoElffen and one for you sattimis showing the App.
Hi MAFoElffen,

$ io.github.hakandundar34coding.mini-system-monitor/x86_64/stable```

bash: io.github.hakandundar34coding.mini-system-monitor/x86_64/stable: No such file or directory

```

Is following link for installing "mini system monitor"?

Install GNOME System Monitor in Ubuntu 22.04
[https://techpiezo.com/linux/install-gnome-system-monitor-in-ubuntu-22-04/](https://techpiezo.com/linux/install-gnome-system-monitor-in-ubuntu-22-04/)

Regards

---

### Post by #&amp;thj^% on 2023-09-07
> **satimis said:**
> Hi MAFoElffen,

$ io.github.hakandundar34coding.mini-system-monitor/x86_64/stable```

bash: io.github.hakandundar34coding.mini-system-monitor/x86_64/stable: No such file or directory

```

Is following link for installing "mini system monitor"?

Install GNOME System Monitor in Ubuntu 22.04
[https://techpiezo.com/linux/install-gnome-system-monitor-in-ubuntu-22-04/](https://techpiezo.com/linux/install-gnome-system-monitor-in-ubuntu-22-04/)

Regards
You need more coffee, I'm 1fallen...LOL
You would install it like:
```
flatpak install io.github.hakandundar34coding.mini-system-monitor/x86_64/stable

```
Do you first have Flatpak installed?

---

### Post by satimis on 2023-09-08
> **1fallen said:**
> You need more coffee, I'm 1fallen...LOL
You would install it like:
```
flatpak install io.github.hakandundar34coding.mini-system-monitor/x86_64/stable

```
Do you first have Flatpak installed?
Hi 1fallen...LOL

Sorry for my mistake.

I have flatpak installed
$ which flatpak```

/usr/bin/flatpak

```

$ sudo flatpak install io.github.hakandundar34coding.mini-system-monitor/x86_64/stable```

Looking for matches…
error: No remote refs found similar to ‘io.github.hakandundar34coding.mini-system-monitor/x86_64/stable’

```

$ sudo flatpak remotes
no output

I'm stuck here.

Regards

---

### Post by deadflowr on 2023-09-08
You need to add the flathub repository.
Also flatpak doesn't require sudo to install packages.

Follow parts 3 and 4 here:
[https://flatpak.org/setup/Ubuntu]("https://flatpak.org/setup/Ubuntu")

---

### Post by satimis on 2023-09-08
> **deadflowr said:**
> You need to add the flathub repository.
Also flatpak doesn't require sudo to install packages.

Follow parts 3 and 4 here:
[https://flatpak.org/setup/Ubuntu]("https://flatpak.org/setup/Ubuntu")
Hi deadflowr,

Tks for your advice.  I have already solved the problem as follow:-

$ flatpak remote-add --if-not-exists flathub [https://flathub.org/repo/flathub.flatpakrepo](https://flathub.org/repo/flathub.flatpakrepo)

$ flatpak install io.github.hakandundar34coding.mini-system-monitor/x86_64/stable```

.......
.......
3. [&#10003;] org.freedesktop.Platform.Locale                   22.08       i  flathub  17.8*kB / 333.4*MB
 4. [&#10003;] org.freedesktop.Platform.openh264                 2.2.0       i  flathub   1.2*MB / 944.3*kB
 5. [&#10003;] org.gtk.Gtk3theme.Yaru                            3.22        i  flathub 328.1*kB / 191.5*kB
 6. [&#10003;] org.freedesktop.Platform                          22.08       i  flathub 207.8*MB / 211.7*MB
 7. [&#10003;] io.github.hakandundar34coding.mini-system-monitor stable      i  flathub   6.9*MB / 5.2*MB

Installation complete.
```

$ flatpak run io.github.hakandundar34coding.mini-system-monitor```


Note that the directories 

'/var/lib/flatpak/exports/share'
'/home/satimis/.local/share/flatpak/exports/share'

are not in the search path set by the XDG_DATA_DIRS environment variable, so
applications installed by Flatpak may not appear on your desktop until the
session is restarted.

```

I can start the "mini system monitor" but it is small.  How can I increase its size?  Thanks
(resize - greyout)

Regards

---

### Post by #&amp;thj^% on 2023-09-08
> **satimis said:**
>  but it is small.  How can I increase its size?  Thanks
(resize - greyout)

Regards
That was the point small lite footprint, the full featured is this one:
```
flatpak install io.github.hakandundar34coding.system-monitoring-center 
```
Same Developer just more bells and whistles. (Including resize)

---

### Post by satimis on 2023-09-09
> **1fallen said:**
> That was the point small lite footprint, the full featured is this one:
```
flatpak install io.github.hakandundar34coding.system-monitoring-center 
```
Same Developer just more bells and whistles. (Including resize)
Hi 1fallen,

I got it.  Thanks.

Do you have suggestion on other monitors?

Regards

---

### Post by The Cog on 2023-09-09
> **satimis said:**
> Hi 1fallen,

I got it.  Thanks.

Do you have suggestion on other monitors?

Regards

I like **btop**. It's command-line but does graphics pretty well. If you only want to see the network traffic, type 124 after starting it.

---

### Post by Dennis N on 2023-09-09
> **satimis said:**
> Hi all
Please advise how to monitor/check the upload and download speeds of the broadband?
Thanks
Regards

I use the gnome shell extension "Net speed Simplified". It displays on the top panel.

---

### Post by satimis on 2023-09-09
> **The Cog said:**
> I like **btop**. It's command-line but does graphics pretty well. If you only want to see the network traffic, type 124 after starting it.
Hi The Cog,

Thanks for your suggestion.

Is it the right article for me to follow; ?
Install btop in Ubuntu 22.04
[https://techpiezo.com/linux/install-btop-in-ubuntu-22-04/](https://techpiezo.com/linux/install-btop-in-ubuntu-22-04/)

I only need to monitor the upload and download speeds, showing them to my FTTH network supplier.

Regards

---

### Post by satimis on 2023-09-09
> **Dennis N said:**
> I use the gnome shell extension "Net speed Simplified". It displays on the top panel.
Hi Dennis N,

Thanks for your advice.

Is it the right ariticle for me to follow; ?
A complete guide to install and use Gnome Shell Extensions on Ubuntu 22.04
[https://linuxhint.com/install-gnome-shell-extensions-ubuntu-22-04/](https://linuxhint.com/install-gnome-shell-extensions-ubuntu-22-04/)

I only need to monitor the download and upload speeds, showing them to my FTTH network supplier.

Regards

---

### Post by Dennis N on 2023-09-09
> **satimis said:**
> Hi Dennis N,

Thanks for your advice.

Is it the right ariticle for me to follow; ?
A complete guide to install and use Gnome Shell Extensions on Ubuntu 22.04
[https://linuxhint.com/install-gnome-shell-extensions-ubuntu-22-04/](https://linuxhint.com/install-gnome-shell-extensions-ubuntu-22-04/)

I only need to monitor the download and upload speeds, showing them to my FTTH network supplier.

Regards

You definitely need this to install and/or manage any extensions. I'm surprised you don't already use it! A screenshot is attached. Click Browse, and there is a search box to enter the extension name or some keyword if are just shopping.

---

### Post by satimis on 2023-09-09
> **Dennis N said:**
>  - snip -
Click Browse, and there is a search box to enter the extension name or some keyword if are just shopping.
Please explain in more detail.

What is "the extension name" ?

Thanks

Regards

---

### Post by Dennis N on 2023-09-09
> **satimis said:**
> Please explain in more detail.

What is "the extension name" ?

Thanks

Regards
See the image I attached to my previous post. See that I have 4 extensions I have installed myself. The extension name is whatever is shown there. In this case, **Net speed Simplified**. Click Browse, then enter that name in the search box (image attached). Keep looking down through results until you see it - the search function seems to return many unwanted matches!

[ATTACH=CONFIG]292707[/ATTACH]

---

### Post by TheFu on 2023-09-11
I like **glances**, but it does much more monitoring.
```
istar (Ubuntu 20.04 64bit / Linux 5.15.0-83-generic) - IP 172.22.22.20/24 Pub 50.73.91.145        Uptime: 2 days, 9:48:15

CPU  [ 14.3%]   CPU      14.3%  nice:     0.0%  ctx_sw:    4K      MEM     67.9%      SWAP     15.8%      LOAD    12-core
MEM  [ 67.9%]   user:    14.2%  irq:      0.0%  inter:   5538      total:  30.7G      total:   4.10G      1 min:    0.17
SWAP [ 15.8%]   system:   0.2%  iowait:   0.2%  sw_int:  1272      used:   20.8G      used:     663M      5 min:    0.27
                idle:    85.3%  steal:    0.0%                     free:   9.86G      free:    3.45G      15 min:   0.32

NETWORK       Rx/s   Tx/s   TASKS 654 (1323 thr), 1 run, 495 slp, 158 oth sorted automatically by CPU consumption
br0           968b   10Kb
enp3s0         3Kb   14Kb   CPU%   MEM%  VIRT  RES       PID USER          TIME+ THR  NI S  R/s W/s  Command
lo              0b     0b   157.7  12.8  4.67G 3.92G    4677 libvirt-q  11h39:04 7     0 S    ? ?    qemu-system-x86_64 -
lxcbr0          0b     0b   4.3    14.0  6.65G 4.29G    4747 libvirt-q   4h20:57 7     0 S    ? ?    /usr/bin/qemu-system
_th6fe5f989    4Kb    2Kb   4.0    0.2   431M  61.4M 2264573 tf             0:00 1     0 R    0 1K   /usr/bin/python3 /us
_th35c55525     0b     0b   0.7    2.9   1.78G 906M     5076 libvirt-q      9:34 7     0 S    ? ?    qemu-system-x86_64 -
_th6676b2ca     0b     0b   0.3    3.7   1.82G 1.13G    4934 libvirt-q     18:52 5     0 S    ? ?    qemu-system-x86_64 -
_thbb5c62fb     0b     0b   0.3    1.6   1.18G 503M     4790 libvirt-q     12:48 5     0 S    ? ?    qemu-system-x86_64 -
virbr0          0b     0b   0.3    1.0   3.08G 330M    11231 1000000        4:01 43    0 S    ? ?    mysqld --defaults-fi
vnet0         448b   616b   0.3    0.0   0     0          93 root           9:16 1     5 S    ? ?    [ksmd]
vnet1          1Kb   800b   0.3    0.0   0     0        2040 root           0:00 1   -20 S    ? ?    [metaslab_group_]
vnet2           0b     0b   0.3    0.0   0     0     2228666 root           0:00 1     0 I    ? ?    [kworker/9:2-events]
vnet3           0b     0b   0.0    8.6   9.50G 2.63G    2639 jellyfin    1h35:40 45    0 S    ? ?    /usr/bin/jellyfin --
vnet4           0b     0b   0.0    4.1   1.48G 1.26G   10038 1000115        0:33 2     0 S    ? ?    /usr/sbin/clamd --fo
                            0.0    0.4   2.26G 116M   600182 1000000        0:13 25    0 S    ? ?    lxd --logfile /var/s
DefaultGateway       18ms   0.0    0.4   6.53G 113M     5196 root           0:32 21    0 S    ? ?    lxd --logfile /var/s
                            0.0    0.3   2.24G 108M   601085 1000000        0:14 25    0 S    ? ?    lxd --logfile /var/s
FILE SYS      Used  Total   0.0    0.2   4.65G 70.3M    3995 gdm            0:29 29    0 S    ? ?    /usr/bin/gnome-shell
/            26.8G  34.2G   0.0    0.2   311M  68.4M    9835 1000033        0:01 1     0 S    ? ?    php-fpm: pool www
/TV          56.2G   293G   0.0    0.2   309M  65.3M    9836 1000033        0:01 1     0 S    ? ?    php-fpm: pool www
/d/D1        3.46T  3.48T   0.0    0.2   78.9M 62.8M 1275477 1000117        0:00 1     0 S    ? ?    /usr/sbin/amavisd-ne
/d/D2        3.43T  3.56T   0.0    0.2   78.6M 62.6M 1337909 1000117        0:00 1     0 S    ? ?    /usr/sbin/amavisd-ne
/d/D3        3.50T  3.58T   0.0    0.2   76.4M 59.9M   11469 1000117        0:00 1     0 S    ? ?    /usr/sbin/amavisd-ne
/d/D6        2.43T  3.54T
2023-09-11 18:12:00 EDT4T

```
I don't know if the glances text will post correctly. There are many columns.

OTOH, speedtest has been flaky the last year for me. 

```
$ speedtest-cli 
Retrieving speedtest.net configuration...
Cannot retrieve speedtest configuration
ERROR: HTTP Error 403: Forbidden
```

But works fine on other systems using the same internet connection:
```
$ speedtest-cli 
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Comcast (Atlanta, GA) [42.47 km]: 19.889 ms
Testing download speed................................................................................
Download: 29.37 Mbit/s
Testing upload speed......................................................................................................
Upload: 6.11 Mbit/s
```
Ya'll.

Sigh.  I miss the 300 Mbps symmetric connection that I had last week, but not the 3 months of incompetent, incorrect, billing from the company.

BTW, that system which got the permission denied error worked less than 5 min later.
```
Download: 28.97 Mbit/s
Upload: 5.96 Mbit/s

```
I'm on a business 30/6 Mbps connection with a /29 subnet.

---

### Post by MAFoElffen on 2023-09-11
Why the curiosity to run multiple GUI network speed monitors at once? Am I missing something there?

Like TheFu and 1fallen, I run the cli tools to check, diagnose and then let them sit until I need them again. I don't need to collect stats unless there is a problem, and watching "a GUI dial" is not going to do that.

Right? Is it just cheap entertainment? I just seem to be confused with that...

---

### Post by TheFu on 2023-09-11
> **MAFoElffen said:**
> Why the curiosity to run multiple GUI network speed monitors at once? Am I missing something there?

Sometimes we are our own worst enemies.  It is a good way to learn, assuming the knowledge is retained. OTOH, if it isn't retained, then it is just wasting time.

Constant network monitoring with the overhead of a GUI is a waste, IMHO.  

I have no problem if it is part of overall system monitoring and stats are gathered every 1-5 minutes along with 50 other system performance data.  Use something like Munin for that.  With the GUI overhead removed, capturing system performance stats isn't a big deal and having 3-12 months of that data is extremely useful.  With all that data, together, figuring out performance problems is easier.

---

### Post by satimis on 2023-09-11
Hi all,

Why I'm interested checking the broadband speed because I'm currently upgrade FTTH from 500M to 1000M.

After upgrade the technician of the broadband company showed me the download/upload speeds about 950M/950M, almost equal speed on a Windows 10 notebook.

Connection:
ONT to PC (direct connection not via router)

But I checked the speed running "speedtest"
(also direct connection)
Download:  about 950M
Upload: only about 560M

I'm curiously to know WHY?

Regards

---

### Post by satimis on 2023-09-12
On my spare PC (OS - ubuntu 22.04)

I follow below link;
Install Ookla Speedtest CLI on Ubuntu 20.04
[https://lindevs.com/install-ookla-speedtest-cli-on-ubuntu](https://lindevs.com/install-ookla-speedtest-cli-on-ubuntu)

install speedtest

$ speedtest --version```

Speedtest by Ookla 1.2.0.84 (ea6b6773cf) Linux/x86_64-linux-musl 6.2.0-32-generic x86_64

The official command line client for testing the speed and performance
of your internet connection.

```

$ speedtest```

......
......
......
Upload:   925.63 Mbps (data used: 451.2 MB)                                                   
                  4.06 ms   (jitter: 0.44ms, low: 2.71ms, high: 5.39ms)
 Packet Loss:     0.0%
  Result URL: https://www.speedtest.net/result/c/c9d22fb7-678c-4cc7-8686-3144ec66d991

```

$ speedtest | grep Download```

    Download:   927.42 Mbps (data used: 453.6 MB)  
    
```

Download: 927.42 Mbps

Download and Upload almost equal

Connection:
FTTH -> ONT -> Router -> PC

It is quite strange.

---

### Post by TheFu on 2023-09-12
> **satimis said:**
>  
Download:  about 950M
Upload: only about 560M

I'm curiously to know WHY?

Could be anything between the system and the remote testing server.  You'll need to 
[LIST=1]
[*]simplify the test setup to isolate each component (hw and sw have many components)
[*]test
[*]repeat.
[/LIST]
Expect 5-20 simplification steps to narrow down the culprit.

---

### Post by satimis on 2023-09-12
> **TheFu said:**
> Could be anything between the system and the remote testing server.  You'll need to 
[LIST=1]
[*]simplify the test setup to isolate each component (hw and sw have many components)
[*]test
[*]repeat.
[/LIST]
Expect 5-20 simplification steps to narrow down the culprit.
Hi TheFu,

Thanks for your advice.

The speedtest package installed on my spare PC works without problem (see #30 above)

Would it be the problem of the speedtest package installed on my daily working PC?

---

### Post by TheFu on 2023-09-12
> **satimis said:**
> Hi TheFu,

Thanks for your advice.

The speedtest package installed on my spare PC works without problem (see #30 above)

Would it be the problem of the speedtest package installed on my daily working PC?

How would I know?  You need to follow the steps. Nobody he can do that for you.  There's no easy answer.  Hardware, software, every layer of each, needs to be tested.

For example, my 2014 GigE router is limited by the OS I choose to run to less than 400 Mbps.  This is a known limitation for the complete stack of hardware, drivers, and software.  If I choose to use some other router software with different drivers, people have gotten 920 Mbps on the same hardware. They blame the drivers for the performance limitation.  Now, that performance limitation is per-thread, so if I open multiple connections, each gets a different thread and with 2 threads, it gets about 700 Mbps.  With 3+ threads, it gets 920 Mbps, which is about the max limitation of the GigE protocol with ethernet overhead.  If you are shown more than about 940 Mbps in any speed test on GigE hardware, they aren't using IP as the protocol. Basically, 950 Mbps is a lie.  

If you have 2.5Gbps or 10Gbps hardware that is software limited to 1 Gbps, the rules are different.

Bandwidth isn't everything.  Predictability matters more to me.

---

### Post by satimis on 2023-09-12
> **TheFu said:**
> How would I know?  You need to follow the steps. Nobody he can do that for you.  There's no easy answer.  Hardware, software, every layer of each, needs to be tested.

For example, my 2014 GigE router is limited by the OS I choose to run to less than 400 Mbps.  This is a known limitation for the complete stack of hardware, drivers, and software.  If I choose to use some other router software with different drivers, people have gotten 920 Mbps on the same hardware. They blame the drivers for the performance limitation.  Now, that performance limitation is per-thread, so if I open multiple connections, each gets a different thread and with 2 threads, it gets about 700 Mbps.  With 3+ threads, it gets 920 Mbps, which is about the max limitation of the GigE protocol with ethernet overhead.  If you are shown more than about 940 Mbps in any speed test on GigE hardware, they aren't using IP as the protocol. Basically, 950 Mbps is a lie.  

If you have 2.5Gbps or 10Gbps hardware that is software limited to 1 Gbps, the rules are different.

Bandwidth isn't everything.  Predictability matters more to me.
Please refers to my posting #29 above.  I only need to check the band width of Download and Upload.

**[COLOR="#FF0000"]Performed following steps to solve my problem;[/COLOR]**

On daily working PC

Uninstall the old speedtest-cli package

$ speedtest --version```

speedtest-cli 2.1.3
Python 3.10.12 (main, Jun 11 2023, 05:26:28) [GCC 11.4.0]

```

$ sudo apt-get purge speedtest-cli```

.......
The following packages will be REMOVED:
  speedtest-cli*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 106 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 283266 files and directories currently installed.)
Removing speedtest-cli (2.1.3-2) ...
Processing triggers for man-db (2.10.2-1) ...

```

Install Ookla Speedtest CLI on Ubuntu 20.04
[https://lindevs.com/install-ookla-speedtest-cli-on-ubuntu](https://lindevs.com/install-ookla-speedtest-cli-on-ubuntu)

$ wget -qO - [https://packagecloud.io/install/repositories/ookla/speedtest-cli/script.deb.sh](https://packagecloud.io/install/repositories/ookla/speedtest-cli/script.deb.sh) | sudo bash```

Detected operating system as Ubuntu/jammy.
Checking for curl...
Detected curl...
Checking for gpg...
Detected gpg...
Detected apt version as 2.4.9
Running apt-get update... done.
Installing apt-transport-https... done.
Installing /etc/apt/sources.list.d/ookla_speedtest-cli.list...done.
Importing packagecloud gpg key... Packagecloud gpg key imported to /etc/apt/keyrings/ookla_speedtest-cli-archive-keyring.gpg
done.
Running apt-get update... done.

The repository is setup! You can now install packages.

```

$ sudo apt install -y speedtest```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  speedtest
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,106 kB of archives.
After this operation, 2,628 kB of additional disk space will be used.
Get:1 https://packagecloud.io/ookla/speedtest-cli/ubuntu jammy/main amd64 speedtest amd64 1.2.0.84-1.ea6b6773cf [1,106 kB]
Fetched 1,106 kB in 1s (1,256 kB/s)
Selecting previously unselected package speedtest.
(Reading database ... 283255 files and directories currently installed.)
Preparing to unpack .../speedtest_1.2.0.84-1.ea6b6773cf_amd64.deb ...
Unpacking speedtest (1.2.0.84-1.ea6b6773cf) ...
Setting up speedtest (1.2.0.84-1.ea6b6773cf) ...
Processing triggers for man-db (2.10.2-1) ...

```

$ speedtest --version```

Speedtest by Ookla 1.2.0.84 (ea6b6773cf) Linux/x86_64-linux-musl 6.2.0-26-generic x86_64

The official command line client for testing the speed and performance
of your internet connection.

```


**[COLOR="#FF0000"]Connection:[/COLOR]**

1)
FTTH -> ONT -> Router -> PC
$ speedtest | grep Download```

    Download:   937.33 Mbps (data used: 468.1 MB)

```                                                 

$ speedtest | grep Upload```

      Upload:   924.26 Mbps (data used: 438.7 MB)   

```

Download and Upload speeds are almost same

2)
FTTH -> ONT -> PC

$ speedtest | grep Download```

    Download:   938.79 Mbps (data used: 436.1 MB)   

```

$ speedtest | grep Upload```

      Upload:   933.16 Mbps (data used: 467.4 MB)

```

Download and Upload speeds are almost same                              

Very little loss via router

---

