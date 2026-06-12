---
title: "Where is Azureus?"
date: 2006-12-31
forum: General Help
---

### Post by OsakaWilson on 2006-12-31
I want to tell Firefox to make Azureus the default for opening .torrent files. 

I know I have to answer "What should Firefox do with this file?" to "Open with Azureus" by selecting "Other..." and browsing for Azureus.

But where is Azureus? I can't find it anywhere.

---

### Post by Hardi on 2006-12-31
Open up a terminal and type "whereis azureus" and "locate azureus" (without quotes)- I hope one of them will help you.

---

### Post by OsakaWilson on 2006-12-31
Thanks for the reply. I did a whereis and got this.

desktop:~$ whereis azureus
azureus:
desktop:~$ 

Then I did a locate and got what's below this. Any idea which one is the application? Sorry to be so clueless.

I tried '/usr/share/applications/azureus.desktop' but that doesn't see to work.

desktop:~$ locate azureus
/var/lib/dpkg/info/azureus.list
/var/lib/dpkg/info/azureus.postrm
/home/wilson/.local/share/applications/azureus-usercustom.desktop
/home/wilson/.local/share/applications/azureus-usercustom-1.desktop
/home/wilson/.azureus
/home/wilson/.azureus/plugins
/home/wilson/.azureus/plugins/azplugins
/home/wilson/.azureus/plugins/bdcc
/home/wilson/.azureus/.lock
/home/wilson/.azureus/.keystore
/home/wilson/.azureus/logs
/home/wilson/.azureus/logs/save
/home/wilson/.azureus/azureus.config
/home/wilson/.azureus/.certs
/home/wilson/.azureus/azureus.config.bak
/home/wilson/.azureus/tmp
/home/wilson/.azureus/shares
/home/wilson/.azureus/torrents
/home/wilson/.azureus/torrents/ubuntu-ja-6.10-desktop-i386.iso.torrent
(2006.HDTV.AC3_SoS).torrent
/home/wilson/.azureus/torrents/[SoS].+[_]+ 
home/wilson/.azureus/torrents/[SoS].^_^_ 
/home/wilson/.azureus/torrents/ubuntu-6.10-desktop-i386.iso.torrent
/home/wilson/.azureus/torrents/ubuntu-6.10-desktop-amd64.iso.torrent
/home/wilson/.azureus/dht
/home/wilson/.azureus/dht/addresses.dat
/home/wilson/.azureus/dht/version.dat
/home/wilson/.azureus/dht/contacts.dat
/home/wilson/.azureus/dht/diverse.dat
/home/wilson/.azureus/azureus.statistics
/home/wilson/.azureus/tracker.config
/home/wilson/.azureus/tracker.config.bak
/home/wilson/.azureus/downloads.config.bak
/home/wilson/.azureus/active
/home/wilson/.azureus/downloads.config
/home/wilson/.azureus/ipfilter.cache
/home/wilson/.azureus/filters.config
/home/wilson/.azureus/banips.config
/home/wilson/.azureus/banips.config.bak
/home/wilson/.azureus/azureus.statistics.bak
/opt/azureus
/opt/azureus/azureus
/opt/azureus/Azureus.png
/opt/azureus/Azureus.torrent.png
/opt/azureus/Azureus2.jar
/opt/azureus/ChangeLog.txt
/opt/azureus/License.txt
/opt/azureus/plugins
/opt/azureus/plugins/azplugins
/opt/azureus/plugins/azplugins/azplugins_2.1.1.jar
/opt/azureus/plugins/azrating
/opt/azureus/plugins/azrating/azrating_1.3.1.jar
/opt/azureus/plugins/azupdater
/opt/azureus/plugins/azupdater/azupdaterpatcher_1.8.3.jar
/opt/azureus/plugins/azupdater/plugin.properties
/opt/azureus/plugins/azupdater/Updater.jar
/opt/azureus/README.txt
/opt/azureus/swt-about.html
/opt/azureus/swt.jar
/opt/azureus/libswt-atk-gtk-3232.so
/opt/azureus/libswt-awt-gtk-3232.so
/opt/azureus/libswt-cairo-gtk-3232.so
/opt/azureus/libswt-glx-gtk-3232.so
/opt/azureus/libswt-gnome-gtk-3232.so
/opt/azureus/libswt-gtk-3232.so
/opt/azureus/libswt-mozilla-gcc3-gtk-3232.so
/opt/azureus/libswt-pi-gtk-3232.so
/usr/share/app-install/desktop/azureus.desktop
/usr/share/applications/azureus.desktop
/usr/share/automatix2/conf/azureus.desktop
wilson@wilson-desktop:~$

---

### Post by aidanr on 2006-12-31
/opt/azureus/azureus

---

### Post by OsakaWilson on 2006-12-31
I set /opt/azureus/azureus as the default, but still nothing happens. Is it possible that this feature is not working in Azureus? Hmmm.

---

### Post by taurus on 2006-12-31
Have you tried to run it from a terminal with

```
/opt/azureus/azureus
```

And you have java installed, right???

---

### Post by OsakaWilson on 2007-01-01
I can run Azureus from the Applications list. It runs fine. What I'm trying to do is make it the default for opening .torrent files that I download with Firefox. 

Maybe this feature just doesn't function in Firefox.

---

### Post by taurus on 2007-01-01
When you click a torrent link in firefox, it will ask you which app you want it to open.  Browse until you find azureus and tell it use azureus as a default app for it.

---

### Post by gun on 2007-01-01
Start the terminal program immediately after you login. It should start then. 

1) 
How much memory your box has? Report
$ cat /proc/meminfo 

What about disk space? Report 
$ df -h 

Report also mounted partitions (interested to know where's /home and /tmp if they have own partitions)
$ mount
------------------------------------------------------------

2) The programs that do not start, are they "sudo" (super user) programs or just ordninary ones ?
 
[www.unreadedpost.com]("www.unreadedpost.com")

3) Create a new user and login with that. Can you see the same problem then?

---

### Post by OsakaWilson on 2007-01-01
Taurus,
Thanks for sticking around and helping me. I think I'm not explaining well. 

I have successfully done everything you suggested in your last post except find Azureus when I browse for it. 

My question is: where is it? I don't know the path that I need to follow to find it.

---

### Post by taurus on 2007-01-01
It should be in /opt/azureus/azureus.  So browse to /, then to opt (/opt), then to azureus (/opt/azureus), and highlight azureus (/opt/azureus/azureus).  That should do it.

---

### Post by OsakaWilson on 2007-01-05
Thanks for the help. I followed the path, but after all, nothing happens. It just downloads the torrent as if I had selected "Save to disk".

Is this working for anyone else?

---

### Post by aidanr on 2007-01-05
you can try this, i haven't tried it because it work for me by just setting it in firefox

```
sudo gedit /etc/mailcap
```

add the following to the end of the file

```
application/x-bittorrent; /opt/azureus/azureus "%s"
```

from [here]("http://www.azureuswiki.com/index.php/Open_torrents_from_web_browser_in_Linux")

---

### Post by sefk26 on 2007-01-05
file:///usr/bin/azureus

---

### Post by olejorgen on 2007-01-05
> **OsakaWilson said:**
> I can run Azureus from the Applications list. It runs fine. What I'm trying to do is make it the default for opening .torrent files that I download with Firefox. 

Maybe this feature just doesn't function in Firefox.

If you can run it from the menu you can use alacarte to check where it's located. (If it's in path it will most likely not be a full path, but in this case "whereis" / "which" should give you the path.)

I'm not on linux now so I can't give exact instructions.

---

