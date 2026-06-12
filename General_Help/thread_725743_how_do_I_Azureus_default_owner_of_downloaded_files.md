---
title: "how do I Azureus default owner of downloaded files."
date: 2008-03-16
forum: General Help
---

### Post by mchamberlain on 2008-03-16
I have a headless system setup running Azureus and I use azsmrc to login and upload torrents. All that work great. I then share my downloads folder with samba so i can access my downloaded files across the network from my win machines. Also works fine. The problem is that Azureus by default makes the owner of the downloaded files root and i need to be able to change the default owner so that i have permission to access them through samba. as of now i have to log in via ssh and chown the files manually to get at them. if there is not a direct fix does anyone know a work around that might be handy? ty in advance

---

### Post by cozmicharlie on 2008-03-18
I have Azureus installed to my /opt folder and I am the owner.  I believe if you install Azureus as user instead of root it should make the downloaded files owned by user.  I use Azsmrc also to network in to Azureus and share via ssh and samba and I have no problem.  

I hope this helps

---

### Post by mchamberlain on 2008-03-19
Well that makes sense. do you know if I can just change the ownership somehow? did you install the azureus from the there web site or with apt? I used apt bu i was logged in as root and didn't use sudo. Thanks for the thoughts already though i didn't think of that.

---

### Post by cozmicharlie on 2008-03-19
OK- since you were logged in as root it installed it as root.  You can change permissions using command line or just right click and go to properties>permissions (you need to open nautilus as root to do this - $sudo nautilus) and change the ownership to user (your user name).  

I did not install from synaptic or using apt-get.  I either installed from the source or I used getdeb.net (can't remember which).  There are a couple How To's in the forums - just search for Azureus and you should be able to find them.  If you decide to uninstall Azureus and re-install - make sure to delete the /home/.azurues folder also.  When you re-install, a new folder will be created.

---

### Post by mchamberlain on 2008-03-19
Alright then thanks for all your help.

---

