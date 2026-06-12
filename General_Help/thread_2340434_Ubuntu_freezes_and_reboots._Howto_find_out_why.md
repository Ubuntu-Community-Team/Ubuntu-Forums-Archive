---
title: "Ubuntu freezes and reboots. Howto find out why?"
date: 2016-10-18
forum: General Help
---

### Post by elmurdoque on 2016-10-18
Hi there.

I recently swapped my machine and now i run into the problem that it freezes from time to time. 
The picture will freeze, the sound will loop the last 10th of a second and neither mouse nor keyboard respond. 
After a few seconds in this state, i get a purple screen and then the machine reboots. 

I tried to find out what log files might be helpful, but so far, google was of no big help for me. I'm fairly new to Ubuntu. 

It feels that the freezing occurs more frequently when there is some load on the system, but it is more a feeling than a measured fact. 

I know that specs might help here, so i post what i know: 

Ubuntu 16.04 64 bit
i5 4670T cpu
Nvidia Geforce GTX950 gpu (using nvidia driver ver 367.44 as suggested on the nvidia homepage)
8gig memory

Could anyone please point me into the right direction ?

---

### Post by TheFu on 2016-10-18
You were on the right track. My google-fu is strong from years of use.

Google for "**ubuntu logs**" found this: 
* [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
* [http://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located/186280](http://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located/186280)
* [http://askubuntu.com/questions/297053/where-are-all-ubuntu-logs-terminal-history-stored](http://askubuntu.com/questions/297053/where-are-all-ubuntu-logs-terminal-history-stored)
* [http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)
as the first 4 results. These are all reputable locations.

My personal take on log files; [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

When you are really, really new to a topic as vast as "linux", google isn't really useful until the base-knowledge is gained.

---

