---
title: "Ubuntu as read only on a embedded linux device for in my car.."
date: 2013-05-22
forum: General Help
---

### Post by icepick2000 on 2013-05-22
[LEFT][COLOR=#000000][FONT=Arial]I got my hands on a couple of old Fujitsu-Siemens windows based terminals. I succesfully managed to install ubuntu 11 on the compact flash card thats inside. The system boots fine (ext3) and I have installed scripts on it for my 3G modem, GPS, webcam etc. I made the system without swap (to save the CF card).. and that works fine. My only worry is that eventually the filesystem could get corrupted by the sudden loss of power the system will experience everytime I turn my car engine off. The scripts write all output to /tmp/ramdisk. Is there a way to make the whole filesystem read only? And how would this impact things like /var/log/messages etc? And can I still make changes to the system in the future then?[/FONT][/COLOR][/LEFT]

---

