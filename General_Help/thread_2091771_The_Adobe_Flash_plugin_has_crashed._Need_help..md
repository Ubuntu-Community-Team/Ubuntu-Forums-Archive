---
title: "The Adobe Flash plugin has crashed. Need help."
date: 2012-12-06
forum: General Help
---

### Post by agentfortyseven on 2012-12-06
Hey guys,
For some strange reasons my adobe flash plugin keeps crashing.
I don't really have much problem watching Youtube videos, it seldom crashes when im on it. But whenever I try to play videos from any other sites like Facebook, Dailymotion etc.. my plugin keeps crashing.
One way to fix this problem was disabling the hardware acceleration but this reduces the FPS (frames per second) of the videos which is not what I want.
Can you guys please help me fix this problem.

---

### Post by agentfortyseven on 2012-12-06
I never had this problem with Ubuntu 10.04.
Also I tried running the following command but it didn't help.

sudo apt-get --purge remove adobe-flash-properties-gtk adobe-flashplugin libswfdec-0.8-0 swfdec-gnome; sudo dpkg -P flashplugin-installer; sudo apt-get --purge autoremove; sudo apt-get install adobe-flashplugin

---

### Post by agentfortyseven on 2013-02-03
bump

---

### Post by zoldik on 2013-02-03
Hello,
Try to compile it from source code, get the flashplayer.tar.gz from website:
[http://get.adobe.com/en/flashplayer/](http://get.adobe.com/en/flashplayer/)

then copy it to your Desktop.
-change directory:
#cd /home/<user>/Desktop
-Unpack the tar.gz file
# tar xzf install_flash_player_11_linux.x86_64.tar.gz

-Copy libflashplayer to plugin directory:
# cp libflashlayer.so /home/<user>/.mozilla/plugins/

-Copy the Flash Player Local Settings configurations files to the /usr directory. At the prompt type:

# sudo cp –r usr/* /usr

Restart your browser.

---

