---
title: "azureus down/up speed just stops!"
date: 2006-11-22
forum: General Help
---

### Post by dr.drake on 2006-11-22
well, I am not the only one with azureus problems since my upgrade to edgy.
first azureus kept shutting down just after it openened, this was a known java-dependent bug, which I fixed with [this thread]("http://www.ubuntuforums.org/showthread.php?t=289564&highlight=azureus").
it ran well for about a week and a half, then it went al haywire on me again. I found the other bug, and "fixed it with [this bug report]("http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus"), making me install it again, the non-repo way.
this time again, the random dissappearance of azureus stopped, but my downloads were really troubled, stopping, failing and loads more.
where azureus usually worked "out of the box", this time I had to really tweak it in the prefs. never before I had to specify different ports, maximum nr of connections and more settings. it always just worked.
anyway, I did as much tweaking as I could, and now it basically works, BUT..

the only problem that I keep having now is that after a while **the down- and up-speeds drop to 0 B/s and it stops downloading!**!!! the status is still set on "downloading" but there is no traffic. it is not that it timed out, because I had torrents running with only 3 minutes left untill completion, and a lot of peers connected. no way they could all just have disconnected at the very same time, but still: BANG! total meltdown, non functional.

it's starting to drive me nuts...

so: PLEASE HELP???!

*edit: in the meantime I've put the same torrents on download with Ktorrent, where the downloads continue when azureus is stopping, so there is probably nothing wrong with my connection.
very noticable is that azureus actualy has really much higher download speeds on the same files... up to 20 times higher.
I'm beginning to think he high number of seeds/peers on those torrents might be the key to the download failure, so I will add a low seed/peer torrent to the list.

---

### Post by tribaal on 2006-12-01
Same problem... I know for a fact that my networking setup is good (exact same setup with windows works), but the torrents just drop dead after a while... :(

- trib'

---

### Post by dr.drake on 2006-12-02
well, I couldn't get it to work properly, so I took the easy way out; I uninstalled and switched to Ktorrent, it eats less CPU as well..

---

### Post by Musashi-san on 2006-12-09
Same problem here, after playing around i've done this:

Uninstall azureus:
apt-get remove azureus azureus-gcj

Download Azureus from sourceforge:
[http://downloads.sourceforge.net/azureus/Azureus_2.5.0.0_linux.tar.bz2?modtime=1156163390&big_mirror=0]("http://downloads.sourceforge.net/azureus/Azureus_2.5.0.0_linux.tar.bz2?modtime=1156163390&big_mirror=0")

The follow the guide (alternative method) from:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29")
```

sudo tar jxvf Azureus_2.5.0.0_linux.tar.bz2 -C /opt/
sudo gedit /usr/share/applications/azureus.desktop

* Add the following to the new file 

[Desktop Entry] 
Name=Azureus
Comment=Java BitTorrent Client
Exec=/opt/azureus/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;

* Save the edited file 

* Applications -> Internet -> Azureus

```

It seems to work fine.

---

### Post by Musashi-san on 2006-12-09
Its seems to be a problem with the Java enviroment:

apt-get install sun-java5-jre sun-java5-plugins

Make sure you have Multiverse on apt source list enabled:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_apt-get_the_easy_way_.28Synaptic.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_apt-get_the_easy_way_.28Synaptic.29")

---

