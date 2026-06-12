---
title: "HOWTO: Install Flash"
date: 2008-03-01
forum: General Help
---

### Post by Aeph on 2008-03-01
Flash doesn't work natively, at least not as of 7.10. Getting it through the Synaptic Package Manager is buggy and Firefox's prompting to install plug-ins doesn't actually do anything really useful. If you want flash, this is how to manually get it:

1. Go to [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz")
Open it with through the archive manager and extract it to your desktop.

2. Double click on the extracted folder and open flashplayer-installer. Run it in the terminal

3. Follow the instructions. Press enter. Close your browser (you may want to glance over the rest of these instructions first if you are new to using Linux). Enter the path of your browser. If it's Firefox, enter /usr/lib/firefox. Press Y when it asks if you want to proceed. Press N when it asks if you want to preform another installation.

That's it. You can delete the folder from your desktop. You now have Flash installed.

---

### Post by gobbles414 on 2008-03-01
Hi all,

I recommend using the following URL, instead of the one that Aeph has provided. Until Adobe is kind enough to provide a .deb formatted installer, you'll want to choose the .tar.gz installer. EDIT: You'll want to choose **/usr/lib/firefox** in the installer -- all small letters and no period before firefox.

[http://www.adobe.com/products/flashplayer/]("http://www.adobe.com/products/flashplayer/")

---

### Post by LuisGMarine on 2008-03-01
Ubuntu has come along quite a way, you don't need all those fancy instructions.  Just go to a website that uses flash, like YouTube, and it will ask you if you want to install the missing plugin.  Hit yes and you have two options, install the regular Flash by Adobe or the one by the open source progject, forgot the name I think its like GSWAF or something.


Saves a lot of new people time.  Thanks for the effort.

---

### Post by gobbles414 on 2008-03-01
LuisGMarine,

It's been awhile since I've tried the automatic method that you mention. But aren't open source Flash players still based on Flash 7 or 8? To fully enjoy the internet, one really needs to have a Flash 9 compliant plugin.

---

