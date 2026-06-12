---
title: "Getting rules to the firewall to stick after reboot"
date: 2017-02-11
forum: General Help
---

### Post by frederyck2 on 2017-02-11
I've been running Ubuntu since 2008, and while I'm very far from an expert, especially when it comes to the firewall, I know my way around the OS half decently. 

Yesterday I installed a fresh Ubuntu 16.04 on a new SSD disk, and everything seemed peachy. I connected to the wireless, installed a few programs, including Chrome, and things generally went smoothly. Then I fired up the Videostream extension to Chrome to cast to my Chromecast. I know from prior experiences that the computer wouldn't be able find the Chromecast or use Videostream without these fixes:

```
sudo iptables -I INPUT -p udp -m udp --dport 32768:61000 -j ACCEPT
sudo firewall-cmd --add-port=5556/tcp
sudo firewall-cmd --add-port=5558/tcp


```

links to where I found the commands:
[http://askubuntu.com/questions/324236/how-can-i-use-chromecast](http://askubuntu.com/questions/324236/how-can-i-use-chromecast)
[http://community.getvideostream.com/topic/507/firewall-issues-on-linux](http://community.getvideostream.com/topic/507/firewall-issues-on-linux)


I needed to do them before my last installation and the commands worked beautifully then, and worked beautifully this time. Except they don't seem to stick when I reboot. I need to do them everytime I start the system. It's not that big of a deal, but it seems strange that my last installation of Ubuntu (also 16.04) on another disk didn't need repeating the commands after a reboot.

As I said, I'm not too familiar with the firewall, so is there anything I've missed to make the changes stick?

---

### Post by Perfect Storm on 2017-02-11
Have you tried with **--permanent** flag.

---

### Post by frederyck2 on 2017-02-11
Thank you, that seemed to work for the firewall commands as they were still in place after a reboot! Yay! Iptables, however, doesn't seem to have that flag.

---

### Post by Perfect Storm on 2017-02-11
[https://www.thomas-krenn.com/en/wiki/Saving_Iptables_Firewall_Rules_Permanently](https://www.thomas-krenn.com/en/wiki/Saving_Iptables_Firewall_Rules_Permanently)

---

### Post by SeijiSensei on 2017-02-11
Programs that need to run with root privileges during boot can be invoked in /etc/rc.local.  Put the iptables command there without sudo but with the full path /sbin/iptables.

---

### Post by frederyck2 on 2017-02-12
Thank you, both of you! I still have no idea why it worked without these actions on my old installation... :)

---

