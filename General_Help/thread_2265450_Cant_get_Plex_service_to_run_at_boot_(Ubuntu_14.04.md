---
title: "Cant get Plex service to run at boot (Ubuntu 14.04 64bit)"
date: 2015-02-15
forum: General Help
---

### Post by ssott on 2015-02-15
Hi All,
  Im not sure if this is a Plex or Ubuntu issue but the Plex service simply will not start on boot, however it starts fine if i manually run  it using service plexmediaserver start right after, prior to this its in  stop/waiting state.  
  sudo /usr/sbin/start_pms shows no issue, i cant see anything in the  logs in relation to why this is happening, /var/lib/plexmediaserver is  owned by plex : plex

  
 Package: plexmediaserver
Status: install ok installed
Priority: extra
Section: video
Installed-Size: 242656
Maintainer: Tobias Hieta <tobias@hieta.se>
Architecture: amd64
Version: 0.9.11.4.739-a4e710f
Depends: avahi-daemon, avahi-utils
Conffiles:
 /etc/default/plexmediaserver 9f9e2b0cc1986d114fec86f39235f459
 /etc/init/plexmediaserver.conf 64d6777eaaa21709298bd53b9d5d78aa
 /etc/apt/sources.list.d/plexmediaserver.list 248977a7d9b39b47e0e0a0017e8f203b
Description: Plex organizes all of your personal media so you can easily access and enjoy it.
Homepage: [https://plex.tv](https://plex.tv)
 
 sudo sysv-rc-conf --list plexmediaserver
plexmediaser 2: on       3: on    4: on    5: on
 

 Any ideas?

---

### Post by mooreted on 2015-02-15
Looking around it could be a lot of things. I have not had any problems on my 14.04 x64 system. It might be best to ask in the Plex forums. 

Check dmesg and your system logs for Plex errors. You could have a drive that is full or not mounted fast enough, a corrupted settings xml, a file that doesn't want to load. 

Until you can narrow it down, it's hard to say what the problem is.

---

