---
title: "Randomly kills all my windows and logs me out"
date: 2024-10-27
forum: General Help
---

### Post by dangerous001 on 2024-10-27
I bought a refurbished Lenovo IdeaPad with core i9 and 32GB RAM. It came with windows 11. I installed ubuntu 24.04 on it. It runs amazingly fast - loving it.

Several times a day, it will close all my windows and log me out. How do I debug this? There are so many log files in linux. Which ones should I look at?

I used to use ubuntu/linux a lot around 10 years back and then switched to mac for the last 10 years. 

I get so frustrated sometimes that I am thinking of just moving back to mac though I love the feeling of using linux/OSS and would like to continue using it.

The programs I run:
- brave browser
- gvim
- terminal
- winamp in wine
- Discord
- Transmission
- mac os inside qemu.
- signal
- telegram
- nordvpn
- pihole/dnsmasq
- Thinkorswim (java)
- calibre



[FONT=courier new]$ sudo apt upgrade 


Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libcjson1 libpostproc57 libavcodec60 libavcodec60 libavutil58 libavutil58
  libswscale7 libswresample4 libswresample4 libavformat60 libavfilter9
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)
The following upgrades have been deferred due to phasing:
  file-roller python3-distupgrade shotwell shotwell-common
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.



$ sudo apt update
Hit:1 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease
Hit:2 [https://updates.signal.org/desktop/apt](https://updates.signal.org/desktop/apt) xenial InRelease                  
Hit:4 [https://tvd-packages.tradingview.com/ubuntu/stable](https://tvd-packages.tradingview.com/ubuntu/stable) jammy InRelease       
Hit:3 [https://linux-packages.resilio.com/resilio-sync/deb](https://linux-packages.resilio.com/resilio-sync/deb) resilio-sync InRelease
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security InRelease [126 kB]      
Hit:6 [https://ppa.launchpadcontent.net/atareao/telegram/ubuntu](https://ppa.launchpadcontent.net/atareao/telegram/ubuntu) noble InRelease 
Hit:7 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) noble InRelease           
Hit:8 [https://ppa.launchpadcontent.net/brandonsnider/cdrtools/ubuntu](https://ppa.launchpadcontent.net/brandonsnider/cdrtools/ubuntu) noble InRelease
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/main amd64 Components [7,184 B]
Get:10 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) noble-updates InRelease [126 kB]            
Hit:11 [https://ppa.launchpadcontent.net/flexiondotorg/quickemu/ubuntu](https://ppa.launchpadcontent.net/flexiondotorg/quickemu/ubuntu) noble InRelease
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/restricted amd64 Components [212 B]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/universe amd64 Components [51.9 kB]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/multiverse amd64 Components [212 B]                  
Get:15 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) noble-backports InRelease [126 kB]
Get:16 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) noble-updates/main amd64 Packages [599 kB]
Get:17 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) noble-updates/main amd64 Components [114 kB]
Get:18 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) noble-updates/restricted amd64 Components [212 B]                                                                                                                                                                                  
Get:19 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) noble-updates/universe amd64 Packages [709 kB]                                                                                                                                                                                     
Get:20 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) noble-updates/universe i386 Packages [437 kB]                                                                                                                                                                                      
Get:21 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) noble-updates/universe amd64 Components [305 kB]                                                                                                                                                                                   
Get:22 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) noble-updates/multiverse amd64 Components [940 B]                                                                                                                                                                                  
Get:23 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) noble-backports/main amd64 Components [208 B]                                                                                                                                                                                      
Get:24 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) noble-backports/restricted amd64 Components [216 B]                                                                                                                                                                                
Get:25 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) noble-backports/universe amd64 Components [21.1 kB]                                                                                                                                                                                
Get:26 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) noble-backports/multiverse amd64 Components [212 B]                                                                                                                                                                                
Fetched 2,625 kB in 10s (275 kB/s)                                                                                                                                                                                                                                            
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
6 packages can be upgraded. Run 'apt list --upgradable' to see them.
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'https://brave-browser-apt-release.s3.brave.com stable InRelease' doesn't support architecture 'i386'
W: [http://linux-packages.resilio.com/resilio-sync/deb/dists/resilio-sync/InRelease:](http://linux-packages.resilio.com/resilio-sync/deb/dists/resilio-sync/InRelease:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
N: Skipping acquire of configured file 'non-free/binary-i386/Packages' as repository 'http://linux-packages.resilio.com/resilio-sync/deb resilio-sync InRelease' doesn't support architecture 'i386'
[/FONT]
Log files are [here]("https://drive.google.com/drive/folders/1sNspz5TJW6bGslPfnI-VrESthyIo6xkR"): 

$ cat /var/log/syslog > var-log-syslog.txt
$ cat /var/log/auth.log > var-log-syslog.txt
$ cat /var/log/auth.log > var-log-auth-log.txt
$ journalctl -b  # View logs from the current boot

How do I enable DEBUG logs?

Thank you!

---

### Post by 1fallen on 2024-10-27
Would you please run our system-info script, and at the end it will  provide a link; just paste that link back here in your thread.
```
wget -N -t 5 -T 10 https://github.com/Mafoelffen1/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info --details

```

---

### Post by dangerous001 on 2024-10-27
> **1fallen2 said:**
> Would you please run our system-info script, and at the end it will  provide a link; just paste that link back here in your thread.
```
wget -N -t 5 -T 10 https://github.com/Mafoelffen1/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info --details

```

I was using gnome classic before. Now, I installed KDE and switched to plasma window manager.

[https://termbin.com/4ol7](https://termbin.com/4ol7)

---

### Post by 1fallen on 2024-10-27
This I need to check, but will you now include:
```
inxi -m
```
This is what I'm seeing:
```
---------- Memory Information:
               total        used        free      shared  buff/cache   available
Mem:           31698       25403        1253        1799        7475        6295
Swap:           8191         564        7627

```
It's hard for me to imagine why your using 25 Gigs of ram. I only use 16 Gigs total and never come close to that???

---

### Post by Doug S on 2024-10-27
> **1fallen2 said:**
> 
It's hard for me to imagine why your using 25 Gigs of ram. I only use 16 Gigs total and never come close to that???
+1.
I noticed the same. There is a lot of stuff in use, maybe try not using one or two things at a time and see if there is any difference. First, I would try not using the brave-browser as it shows many many times in the tty list

---

### Post by dangerous001 on 2024-10-28
[FONT=monospace][FONT=courier new][COLOR=#B218B2]$[/COLOR][COLOR=#000000] inxi -m[/COLOR]
[COLOR=#5454FF]**Memory:**[/COLOR][COLOR=#000000][/COLOR]
  [COLOR=#5454FF]**System RAM:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454FF]**total:**[/COLOR][COLOR=#000000] 32 GiB [/COLOR][COLOR=#5454FF]**available:**[/COLOR][COLOR=#000000] 30.96 GiB [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#000000] 24.14 GiB (78.0%)[/COLOR]
  [COLOR=#5454FF]**Message:**[/COLOR][COLOR=#000000] For most reliable report, use superuser + dmidecode.[/COLOR]
  [COLOR=#5454FF]**Array-1:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454FF]**capacity:**[/COLOR][COLOR=#000000] 32 GiB [/COLOR][COLOR=#5454FF]**slots:**[/COLOR][COLOR=#000000] 8 [/COLOR][COLOR=#5454FF]**modules:**[/COLOR][COLOR=#000000] 8 [/COLOR][COLOR=#5454FF]**EC:**[/COLOR][COLOR=#000000] None[/COLOR]
  [COLOR=#5454FF]**Device-1:**[/COLOR][COLOR=#000000] Controller0-ChannelA [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] LPDDR5 [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 4 GiB [/COLOR][COLOR=#5454FF]**speed:**[/COLOR][COLOR=#000000] 7467 MT/s[/COLOR]
  [COLOR=#5454FF]**Device-2:**[/COLOR][COLOR=#000000] Controller0-ChannelB [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] LPDDR5 [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 4 GiB [/COLOR][COLOR=#5454FF]**speed:**[/COLOR][COLOR=#000000] 7467 MT/s[/COLOR]
  [COLOR=#5454FF]**Device-3:**[/COLOR][COLOR=#000000] Controller0-ChannelC [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] LPDDR5 [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 4 GiB [/COLOR][COLOR=#5454FF]**speed:**[/COLOR][COLOR=#000000] 7467 MT/s[/COLOR]
  [COLOR=#5454FF]**Device-4:**[/COLOR][COLOR=#000000] Controller0-ChannelD [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] LPDDR5 [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 4 GiB [/COLOR][COLOR=#5454FF]**speed:**[/COLOR][COLOR=#000000] 7467 MT/s[/COLOR]
  [COLOR=#5454FF]**Device-5:**[/COLOR][COLOR=#000000] Controller1-ChannelA [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] LPDDR5 [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 4 GiB [/COLOR][COLOR=#5454FF]**speed:**[/COLOR][COLOR=#000000] 7467 MT/s[/COLOR]
  [COLOR=#5454FF]**Device-6:**[/COLOR][COLOR=#000000] Controller1-ChannelB [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] LPDDR5 [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 4 GiB [/COLOR][COLOR=#5454FF]**speed:**[/COLOR][COLOR=#000000] 7467 MT/s[/COLOR]
  [COLOR=#5454FF]**Device-7:**[/COLOR][COLOR=#000000] Controller1-ChannelC [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] LPDDR5 [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 4 GiB [/COLOR][COLOR=#5454FF]**speed:**[/COLOR][COLOR=#000000] 7467 MT/s[/COLOR]
  [COLOR=#5454FF]**Device-8:**[/COLOR][COLOR=#000000] Controller1-ChannelD [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] LPDDR5 [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 4 GiB [/COLOR][COLOR=#5454FF]**speed:**[/COLOR][COLOR=#000000] 7467 MT/s[/COLOR]
[/FONT]
[/FONT]

---

### Post by dangerous001 on 2024-10-28
Thanks @1Fallen2 & @Doug S for pointing me in the right direction! I will try to debug why so much RAM is being used. Would be nice if ubuntu would show me a warning popup saying that too much RAM is being used instead of just logging out without warning.

---

### Post by 1fallen on 2024-10-28
Yes much better now!
```
[FONT=monospace][FONT=courier new][COLOR=#000000][/COLOR][COLOR=#5454FF]**available:**[/COLOR][COLOR=#000000] 30.96 GiB [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#000000] 24.14 GiB (78.0%)
```

I'll bet your random logouts are gone now. (or i hope they are)
You was aware of the many open Brave-browsers in your TTY's right? if not that is a good place to investigate.

[/COLOR][/FONT][/FONT]

---

### Post by dangerous001 on 2024-10-29
Yes, random logouts are gone after I switched from gnome classic to plasma. Thank you very much!

---

