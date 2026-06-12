---
title: "Ubuntu hangs on boot after trying to upgrade for Skype"
date: 2014-08-20
forum: General Help
---

### Post by wynne3 on 2014-08-20
Hi,

I have been running Ubuntu 12.04 64bit on a ThinkPad Edge E525 for a couple of years without any major problems.

I recently tried to upgrade a few packages to stop Skype crashing, this has resulted in Ubuntu hanging on boot, the screen goes purple, then the ubuntu logo appears, then the following text appears:
"Checking battery state [ OK ], then it hangs.

I can enter the shell using ctrl+alt+f1 and get to my .bash_history file. The fatal commands were:

mv .Skype .Skype.old
sudo apt-get install libqt4-dbus:i386 libqt4-network:i386 libqt4-xml:i386 libqtcore4:i386 libqtgui:i386 libqttwebkit4:i386 sni-qt:i386
sudo apt-get install libqt4-dbus:i386 libqt4-network:i386  libqt4-xml:i386 libqtcore4:i386 libqtgui:i386 libqttwebkit4:i386  sni-qt:i386 libgstreamer-plugins-base0.10-0:i386
sudo apt-get install libqt4-dbus:i386 libqt4-network:i386  libqt4-xml:i386 libqtcore4:i386 libqtgui:i386 libqttwebkit4:i386  sni-qt:i386 libgstreamer-plugins-base0.10-0:i386 libsqlite3-0:i386
sudo apt-get install skype
sudo apt-add-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"
sudo apt-get update && sudo apt-get install skype

I cannot connect to the internet via wireless or cable.
The output of ifconfig is:

lo           Link encap:Local Loopback
              inet addr:127.0.01 Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host 
              UP LOOPBACK RUNNING MTU:16436 Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 frame:0
              collisions:0 txqueuelen:0
              RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

Also when I connect an external hardrive (I wanted to copy all my files off and just start again) , the output has the form:

[ 89.1 ??????] sd 3:0:0:0 [sdb] No caching mode page found
[ 89.1 ??????] sd 3:0:0:0 [sdb] Assuming drive cache: write through
[ 89.1 ??????] sd 3:0:0:0 [sdb] No caching mode page found
[ 89.1 ??????] sd 3:0:0:0 [sdb] Assuming drive cache: write through
[ 89.1 ??????] sd 3:0:0:0 [sdb] No caching mode page found
[ 89.1 ??????] sd 3:0:0:0 [sdb] Assuming drive cache: write through


I'm up **** creek, any help would be appreciated.

---

