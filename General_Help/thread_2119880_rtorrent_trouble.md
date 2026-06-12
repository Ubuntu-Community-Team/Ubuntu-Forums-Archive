---
title: "rtorrent trouble"
date: 2013-02-25
forum: General Help
---

### Post by rucker222 on 2013-02-25
Hi guys,

I need some help please.

I installed and had rtorrent working for all of about half a day yesterday until the evening when I went to use it again and got this error. rtorrent: undefined symbol: _ZN7torrent10ThreadBase8m_globalE

after taking me quite a while and having issues I have managed to get it working again (sort of).

when trying to start r torrent I get the below errors.


rtorrent: Error in option file: ~/.rtorrent.rc:102: Command "hash_read_ahead" does not exist.
lee@ubuntu:~$ rtorrent 
rtorrent: Error in option file: ~/.rtorrent.rc:105: Command "hash_interval" does not exist.
lee@ubuntu:~$ rtorrent 
rtorrent: Error in option file: ~/.rtorrent.rc:110: Command "hash_max_tries" does not exist.


So to get around this I had to comment those lines out as shown below.


# Hash read-ahead controls how many MB to request the kernel to read
# ahead. If the value is too low the disk may not be fully utilized,
# while if too high the kernel might not be able to keep the read
# pages in memory thus end up trashing.
[COLOR=Red]#hash_read_ahead = 10 <<<<<< this line[/COLOR]

# Interval between attempts to check the hash, in milliseconds.
[COLOR=Red]#hash_interval = 100 <<<<<< this line[/COLOR]

# Number of attempts to check the hash while using the mincore status,
# before forcing. Overworked systems might need lower values to get a
# decent hash checking rate.
[COLOR=Red]#hash_max_tries = 10 <<<<<< this line[/COLOR]

execute = {sh,-c,/usr/bin/php /var/www/rutorrent/php/initplugins.php lee &}

my question is, can/does this need to be fixed and how? 

It there a way to test all of the required dependencies are installed correctly and install/update them if necessary. 

any help would be greatly appreciated. 

Cheers

Lee.

---

### Post by rucker222 on 2013-02-25
A couple of other things i forgot to mention were that I have installed rtorrent 0.9.2/0.13.2

I have also got a message at the bottom of the rtorrent screen saying 

Scheduled command failed: ratio: "stop_on_ratio" does not exist.

Cheers.

---

