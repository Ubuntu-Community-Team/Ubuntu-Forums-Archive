---
title: "HELP - How do I copy files from XP laptop to my Ubuntu system via home network?"
date: 2006-08-20
forum: General Help
---

### Post by MJSOnline on 2006-08-20
Hi.  How do I copy files from my XP laptop to my Ubuntu system via home network? I am very new to all the home networking thing so be gentle. Thanks. M

---

### Post by noof on 2006-08-20
Is it XP Home or Pro? If it's Pro you can share the folder containing the files and then in gnome go to "Places->Network servers", choose "Windows Network", click the icon that comes up and then you should see the name of the XP-computer.

If it's Home-edition (or as an alternative way of doing it in pro) I think you can do it by making sure you have a windows account that belongs to the administrator group (Start->Run "compmgmt.msc" Local users and groups->Users, double-click the user and go to "Member of" and add the administrator group if it isn't there) and have a non-blank password (important). Then in nautilus you can press ctrl+L and enter "smb://nameofyourlaptop/c$" and enter your username/password.

---

### Post by MJSOnline on 2006-08-20
It is Pro.  I did as you said, for pro, but no luck.  Do I need other packages installed? M

---

### Post by Irony on 2006-08-20
A windows shared folder should show up automatically in Ubuntu in Places > Network Servers.

If it doesn't make sure you Laptop firewall is configured to accept Home Networking. For example in Norton go to Firewall and select auto-configure for home network. In Zone Alarm you may have to add allowable IPs. Do a Google for the particular firewall.

---

### Post by hollaburoo on 2006-08-20
If all else fails try going to Places --> Connect to Server, choose Windows Share as the server type and give the windows computer's ip address as the server.  Just make sure that the windows pc has a static ip address if you do this.  You can set up a static ip address with instructions from [here.]("http://www.portforward.com/networking/static-xp.htm")

---

