---
title: "Newbie: Screen Resolution and Flash Player"
date: 2006-11-27
forum: General Help
---

### Post by corl30ne on 2006-11-27
Hello everyone,

I'm Corl30ne and I'm just starting to play with Ubuntu.
So far, let me tell you folks who contibuted and still contribute for it: I'm impressed ;)

So let's go straight to the issue.
I installed and configured Ubuntu (don't have any problems so far). But now I want to increase the screen resolution and apparently I cannot. I have a Samsung SyncMaster 710N, having it on 1024*768 is blurry even in Windows.

Anyone had this problem before? When I try to change it, the only options I get are 640,800 and of course 1024. I'm looking for 1280.

As for the Macromedia Flash Player, I am running off a AMD64, so I bet you guys know what the issue is! Anyone using this that got it working? I installed EasyUbuntu and that seem to have worked for me installing the Win32 codecs etc. Unfortunately the developers didn't put this option yet. (Great work they done there by the way!)

To the mods and regular users: If I posted in the wrong place, let me know. 
It's the very first time I post on this board.

Thanks for reading this and for any tips you might have!

---

### Post by corl30ne on 2006-11-27
I've fixed the videocard issue.
For those looking for the solution... in my particular issue it was a matter of adding the refresh rates of my monitor to the xorg.conf file, and off course adding the resolution to the config file as well.

Looks great now. Even more smooth then windows :mrgreen:

I'm hunting the solution for Macromedia Flash now.

---

### Post by PrinceArithon on 2006-11-27
Flash is pretty easy actually.

For the plug in you want to do this.

sudo apt-get install flashplugin-nonfree
sudo update-flashplugin

IF for some reason you get an error try this installation

sudo apt-get install libflash-mozplugin
sudo update-flashplugin

After this restart Mozilla.

Now you need to update the flashplayer, so put this into your command line.

wget [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz)
tar xvzf FP9_plugin_beta_112006.tar.gz
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/flashplugin-nonfree/ 


This should work with getting flash to work for you.

---

