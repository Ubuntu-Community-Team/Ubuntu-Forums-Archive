---
title: "PS3 Media Server not opening, java not found"
date: 2013-04-09
forum: General Help
---

### Post by Blackbart42 on 2013-04-09
Hello,

This is my first time posting on the forums but I've tried everthing and cannot find an answer anywhere. My problm is that I am unable to run PS3 Media Server (PMS) on Ubuntu 12.10. I run the 32 bit edition on my laptop. 

When I try to open PMS from the unity menu nothing happens, and when I try to open it from the terminal with the command "ps3mediaserver" I get the output  

> /usr/bin/ps3mediaserver: 34: exec: /usr/local/java/jdk*/bin/java: not found

When I first installed PMS it worked wonderfully, but I installed Open JDK and Open JRE to try to get Minecraft working and ever since then I've had this problem. I've given up on Minecraft for now. I assumed that PMS did not run with Open Java and I needed Oracle Java instead.

In my attempts to fix PMS I've purged java using [these instructions]("http://askubuntu.com/questions/84483/how-to-completely-uninstall-java") and uninstalled PMS to the best of my ability. I then re-installed Java 7 from oracle using [these instructions.]("http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html") I then re-installed PMS from the PPA using these commands:

> sudo add-apt-repository 
ppa:happy-neko/ps3mediaserver 
sudo apt-get update sudo apt-get install ps3mediaserver

PMS still didn't work and I got the same output from the terminal. I thought that maybe PMS didn't work with Java 7 so i and installed Java 6 using [these instructions]("http://www.liberiangeek.net/2012/11/install-oracle-java-jrejdk-6-in-ubuntu-12-10-quantal-quetzal/"). Still no luck. 

Does anyone have any ideas?

Thanks!

---

### Post by Blackbart42 on 2013-04-09
UPDATE:

I uninstalled PMS again using 

> sudo apt-get purge ps3mediaserver
rm -rf ~/.config/ps3mediaserver

and am purging java again using the same process I used before. I will then try installing Open Java again and will try that instead with all other java properly removed. If that doesn't work I plan to try to get Plex, an alternative application that is not java based, working. I'll report back once I've figured this out or once I'm stumped again.

---

### Post by ppjdee on 2013-04-09
> **Blackbart42 said:**
>  I've given up on Minecraft for now

Pretty much unrelated, but I found Minecraft pretty simple to install and get it working.

---

### Post by Blackbart42 on 2013-04-10
UPDATE: Everything broke and I started getting errors about a GPU hang ever minute or so. I wiped the machine installed the Ubuntu 13.04 Beta. Now the machine works again, but PMS is still broken. Plex didn't work due to permissions issues that I am not skilled enough to fix. I think the GPU errors came from my Nvidia Optimus GT540M card not working well with Ubuntu. Now in 13.04 I can't get the Nvidia drivers to wirk and can't get Bumblebee to work, but that's an issue for another forum post.

---

