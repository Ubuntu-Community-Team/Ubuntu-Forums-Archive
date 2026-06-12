---
title: "unable to view router share on home network"
date: 2018-01-26
forum: General Help
---

### Post by mb195811 on 2018-01-26
I am unable to view the shared drive attached to my home router.  This is my first experience with Linux.  I am running Lubuntu 16.04 (old hardware) and I am not sure how to set up the network to view the share.  The computer is hard wired to the router.  I am connected to the internet and able to use my browser and email clients, but unable to view the router.  Any assistance would be appreciated.

Mark

---

### Post by Holger_Gehrke on 2018-01-26
How to do it depends on the way the router offers the share on the network. My old router had an ftp-server that gave access to connected USB storage devices, the new one offers them by smb/cifs (this is what windows uses for shared folders). If the router uses smb, you can just select "Network" from the sidebar in "Places"-mode in the filemanager. The router should show up there, but it might also "hide" in a workgroup. If the router uses ftp, just type "ftp://" and the IP-Address of the router into the address bar of the filemanager. If you don't know the IP-address of the router, click on the network connection icon on the taskbar and select "Connection Information" from the popup menu. The address given as "Default Route" should be your router.

Holger

---

### Post by mb195811 on 2018-01-29
I tried using filemanager to access the router, and it shows a Windows network but cannot retrieve the list of files.  I an not sure smb is installed.  I also connect to the router with windows and a Mac.  should I install smb?  I have read to use NFS instead.  my only goal is to connect to the share on the router.

---

