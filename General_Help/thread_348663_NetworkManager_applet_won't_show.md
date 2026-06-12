---
title: "NetworkManager applet won't show"
date: 2007-01-29
forum: General Help
---

### Post by Nunyah on 2007-01-29
Hey guys!

I have a problem concerning the gnome version of NetworkManager. I don't see the applet. In fact, I've never seen the applet, not even since I installed 6.10.

Until now, I've used Wifi-radar to manage my network connections, but WPA has never really worked, which kinda sucks, as most AP's use this today.

The NetworkManager, it's deamon and the applet is all listet as running processes.

I've tried to uninstall it serveral times, I've also tried to uninstall Wifi-radar in case they couldn't work together. I've picked up a numerous tips around, like commenting out most of the stuff in the interface file. If I manually try to start the NetworkManager, I get no error whatsoever.

Simply put, the applet won't show!

I would be forever thankful if any of you could help me with this.

---

### Post by r4ik on 2007-01-29
How to Configure Ubuntu/Kubuntu with WPA using Network-Manager

Ubuntu Dapper in typical cases can configure WPA to work out of the box with minimal hassle. You'll need to install network-manager.


For Ubuntu:

sudo apt-get install network-manager-gnome

For Kubuntu (will install knetworkmanager):

sudo apt-get install network-manager-kde

Logout/Reboot.

Ubuntu users should now see the NetworkManager Applet in the Gnome notification area. Kubuntu users will probably have to run knetworkmanager before they see NetworkManager in the systray.

If instead, you get a "The NetworkManager applet could not find some required resources. It cannot continue." message, then:

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor

Once Network-Manager is installed, click on the NM icon in the notification area (default is at the top right of Ubuntu/Gnome). Choose your network, then enter your passphrase. Type a password for the keyring, and you're set.

If you don't see your network, click "Create New Wireless Network...", type your essid/networkname, then choose "WPA Personal" for wireless security.

    * Note: If you installed Kubuntu then installed ubuntu-desktop & network-manager-gnome, you may not be able to use network-manager in Gnome, if at all. In this case, you may have to use WPA Supplicant and do some manual editing of conf files to get WPA up and running. 

    * Note: When you first log into Gnome/KDE, the keyring application will ask for a password. Future revisions of Network-Manager should resolve this. 

Good luck !

---

### Post by Nunyah on 2007-01-29
Thanks, but I've allready tried guides like that. There's no errors and everything seems smooth, except that the applet won't show up in the notification area (or any other places AFAIK).

---

### Post by strabes on 2007-01-29
run "nm-applet &"

---

### Post by Nunyah on 2007-01-30
> user@vultux:~$ nm-applet &
[1] 15133
As you can see, the process is running as it should..

---

### Post by golem3 on 2007-01-30
Believe it or not, the Network Manager gave me so much grief I was forced to re-install Ubuntu. Of course, I had also messed up some other things, but the NM applet caused serious issues AFTER I removed it from the menu by mistake. I found there was no way of restoring it. I tried re-installing the package, uninstalling and then reinstalling...nothing.

---

### Post by Nunyah on 2007-01-31
Hmm, what you describe is very related to my problems... I accidently deleted my top panel and had to add icons manually again, but I'm pretty sure I diddn't have the NM applet before, though I may be wrong here as I was pretty new to Linux and Ubuntu. (still is..)

Anyone got a solution in order to force the applet to show itself? I don't really want to do a clean install just yet..

---

### Post by Karl S. on 2007-02-11
Having a similar problem. Running Xubuntu (6.10) and Knetworkmanager often doesn't appear in my top panel. My wireless seems to be running fine now, so it's not a *huge* problem. But it is an annoyance.

Knetworkmanager is running, by the way, if this noob (me) interpreted this right:

karl@karl-laptop:~$ nm-applet &
[1] 5414

NEVERMIND: it seems to have fixed itself. It's on my menu bar again.

---

### Post by wuziq on 2007-03-15
I am having a similar problem.  I'm running Xubuntu 6.10.  The weird thing is, nm-applet just suddenly stopped showing up today.  All of last week, it showed up and worked fine, I could pick networks, etc etc.  It IS running, as I see it as one of the running processes.  I can kill it and restart it, and still nothing.  I'm not getting any errors, I've tried both nm-applet and nm-applet --sm-disable.  I didn't remove the System Tray because I can still see it (there's a frame around it).  I'm hoping someone could ask some pointed questions to see if somehow my configuration is weird or something, cuz I just don't know what else to do, short of reformatting.. :(

---

### Post by funzero on 2007-03-16
I am also having a similar problem.  Reinstalled twice and set up for my broadcom chipset bcm4306 using fwcutter.  Wireless is working but no icon for wireless in the information bar.  I am also using 6.10 and installed network manager.  Hope some can fix this...I'm new to Linux.

---

### Post by stephen53 on 2007-03-18
Had this problem also. I had deleted my notification area by mistake. When I added it back in the nm-applet appeared. Just right click on your panel and then add to panel. Find that applet (notification area)  and add it .Hope this helps.

---

### Post by lmidnight on 2007-04-06
> **stephen53 said:**
> Had this problem also. I had deleted my notification area by mistake. When I added it back in the nm-applet appeared. Just right click on your panel and then add to panel. Find that applet (notification area)  and add it .Hope this helps.

thank you. thank you. this was driving me nuts for the last 2 days! i had the same problem. thanks for the help.

---

### Post by strabes on 2007-04-06
lol, I thought you would have thought of that (checking for the notification area) so I didn't bother posting about it. Feisty comes with network-manager-gnome or network-manager-kde by default.

---

### Post by watzlaw.wutz on 2007-04-21
in order to make the network manager applet to show up again you just need to add the gnome notification applet.

best regards, watzlaw

---

