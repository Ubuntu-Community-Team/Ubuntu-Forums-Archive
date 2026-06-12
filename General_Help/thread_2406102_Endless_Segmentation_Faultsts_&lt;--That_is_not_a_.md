---
title: "Endless Segmentation Faultsts &lt;--That is not a typo"
date: 2018-11-15
forum: General Help
---

### Post by darobman2 on 2018-11-15
Version: Ubuntu 18.04 LTS
Hardware: Nutanix Virtual Environment
Other Software:  NginX , MySQL

I am unable to perform a update/upgrade to our OS.  The process always terminates with the error Segmentation Faultsts

Example 1:
[FONT=lucida console]arthurb@hawvmoc16tv:~$ sudo apt-get update[/FONT]
[FONT=lucida console]Hit:1 [http://nginx.org/packages/mainline/ubuntu](http://nginx.org/packages/mainline/ubuntu) bionic InRelease[/FONT]
[FONT=lucida console]Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB][/FONT]
[FONT=lucida console]Hit:3 [http://repo.mysql.com/apt/ubuntu](http://repo.mysql.com/apt/ubuntu) bionic InRelease[/FONT]
[FONT=lucida console]Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease[/FONT]
[FONT=lucida console]Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB][/FONT]
[FONT=lucida console]Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB][/FONT]
[FONT=lucida console]Fetched 247 kB in 7s (34.9 kB/s)[/FONT]
[FONT=lucida console]Segmentation faultsts... 0%[/FONT]


Example 2:
[FONT=lucida console]arthurb@hawvmoc16tv:~$ sudo apt-get install -f                                  [sudo] password for arthurb:[/FONT]
[FONT=lucida console]Segmentation faultsts... 0%[/FONT]




Example 3:
[FONT=lucida console]arthurb@hawvmoc16tv:~$ sudo apt-get dist-upgrade[/FONT]
[FONT=lucida console]Segmentation faultsts... 0%[/FONT]



In addition to running the commands above, I have also run *apt-get clean* , [COLOR=#000000][I]sudo rm /var/cache/apt/*.bin

[/I][/COLOR]I've been around the internet and can't find an answer that fits my criteria, i'm hoping someone here can help me dive deeper.  Thanks in advance!

---

