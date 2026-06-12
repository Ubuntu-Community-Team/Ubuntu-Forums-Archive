---
title: "Network Manager not 'there'"
date: 2006-12-22
forum: General Help
---

### Post by Mr Sprout on 2006-12-22
I've been trying to install network manager via the add/remove applications tool in the breezy applications menu. After I install it tells me I can run the program from the Internet sub-section in my applications menu. 

However, Network Manager is not there when I go to check. According to the SPM and the add/remove programs tool it's fully installed but I cant find a way to run it. 

I'm running Ubuntu 6.10.

Any help would be appreciated.

](*,)

---

### Post by cbudden on 2006-12-22
If you add nm-applet --sm-disable to your startup programs list, you will get a icon in your system tray, which is network manager.

---

### Post by goatdad13 on 2006-12-24
I have entered that and I still get no icon. I also tried Alt+F2 and entered nw-applet and that didn't work. I also tried it from command line and nothing happened then either. Luckily, I have been able to use Wireless Assistant. WA has been able to connect me to my home network.

---

### Post by fragos on 2006-12-24
I found a better solution for my tastes.  First remove the gnome-network-manager.  You will may also need to disable nm-applet in your startup list.  Then install wifi-radar.  It will appear in the Internet menu and you'll be able to drag the icon from that menu to place it in the applet bar.  Click on it up there and you get a list of available wifi connections.  You can also easily configure for that and future use of that same connection.  If you also have the network-monitor applet it will both give you detailed information and alllow you to select which physical port to use for connection to the Internet.  When connected by wifi another icon pops up next to the network monitor icon that gives you a graphical indication of signal strength.  wifi-radar and network monitor work very well together.

---

