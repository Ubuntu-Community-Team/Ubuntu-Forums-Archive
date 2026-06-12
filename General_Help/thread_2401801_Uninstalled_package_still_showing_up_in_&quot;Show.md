---
title: "Uninstalled package still showing up in &quot;Show Applications&quot;"
date: 2018-09-22
forum: General Help
---

### Post by pastor-t on 2018-09-22
I had Riseup-VPN installed for a while, but when I uninstalled it, it was still showing up in the "Show Applications" window of the desktop.
I've searched for hours to find it in the deepest, darkest recesses of the disk hierarchy for it, and found nothing.
I even tried re-installing the application and uninstalling it again, in hopes that some obscure bit may have flipped somewhere... nothing.
I know I can't possibly be the only one that's ever had this issue... I'm just not that interesting.
Someone please help, before I lose my mind.

System:
OS: Ubuntu 18.04.1 LTS (64 bit)
MEM: 3.4 GB
CPU: Intel Pentium D @ 2.80GHz x2
VIDEO: Intel 945 G
GNOME: 3.28.2

---

### Post by monkeybrain20122 on 2018-09-22
Probably it installed a .desktop file in ~/.local/share/applications. Just open the file manager, choose show hidden files or press ctrl+H, open .local/share/applications (note the . in front, which is a hidden folder) See if you can find the .desktop file (launcher icon) in there, if so just delete it.

---

### Post by pastor-t on 2018-09-22
Nope... that folder is empty. ( I keep hidden stuff showing, always)

---

### Post by mc4man on 2018-09-22
How did you install it?

---

### Post by pastor-t on 2018-09-22
Through the usual "Ubuntu Software" application.

---

### Post by again? on 2018-09-22
riseup-vpn is a snap package which installs a desktop launcher to /var/lib/snapd/desktop/applications/
which remains after removing riseup-vpn and shows up in the applications overview without an icon.

Remove the launcher.
(for safety the -i flag is used so you will need to confirm with "y" before removal)
```
sudo rm -i /var/lib/snapd/desktop/applications/riseup-vpn_riseup-vpn.desktop
```

---

### Post by pastor-t on 2018-09-23
Close, but not quite ...  finally figured it out this morning.
Apparently, there was still part of the application running in the background, which for some reason, caused some of the remaining parts to be invisible to the file system, regardless of view mode (including the .desktop file you mentioned).

So, for anyone else that has this issue in the future, follow these steps to make it completely go away...

sudo bitmaskd stop # the culprit
cd /var/lib/snapd/desktop/applications
sudo chmod 777 riseup-vpn_riseup-vpn.desktop
sudo rm riseup-vpn.desktop
cd /var/lib/snapd/sequence
sudo chmod 777 riseup-vpn.json
sudo rm riseup-vpn.json
cd $HOME/.cache/gnome-software/screenshots/752x423
rm d6c6a3042bc652328a3c391334a5a327ed79a360da6042f2465ad49333d4e111-riseupvpn-screenshot.png
cd ../112x63
rm d6c6a3042bc652328a3c391334a5a327ed79a360da6042f2465ad49333d4e111-riseupvpn-screenshot.png
cd $HOME/.config/providers
rm -R riseup.net

---

### Post by again? on 2018-09-23
Not a full bottle on snaps and know nothing about bitmask but I did test the installation and removal of riseup-vpn on an up to date
Ubuntu 18.04 install.

/var/lib/snapd/desktop/applications/riseup-vpn_riseup-vpn.desktop wasn't hidden 
Where does bitmaskd come from?
(Ran while riseup-vpn installed and after removal)
```
**[COLOR="#006400"]glen@Gubu:~$[/COLOR] sudo bitmaskd stop**
[sudo] password for glen:         
sudo: bitmaskd: command not found
```

---

### Post by pastor-t on 2018-09-24
Riseup-VPN is based on Bitmask, so likely it was installed either WITH Riseup, or came in afterwards on an update to Riseup.

---

