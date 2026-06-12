---
title: "rtorrent - completed torrents not removed."
date: 2008-06-08
forum: General Help
---

### Post by musther on 2008-06-08
I'm reasonably new to rtorrent, but I'm enjoying using it.  I've managed to set it up pretty well, monitoring a directory for torrents, and moving the completed files.  The problem is, even though completed files are successfully moved, and the source torrent files are deleted, they remain listed in rtorrent, and are simply labelled as 'done' and '[CLOSED]'.

Here's my .rtorrent.rc:

```
# Maximum and minimum number of peers to connect to per torrent.
#min_peers = 40
#max_peers = 100

# Same as above but for seeding completed torrents (-1 = same as downloading)
#min_peers_seed = 10
#max_peers_seed = 50

# Maximum number of simultanious uploads per torrent.
#max_uploads = 15

# Global upload and download rate in KiB. "0" for unlimited.
#download_rate = 0
upload_rate = 8

# Default directory to save the downloaded torrents.
directory = /media/dump/dling/

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /home/musther/rtorrent/

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/home/musther/torrents/*.torrent
schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
#schedule = low_diskspace,5,60,close_low_diskspace=100M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"

# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no

# The ip address the listening socket and outgoing connections is
# bound to.
#bind = 127.0.0.1
#bind = rakshasa.no

# Port range to use for listening.
port_range = 5881-5889

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

# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
encryption = allow_incoming,try_outgoing,enable_retry,prefer_plaintext

# Enable DHT support for trackerless torrents or when all trackers are down.
# May be set to "disable" (completely disable DHT), "off" (do not start DHT),
# "auto" (start and stop DHT as needed), or "on" (start DHT immediately).
# The default is "off". For DHT to work, a session directory must be defined.
#
#dht = auto

# UDP port to use for DHT.
#
#dht_port = 5881

# Enable peer exchange (for torrents not marked private)
#
peer_exchange = yes

# Create symlinks in the watch directory with a suffix indicating the
# download state.

#on_start    = link1,"create_link=tied,,.started"
#on_stop     = link1,"delete_link=tied,,.started"
#on_finished = link1,"create_link=tied,,.finished"
#on_erase    = link1,"delete_link=tied,,.finished"

# When the torrent finishes, it executes "mv -n <base_path> ~/aaa/"
# and then sets the destination directory to "~/aaa/". (0.7.7+)

on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/media/dump/completed/"

#When the torrent finishes, the .torrent file is removed.
on_finished = rm_torrent,"execute=rm,$d.get_tied_to_file="

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

```

---

### Post by nickpj on 2009-04-28
I have the same two "on_finished" handlers, observe the same thing in Ubuntu 8.10,  and have the same question. Did you ever find a solution to this?

---

### Post by musther on 2009-04-28
Never did, sorry.

---

### Post by nickpj on 2009-04-28
Hmmm, okay. Was just googling for this after posting, _may_ have found something that _could_ be what we're both looking for on this page: [http://www.digipedia.pl/man/rtorrent.1.html](http://www.digipedia.pl/man/rtorrent.1.html) ... in particular, have you tried using this setting? :
session_on_completion = no

I'll give it a go and see if it helps.

---

### Post by nickpj on 2009-04-30
Toggling "session_on_completion" did not work. Seems like this might be a bug. Have logged it upstream: [http://libtorrent.rakshasa.no/ticket/1715](http://libtorrent.rakshasa.no/ticket/1715)

---

