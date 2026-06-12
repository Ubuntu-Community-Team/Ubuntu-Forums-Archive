---
title: "Make the most stable Ubuntu for your office. Newbies only!"
date: 2008-06-08
forum: General Help
---

### Post by heatblazer on 2008-06-08
I`ll give you few hints about making the most stable ubuntu needed in your office`s desktops. I am administrating ubuntu machines so I have some expirience. 
 1. I recommend you to install ubuntu 7.04+

 2. Set your networking: ubuntu 7.04 detects automatically your switch/router via the DHCP. If you have direct IP, set it from the networking manager (the tray icon is up and right). If you need to change the MAC (usually your net provider filters your MAC address and if you change your LAN card, you won`t be able to enter the [www.)](www.))

sudo ifconfig eth0 hw ether 11:22:33:44:55:66

If you want this to be executed automatically when the system boots type:

sudo gedit /etc/rc.local 

enter the MAC changing command in the empty line before "exit 0" 

 3. Now that you have the net, make sure to isntall all of your updates. 
 a) Enter System >>> Administration >>> Softwares Sources. Test for the best server for your country. The next step is to enter the UPDATES tab. Remove the V-tick from Pre-Released and Unsupported updates.
 b) Close Software Sources, it will ask to reload the data base. After a few seconds the Update tray icon will appear in the upper corner. Make sure to update to the maximum :) (this is not Windows, here the updates are UP to DATE)

 4. Get your useful software! Here is what I am using from the begginig of my ubuntu expirience.
 a) Get NTFS configuration tool. It`s easy to find in synaptic
 b) Get Mountpy. It`s an automatic mounting app. It is still useful
 c) If you have a weak PC machine (P3 with 256RAM for example) make sure you get xfce-desktop and xfce, but I recommend to do a clean xubuntu install.
 d) Install Open SSH server!!! Very important for administration!!! I`ll set ***-stars priority as soon as you have a working network connection!
 f) Get mozilla thunderbird if you are not familliar with the Evolution mail
 g) Get WINE! This is very usefull app. Follow the steps in [www.winehq.org](www.winehq.org)
 e) If you are doing this for the office, make sure to set 2-3 profiles without SUDO rights. Have only one admin profile.
 h) If you are using GNOME, I seriously recommend you to go with gnome`s apps. Don`t mess it with KDE. It`s not dangerous but it makes the machines work slower. Use Gnome with Gnome and KDE with KDE.
 i) Get aMule and Azureus torrent client. For downloading manager, personally I use Mozilla`s "Save As", or install DownThemAll! (mozilla plugin)
 j) Use TOTEM! It is one of the best players I`ve ever seen. It plays almost very type of media and it`s good choice for mozilla plugin. For music I really recommend Rythmbox. This is a great music manager with a lot of options. Works great with GNOME and is consideraby - fast. If you have KDE - you can use Amarok.
 k) For office apps I use the standart ubuntu packed: OpenOffice and GIMP. They are more than enough for your office.

 That`s from me. Hope that was helpful for the newbies. Enjoy your ubuntu anywhere!

---

