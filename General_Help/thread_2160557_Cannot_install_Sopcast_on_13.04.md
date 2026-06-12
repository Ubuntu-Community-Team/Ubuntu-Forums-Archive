---
title: "Cannot install Sopcast on 13.04"
date: 2013-07-07
forum: General Help
---

### Post by che47audio on 2013-07-07
Hi there,

Probably a simple fix but with my limited knowledge I'm struggling with this. I've followed the instructions on from the below link and all is good until I get to the installation command. When I try to install sopcast from the terminanl I get the following :
```
chris@kestrel:~$ sudo dpkg -i sopcast-player_0.8.5~ppa~precise1_*.debSelecting previously unselected package sopcast-player.
(Reading database ... 304885 files and directories currently installed.)
Unpacking sopcast-player (from sopcast-player_0.8.5~ppa~precise1_amd64.deb) ...
dpkg: dependency problems prevent configuration of sopcast-player:
 sopcast-player depends on sp-auth (>= 3.0.1).


dpkg: error processing sopcast-player (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 sopcast-player



```


The install guide:

[http://linuxg.net/how-to-install-sopcast-0-8-5-on-ubuntu-13-04/](http://linuxg.net/how-to-install-sopcast-0-8-5-on-ubuntu-13-04/)

I see that there is a dependency issue with sp-auth but I have a newer version installed that one. This shouldn't be a problem should it? Or do I somehow need to revert to an earlier version?
Any help would be greatly appreciated.

Thanks

---

### Post by Penguenci on 2013-07-07
[H]("http://ubuntuforums.org/showthread.php?t=1487372")ave you checked this out?

[http://ubuntuforums.org/showthread.php?t=1487372](http://ubuntuforums.org/showthread.php?t=1487372)

---

### Post by gordintoronto on 2013-07-07
Is your Ubuntu 32 bit or 64 bit? In the instructions you mentioned, they include both, but you should only install the appropriate files.

I have sp-auth 3.2.6 and sopcast 0.8.5, installed from the ferramroberto repository (See [http://askubuntu.com/questions/69701/how-to-install-sopcast-player](http://askubuntu.com/questions/69701/how-to-install-sopcast-player)) but it's in Mint 13, which equates to Ubuntu 12.04. I may have also changed the default channel guide to [http://www.sopcast.cn/gchlxml](http://www.sopcast.cn/gchlxml)

The instructions you referred to showed how to download from a repository which doesn't match your version. 

You might also need to install multiarch-support.

The H264 channels work for me, maybe some others. My wife is Chinese, and I put festival extravaganzas on our big screen from my laptop.

---

