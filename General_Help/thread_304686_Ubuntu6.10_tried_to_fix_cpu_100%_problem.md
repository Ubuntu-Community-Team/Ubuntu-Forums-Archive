---
title: "Ubuntu6.10 tried to fix cpu 100% problem"
date: 2006-11-22
forum: General Help
---

### Post by phstpok on 2006-11-22
I found a thread in known bugs and workarounds [http://ubuntuforums.org/showpost.php?p=1747864&postcount=53](http://ubuntuforums.org/showpost.php?p=1747864&postcount=53) pointing to [http://people.ubuntu.com/%7Eseb128/debug/54684/](http://people.ubuntu.com/%7Eseb128/debug/54684/) so I dl libgnomevfs2-common_2.16.1-0ubuntu3_all.deb for a start. Installed it, but error msg about broken dependencies and to "apt-get install check" which then told me to "apt-get -f install". This proceeded to un-install half my system. I had done a clean install of edgy, so I presumed it wasn't taking me back to dapper, but knew what it was doing. It removed most apps I had installed after the os, including automatix2, gnome-games, but also apps installed with edgy, including gnome-terminal, lots of python, lots of libgnome stuff like ui & vfs. It is still running, but afraid a reboot will finish it.

I have backed up my user data (most of my /home directory, which is on a different partition anyway)

I have tried re-installing some apps, but too many broken dependencies. I am going to boot from the cd and re-install from scratch. Just thought to post this if anyone else tries that cpu 100% bug workaround. Don't do it.

I only started getting the cpu bug after installing drapes (wallpaper changer). Removing it made no difference.

---

### Post by phstpok on 2006-11-23
I have wiped and re-installed edgy, keeping my /home partition and formatting the rest. I haven't had anything chewing up the cpu to 100% yet. The only problem I've had was a complete freeze after leaving the system running in screensaver for 2 hours. The only way I could get out was a power cycle. alt-ctrl-backspace & alt-ctrl-del did nothing. 

Other than that, I have re-installed all apps from the previous installation and it's running well. I found an alternative to drapes, wallpapoz, which works well with better functionality (different random wallpaper on each desktop). It also doesn't use mono, which ran the cpu up to 100% when drapes was running. I don't know whether this is a problem with mono running in edgy, or the way drapes utilizes mono. Haven't had time yet to do a bug search on mono.

---

### Post by andrewski on 2006-11-25
> **phstpok said:**
> I found a thread in known bugs and workarounds [http://ubuntuforums.org/showpost.php?p=1747864&postcount=53](http://ubuntuforums.org/showpost.php?p=1747864&postcount=53)
I hope you also posted there; people subscribed to the thread would probably want to know.
> **phstpok said:**
> "apt-get -f install". This proceeded to un-install half my system. I had done a clean install of edgy, so I presumed it wasn't taking me back to dapper, but knew what it was doing. It removed most apps I had installed after the os, including automatix2, gnome-games, but also apps installed with edgy, including gnome-terminal, lots of python, lots of libgnome stuff like ui & vfs. It is still running, but afraid a reboot will finish it.
Sounds like you introduced an unrecognized package into your system. I'm assuming this libgnomevfs package replaced the stock Edgy one, so all the programs that need it (a lot, indirectly) suddenly cannot be installed.

Best bet probably would've been to "apt-get install libgnomevfs" to get the Edgy one back.

Does Seb know about this potential problem?

---

