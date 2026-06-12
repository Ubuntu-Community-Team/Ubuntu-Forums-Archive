---
title: "Bittorent confusion"
date: 2007-01-31
forum: General Help
---

### Post by Mazehero55 on 2007-01-31
I downloaded the original bittorrent deb at bittorrent.com, but it won't install because of the bittorrent already installed. So I try to remove it but to remove it it must remove ubuntu-desktop too.

What's going on, how can I install this.

thank you

---

### Post by FluffyElmo on 2007-01-31
If it's a version conflict, you may be able to force the package to install. I'm assuming that the problem is the Ubuntu version numbering is different from the original. Try install installing the deb from a terminal to see what error it gives and then you can force that option. By forcing it to install you're telling dpkg to ignore errors and proceed anyways so you should be sure what the specific problem is...

First try installing from the terminal to see what the error is:
```
sudo dpkg -i packagename.deb
```

You can force it to install by adding a force option to the command, this command will try to force everything:
```
sudo dpkg --force-all -i packagename.deb
```

If you want to be more specific you can list the available force options with this command and then just override specific errors.
```
dpkg --force-help
```

---

### Post by Andy_D on 2007-01-31
Have you tried installing the package bittorrent-gui (and bittorrent) from the repos? The version that comes with Ubuntu is the gnome bittorrent downloader which is a simplified version of the classic bittorrent as far as I can gather. I believe bittorrent-gui might be what you are after, remember to set it as the default application for .torrent files or the gnome bittorrent downloader (gnome-btdownload) will automatically try and handle torrents.

Hope that helps.

---

### Post by jfca283 on 2007-01-31
use azureus
just verify that you have java in your system
it's the best bittorrent client

---

### Post by balaoko on 2007-02-04
Thanks a lot. just intalled it. It asked a TCP port tested, but it is difficult to get the test passed. Any suggestions for it? Thanks again

> **jfca283 said:**
> use azureus
just verify that you have java in your system
it's the best bittorrent client

---

### Post by zekopeko on 2007-02-04
try installing firestarter from the repos. 

open firestarter (GUI for the firewall) and in it open the port(or range of ports) and that's it.

---

### Post by balaoko on 2007-02-08
Thanks. I tried it and it sounds like my laptop can't do it b/c I am using a public wireless network. So I am using ktorrent instead. Anyway, Thanks for giving me the solution.

> **zekopeko said:**
> try installing firestarter from the repos. 

open firestarter (GUI for the firewall) and in it open the port(or range of ports) and that's it.

---

