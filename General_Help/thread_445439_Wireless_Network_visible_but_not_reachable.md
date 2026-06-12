---
title: "Wireless Network visible but not reachable"
date: 2007-05-15
forum: General Help
---

### Post by winit_gal on 2007-05-15
[Again, I’ve just installed Ubuntu for the first time, so I’m still a novice, but I like to think I catch on quickly.]

When roaming is enabled I pick up my network [Samedi] and it prompts me for my WEP key [which I input]. Connectivity is shown, but then nothing will load.

I searched the forums for other people who had this problem –there were a few- but I’m not sure that my situation is the same.
Here are the results of ifconfig and iwconfig [which all other troubleshooting posts asked for, so I thought I’d check out]
[http://i41.photobucket.com/albums/e260/BugJar/nw1.jpg](http://i41.photobucket.com/albums/e260/BugJar/nw1.jpg)
[http://i41.photobucket.com/albums/e260/BugJar/nw2.jpg](http://i41.photobucket.com/albums/e260/BugJar/nw2.jpg)
[http://i41.photobucket.com/albums/e260/BugJar/nw3.jpg](http://i41.photobucket.com/albums/e260/BugJar/nw3.jpg)

It looks like nothing’s wrong? So why is it when I type URLs in Firefox it tells me it’s unable to connect?

Thanks for your help (again ^_^;)!

---

### Post by goandeatsomestuff on 2007-05-16
Make sure you are connected and have a valid IP, like you do in the screenshots.  Try putting this IP into firefox:
72.14.207.99
If you get the normal google homepage, then do this in a terminal:

sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.backup
sudo gedit /etc/dhcp3/dhclient.conf

This should open up dhclient.conf in a graphical text editor after you put your password in.  It should be a file full of commented lines.  This file controls domain name resolution, which your computer is having a problem doing.  The first command creates a backup file called dhclient.backup, which lets you back up in case a fatal error is made in the future editing process.  What the second command above does is open this file for editing using gedit.  The sudo prefixes open the file as the root user (super user), which has permission to do anything and is necessary to make changes to system files.  

Now, in the open dhclient.conf, find this line, which will be commented out by having "#" in the beginning:
#prepend domain-name-servers xxx.xx.xxx.xxx;
You need to uncomment this line and insert a DNS server, which will fix your problem.  You can use openDNS, which is a free DNS reolution service online, by replacing the string with these TWO strings:
prepend domain-name-servers 208.67.222.222;
prepend domain-name-servers 208.67.220.220;
Be sure that there is no leading "#", save the file, and restart your computer.  Once you are restarted, you should be good to go! Good luck!

---

