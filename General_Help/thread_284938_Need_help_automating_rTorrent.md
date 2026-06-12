---
title: "Need help automating rTorrent"
date: 2006-10-26
forum: General Help
---

### Post by paul6 on 2006-10-26
I'm trying to get rTorrent to automatically start seeding my files when I boot up my computer, so I have two questions:

1) How do I get rtorrent to automatically load previous torrents for seeding when I start it?

2) What should I put in my ~/.xsession file to automatically open a terminal with rtorrent running when I boot up?

Thanks in advance.

---

### Post by paul6 on 2006-10-26
*bump*

---

### Post by paul6 on 2006-10-26
*bump*

---

### Post by trash on 2006-10-30
My guess is you need to create an ~/.rtorrent.rc file with some of the options listed in the 'man rtorrent' pages.. i haven't tried it yet so i hope one of the many rtorrent users can help... I just started using rtorrent yesterday, what a treat:)

---

### Post by Anonii on 2006-10-30
You can add in the startup tab of your session preferences (System -> Preferences -> Sessions), this command:
**gnome-terminal -e rtorrent**
This will do the trick.

For me, when I finish a torrent, the torrent moves to my done folder and after the restart of rtorrent, the .torrent file gets deleted, so I dont know how to answer your first question.

You can check my ~/.rtorrent.rc for reference (also try man rtorrent):

```
# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.

# Maximum and minimum number of peers to connect to per torrent.
#min_peers = 40
#max_peers = 100

# Maximum number of simultanious uploads per torrent.
#max_uploads = 15

# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 0
upload_rate = 4

# Default directory to save the downloaded torrents.
directory = ~/Downloads/Done

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /home/habeeb/.session

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/home/habeeb/Downloads/Torrents/*.torrent
schedule = untied_directory,5,5,stop_untied=

# The ip address reported to the tracker.
#ip = rakshasa

# The ip address the listening socket and outgoing connections is
# bound to.
#bind = rakshasa

# Port range to use for listening.
port_range = 63000-63000

# Start opening ports at a random position within the port range.
#port_random = no

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
#check_hash = no

# Set whetever the client should try to connect to UDP trackers.
#use_udp_trackers = yes

# Alternative calls to bind and ip that should handle dynamic ip's.
#schedule = ip_tick,0,1800,ip=rakshasa
#schedule = bind_tick,0,1800,bind=rakshasa

#
# Do not modify the following parameters unless you know what you're doing.
#

# Hash read-ahead controls how many MB to request the kernel to read
# ahead. If the value is too low the disk may not be fully utilized,
# while if too high the kernel might not be able to keep the read
# pages in memory thus end up trashing.
#hash_read_ahead = 10

# Interval between attempts to check the hash, in milliseconds.
#hash_interval = 100

# Number of attempts to check the hash while using the mincore status,
# before forcing. Overworked systems might need lower values to get a
# decent hash checking rate.
#hash_max_tries = 10

# Max number of files to keep open simultaniously.
#max_open_files = 128

# Number of sockets to simultaneously keep open.
#max_open_sockets = <no default>


# Example of scheduling commands: Switch between two ip's every 5
# seconds.
#schedule = "ip_tick1,5,10,ip=torretta"
#schedule = "ip_tick2,10,10,ip=lampedusa"

# Remove a scheduled event.
#schedule_remove = "ip_tick1"


```

Have fun with rtorrent, one of the most practical clients and yet user-friendly, ever.

---

### Post by trash on 2006-10-30
Thanks for showing us your .rtorrent.rc, rtorrent rules:)

---

### Post by Anonii on 2006-10-30
I forgot to point out some things in my rtorrent.rc:

> # Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/home/habeeb/Downloads/Torrents/*.torrent
schedule = untied_directory,5,5,stop_untied=

Monitors /home/habeeb/Downloads/Torrents for *.torrent files, and immediatly adds them to rtorrent.

> # Port range to use for listening.
port_range = 63000-63000

My only forwarded port.

> 
# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 0
upload_rate = 4


The default upload and download rate. I usually change these after my torrents finish, to seed better.

> # Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /home/habeeb/.session

I dont really know what this exactly is. But it stores information on your torrent progress, active progresses etc. If you point that same directory from an other user's rtorrent.rc, it will continue the downloads that the user habeeb was doing.

---

### Post by trash on 2006-10-30
to autostart in xfce put 'xfce4-terminal -x rtorrent' in autostarted applications

---

