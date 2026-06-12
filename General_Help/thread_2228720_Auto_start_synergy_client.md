---
title: "Auto start synergy client"
date: 2014-06-09
forum: General Help
---

### Post by dietwo on 2014-06-09
Hello all

I am a novice linux user and new to Ubuntu. I am trying to set auto-start for synergy client.

At the page [https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto), the setup is done for gdm display manager. This asks to put the following contents in /etc/gdm/Init/Default

My current version of Ubuntu is 14.04.

$  env | grep -i DESKTOP_SESSIONDESKTOP_SESSION=ubuntu
GNOME_DESKTOP_SESSION_ID=this-is-deprecated

I believe my current display manager is lightdm but I am unable to find the desired Default file in that folder. I am willing to start the synergy client before login.

Thanks.

---

