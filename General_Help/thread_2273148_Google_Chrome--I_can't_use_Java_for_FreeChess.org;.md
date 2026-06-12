---
title: "Google Chrome--I can't use Java for FreeChess.org; tar zxvf jre-8u40-linux-i586.tar."
date: 2015-04-10
forum: General Help
---

### Post by SciGuy1872 on 2015-04-10
[SIZE=2][COLOR=#222222][FONT=Verdana]Ihave tried to make the Jin applet for FreeChess.org work with Chrome 
([/FONT][/COLOR]Google Chrome    41.0.2272.118 (Official Build); JavaScript    V8 4.1.0.27)[COLOR=#222222][FONT=Verdana];I am able to use the applet both in Opera and Firefox.  I downloaded the i386 version, created a /usr/java/ directory and thenpasted the file there and ran: "sudo tar zxvfjre-8u40-linux-i586.tar.gz", like I found on: [www.java.com/en/download/help/linux_install.xml]("http://www.java.com/en/download/help/linux_install.xml")  I alsocreated a symbolic link with the command: "sudo ln -s/usr/java/lib/i386/libnpjp2.so"  However, I restartedChrome and the applet still did not load--I tried removing the JDK and IcedTea, versions 7 and 6, programs from the Software Center.  I re-added them after seeing that they were not the problem. [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]
Here is a list of the commands I entered:

[/FONT][/COLOR]
sudo mkdir /usr/java/
cd /usr/java
sudo tar zxvf jre-8u40-linux-i586.tar.gz
cd /opt/google/chrome/plugins
sudo ln -s /usr/java/lib/i386/libnpjp2.so

While doing this process, I did not receive any errors to report.  [/SIZE] I have Precise Pangolin.[SIZE=2]
Is there any advice?  I use Chrome the most and was wanting to play through it, instead of opening Firefox or Opera just to play chess on the Internet. 



[/SIZE][SIZE=5][SIZE=2]
Thanks,
    Anthony
[/SIZE]

[/SIZE]

---

