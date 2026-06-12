---
title: "Java Plug-in doesn't work in FireFox"
date: 2008-05-19
forum: General Help
---

### Post by BobtheBlueBerry on 2008-05-19
HI. I'm running Ubuntu 8.04 LTS. When I try to run a Java Applet in FireFox 3 Beta 5, it just asks me to install missing plug-ins, and when I select 'Sun Java 6' (or similar), the Synaptic Package Manager just tells me 'this package has already been installer' (I installed it a while ago). I downloaded FireFox 2.0.0.14, and it just tells me install the JRE.

Please help if you can.

Thanks, B&#9786;B.

---

### Post by ibuclaw on 2008-05-19
Firstly, type in these commands:
```
sudo apt-get install ubuntu-restricted-extras sun-java6-plugin
```
To install the proper packages for the Firefox Plugin.

Secondly, type in:
```
rm $HOME/.mozilla/firefox/pluginreg.dat
```
And then restart Firefox to reset/renew the plugin list (Firefox will re-create the file on startup).

If the above fails, [read here.]("http://ubuntuforums.org/showthread.php?t=661833")

Regards
Iain

---

