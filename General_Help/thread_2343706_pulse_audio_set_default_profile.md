---
title: "pulse audio set default profile"
date: 2016-11-18
forum: General Help
---

### Post by kfboerne on 2016-11-18
os = Xubuntu16.04

Hello,
I have posted my problem on the Ubuntu forum of the country where I live but there was no useful response so now I hope this forum can help me.

In Pulse Audio Volume Control (tab Configuration) I want to make HDMI output the default profile. At this moment after a reboot HDMI switches back to analog every time so I have to set it back to HDMI manually. Very annoying.

I am not very technical and have tried so many things that I'm getting a little bit frustrated. 

The output of 'pacmd list-sinks' =_alsa_output.pci-0000_00_1b.0.hdmi-stereo_ and the output of 'pacmd list-sources | grep name:' =_alsa_output.pci-0000_00_1b.0.hdmi-stereo.monitor_
I have pasted these rules in several configuration files (such as/etc/pulse/default.pa,.config/pulse > in the 'default sink' and 'default source' files), saved the file(s) and rebooted my pc but every time the default profile is the analog-profile and NOT the HDMI-profile.

Can anybody please tell me what I am doing wrong since I am out ofoptions. The main question is : where do I paste the above mentioned rules in order to set the default profile to HDMI? When the 'stuff'with the rules isn't correct, what than can I do? I have googled so much and followed all instructions but nothing works for me! 

Thankyou!

---

### Post by kfboerne on 2016-11-19
Anybody perhaps[IMG]https://ubuntuforums.org/images/icons/icon7.png[/IMG]?

---

