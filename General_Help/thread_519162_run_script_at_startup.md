---
title: "run script at startup"
date: 2007-08-06
forum: General Help
---

### Post by walshie616 on 2007-08-06
Hello,

I need to run this script at startup: 

&#65279;sudo ifconfig ra0 down
sudo ifconfig ra0 up
sudo iwconfig ra0 essid linksys
sudo iwconfig ra0 key off
sudo dhclient ra0

This makes my wireless card work.

I have done some research and have found that i need to put a script in this directory:

I have had two problems, I am unsure how to make a 'script' file and I am unable to add/change/remove anything in /etc/init.d/ because I do not have permission?

Thanks for any help!

---

### Post by clum on 2007-08-06
Though it may be useful to learn how to run scripts at start-up, I don't think that would be the appropriate solution in this case, because there is already a script which takes care of setting up networks. Instead, edit /etc/network/interfaces, by entering the command 
sudo gedit /etc/network/interfaces
in a terminal. Add the following lines to the file:
auto ra0
iface ra0 inet dhcp
wireless-essid lynksis

---

### Post by walshie616 on 2007-08-06
Thank you very much!!! :guitar::KS:popcorn:

---

