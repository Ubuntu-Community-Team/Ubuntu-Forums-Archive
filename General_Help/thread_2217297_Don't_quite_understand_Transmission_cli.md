---
title: "Don't quite understand Transmission cli"
date: 2014-04-16
forum: General Help
---

### Post by CaptainMark on 2014-04-16
I've got transmission-daemon running on a server fine and can connect to it using the web ui no problem but I'm struggling to understand the transmission-cli package, I was hoping it would be a way to connect to the daemon and see current torrents via an ssh session but it seems to try to start a new instance of transmission when I run it, same with transmission-remote.

Am I totally missing something? 
Is there a way to get to a cli based version (or a simplified version) of what you see on the web interface??
All the online guides I found seem to assume you already know exactly what your doing already, which I don't obviously.

Regards
Mark

---

### Post by mikewhatever on 2014-04-16
Here is what [transmission-cli]('https://wiki.archlinux.org/index.php/Transmission#Transmission-daemon_and_CLI') does according to Arch wiki.
> 
transmission-remote-cli: (requires transmission-remote-cli) starts the curses interface for the daemon, whether local or remote. 
    transmission-cli: starts a non-daemonized local instance of transmission, for manually downloading a torrent. 
    transmission-show: returns information on a given torrent file. 
    transmission-create: creates a new torrent. 
    transmission-edit: add, delete, or replace a tracker's announce URL.


Looks like transmission-remote-cli might be the way to go.

---

### Post by CaptainMark on 2014-04-16
Thanks this certainly does look like what I need, I will look into this and report back. 

Thanks

---

### Post by mikewhatever on 2014-04-17
You might want to check out rtorrent. It's a cli torrent client with overview, management, remote, an what not.

---

### Post by andrew.46 on 2014-04-21
Another vote here for rtorrent, its configuration file is more than a little mysterious but once all is set it performs without fault...

---

