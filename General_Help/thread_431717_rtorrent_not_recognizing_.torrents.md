---
title: "rtorrent not recognizing .torrents"
date: 2007-05-03
forum: General Help
---

### Post by treeby on 2007-05-03
my rtorrent isn't picking up the .torrent files i leave for it but it put the lock file in the folder so i know i have the directories set correctly...
also when i try to enter the .torrent file in manually by hitting delete or return  it says that it's an invalid torrent file...i've tried several different torrent files and they all get the same message AND they work in uTorrent in vista... so i know it's not the torrent files.
i'm running 64bitrtorrent in AMD64 Feisty. i'm trying to keep the .torrents on a SATA drive. I also tried keeping them on my desktop and rtorrent still wouldn't pick those up either...still got the 'invalid torrent file' thing....i had rtorrent working before fine with 32bitFeisty and the .rc file below which i'm still trying to use....

any help much MUCH appreciated
thanks!

(p.s - i know i should enable encryption but every time i do i get an error)

# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.

# Maximum and minimum number of peers to connect to per torrent.
min_peers = 40
max_peers = 100

# Same as above but for seeding completed torrents (-1 = same as downloading)
#min_peers_seed = 10
#max_peers_seed = 50

# Maximum number of simultanious uploads per torrent.
max_uploads = 15

# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 0
upload_rate = 0

# Default directory to save the downloaded torrents.
directory = /media/sda1/seeding

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /media/sda1/seeding/

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/media/sda1/seeding/torrents/*.torrent
schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
#schedule = low_diskspace,5,60,close_low_diskspace=100M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
#schedule = ratio,60,60,stop_on_ratio=200,200M,2000

# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no

# The ip address the listening socket and outgoing connections is
# bound to.
#bind = 127.0.0.1
#bind = rakshasa.no

# Port range to use for listening.
port_range = 7880-7989

# Start opening ports at a random position within the port range.
#port_random = no

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
check_hash = no

# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes

# Alternative calls to bind and ip that should handle dynamic ip's.
# PUT BOTTOM OUT
#schedule = ip_tick,0,1800,ip=rakshasa
#schedule = bind_tick,0,1800,bind=rakshasa

# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
# encryption = allow_incoming,enable_retry,prefer_plaintext
 #encryption = allow_incoming,enable_retry,try_outgoing


# Do not modify the following parameters unless you know what you're doing.
#

# Hash read-ahead controls how many MB to request the kernel to read
# ahead. If the value is too low the disk may not be fully utilized,
# while if too high the kernel might not be able to keep the read
# pages in memory thus end up trashing.
hash_read_ahead = 10

# Interval between attempts to check the hash, in milliseconds.
hash_interval = 100
# Number of attempts to check the hash while using the mincore status,
# before forcing. Overworked systems might need lower values to get a
# decent hash checking rate.
hash_max_tries = 10

# Max number of files to keep open simultaniously.
max_open_files = 128

# Number of sockets to simultaneously keep open.
#max_open_sockets = <no default>

# Example of scheduling commands: Switch between two ip's every 5
# seconds.
#got rid of the 2 below
#schedule = "ip_tick1,5,10,ip=torretta"
#schedule = "ip_tick2,10,10,ip=lampedusa"

# Remove a scheduled event.
schedule_remove = "ip_tick1"

---

### Post by konsole on 2007-05-04
> **treeby said:**
> 
# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 0
upload_rate = 0

# Default directory to save the downloaded torrents.
directory = /media/sda1/seeding

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /media/sda1/seeding/

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/media/sda1/seeding/torrents/*.torrent
schedule = untied_directory,5,5,stop_untied=


What version of rtorrent and libtorrent are you trying to use?
Where did you get them and how did you install them?
What are the permissions on /media/sda1/seeding/torrents/

Also it's not a good idea to set upload to unlimited. Set it to 80% of your upload max.

---

### Post by treeby on 2007-05-04
first i used the synaptic package manager to install them and when that didn't
work i got the newest .deb files from the rtorrent web page and i used
sudo dpkg -i rtorrentblahblahblah.deb and with libtorrent.deb. i downloaded
the AMD64 versions from here: [http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Funiverse%2Flibt%2Flibtorrent%2Flibtorrent6_0.8.2-1_amd64.deb&md5sum=d1c176c64b8db2963f76415297b28e86&arch=amd64&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Funiverse%2Flibt%2Flibtorrent%2Flibtorrent6_0.8.2-1_amd64.deb&md5sum=d1c176c64b8db2963f76415297b28e86&arch=amd64&type=main)

i have a core2duo and i installed AMD64 ubuntu feisty...it
says these rtorrent files are for dapper...could that be the problem? but i assume
if it didn't work with synaptic it's not the program...but i guess i could be wrong.

What are the permissions on /media/sda1/seeding/torrents/

i don't understand what you mean by 'permissions'
that's just the directory where i want to keep my torrents. it's on a SATA drive.
i think that's about all i could tell you about it.

thanks for any help

---

### Post by konsole on 2007-05-06
> **treeby said:**
> 
What are the permissions on /media/sda1/seeding/torrents/

i don't understand what you mean by 'permissions'
that's just the directory where i want to keep my torrents. it's on a SATA drive.
i think that's about all i could tell you about it.

thanks for any help

Unix file permissions are managed with the chmod utlity which controls who can read, write and execute files. Ensure that you have read and write access to files in the/media/sda1/seeding/torrents/ directory.

Because the repository versions of rtorrent/libtorrent are so old, these versions are likely to be quite buggy.Your best bet IMO is to compile from the sources available from the rtorrent website.

---

