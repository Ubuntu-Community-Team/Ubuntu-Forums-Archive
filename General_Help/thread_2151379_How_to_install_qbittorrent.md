---
title: "How to install qbittorrent"
date: 2013-06-04
forum: General Help
---

### Post by lumaja on 2013-06-04
After been working faultless since January 2013 in Ubuntu 12.04 precise i-386, open the application
 from Dash on searching for another download I don’t know what I press qbittorrent disappear from the  
 screen and never could be restart again, with Synaptic I uninstall it restart Ubuntu and from
 Synaptic i install qbittrorrent ver: 3.0x-4285-20130523-precise1.
 But again can not start from Dash.
 Searching for qbittorrent [SIZE=3]version to install I found this one:[/SIZE]
 
[http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu)  I had it to repository to find if it works.
 I need help how to install it.
 Any information if this the proper qbitttorrent it will help too.

 Thank you

---

### Post by gordintoronto on 2013-06-04
It sounds like it is installed. What happens when you try to run it from the command line?

---

### Post by lumaja on 2013-06-05
[SIZE=3]Open Dash qbittorrent wasn’t there, following you instruction result:[/SIZE]
 

 @-G41M-Combo:~$ qbittorrent  
 The program 'qbittorrent' is currently not installed.  You can install it by typing:  
 sudo apt-get install qbittorrent  
 @-G41M-Combo:~$ sudo apt-get install qbittorrent  
 [sudo] password for luis:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following packages were automatically installed and are no longer required:  
   ttf-umefont libtext-glob-perl libcapi20-3 libboost-thread1.46.1  
   libpam-winbind libfile-find-rule-perl libmpg123-0 winbind ttf-unfonts-core  
   libnumber-compare-perl ttf-droid  
 Use 'apt-get autoremove' to remove them.  
 Suggested packages:  
   qbittorrent-dbg  
 The following NEW packages will be installed:  
   qbittorrent  
 0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.  
 Need to get 0 B/2 844 kB of archives.  
 After this operation, 6 167 kB of additional disk space will be used.  
 Selecting previously unselected package qbittorrent.  
 (Reading database ... 614863 files and directories currently installed.)  
 Unpacking qbittorrent (from .../qbittorrent_3.0.x-0~4285-20130523~precise1_i386.deb) ...  
 Processing triggers for menu ...  
 Processing triggers for bamfdaemon ...  
 Rebuilding /usr/share/applications/bamf.index...  
 Processing triggers for desktop-file-utils ...  
 Processing triggers for gnome-menus ... 
 Processing triggers for man-db ...  
 Processing triggers for hicolor-icon-theme ...  
 Setting up qbittorrent (3.0.x-0~4285-20130523~precise1) ...  
 Processing triggers for menu ...  

 [SIZE=4]@-G41M-Combo:~$  
[/SIZE]
[SIZE=4] [/SIZE][SIZE=4]
[/SIZE]
[SIZE=4] [/SIZE][SIZE=4]Now qbittorrent is in Dash click on it nothing happen, some as before.[/SIZE]

---

### Post by Dhamu on 2013-11-13
qbitorrent client is easy to install on Ubuntu,because it is available in Ubuntu repositories

Installation Procedure

Add Repository : **sudo add-apt-repository ppa:hydr0g3n/qbittorent-stable**

update : **sudo apt-get update**

Install qbitorrent : [B]sudo apt-get install qbitorrent

For More details Visit

[http://dctutors.blogspot.com/2013/10/how-to-install-qbittorrent-311-on.html](http://dctutors.blogspot.com/2013/10/how-to-install-qbittorrent-311-on.html)
[/B]

---

