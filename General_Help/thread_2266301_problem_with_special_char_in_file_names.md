---
title: "problem with special char in file names"
date: 2015-02-21
forum: General Help
---

### Post by glubbish on 2015-02-21
Ubuntu 14.0.4
[COLOR=#000000][FONT=Verdana]LANG=en_AU.UTF-8
Disks are local and mounted in fstab like: 
/dev/sda1 /4tb1 ext4 noatime,nodiratime 0 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]My problem is in 2 parts, with certain movie file names.
eg:
alien3 (where the 3 is superscript) or aeon flux where the ae is a single char.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]alien3 comes out as Alien?.mp4 etc.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Also when I use a samba share from windows 7 the file names come out as blank
I tried putting
unix charset = UTF-8
display charset = UTF-8
in my smb.conf file.
But if made no difference[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I have a synology (1511+) that does not have this problem, but cannot see where the difference lies.
The movies also reside here, but I have added two disks to my kodi box (mythbuntu) and want that as my primary with the nas as backup.

Kodi is able to read the files without problem, also this per script can see the correct names:
[/FONT][/COLOR]
find . -type f -print0 |perl -n0e '$new = $_; if($new =~ s/[^[:ascii:]]/_/g) {print("$_\n");}'
./Æon Flux (2005).avi
./Autómata.2014.1080p.BluRay.x264.YIFY.mp4
./WALL·E (2008).mp4
./Dude, Wheres My Car (2000).MKV
./Alien³ (1992).mp4
./Les Misérables (2012).mkv

Using the same ssh client to connect to the synology and ubuntu system, but synology shows the names as above where the ubuntu shows question marks:
[COLOR=#000000][FONT=Verdana]On the ubuntu kodi system:
ls -als Alien*
1052568 -rw-rw-r-- 1 derek derek 1077823664 Feb 17 09:12 Alien (1979).mp4
2197228 -rw-rw-r-- 1 derek derek 2249956095 Feb 17 09:15 Alien? (1992).mp4
1777864 -rw-rw-r-- 1 derek derek 1820526113 Feb 17 09:13 Alien Resurrection (1997).mp4
1633276 -rw-rw-r-- 1 derek derek 1672470145 Feb 17 09:14 Aliens (1986).mp4[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]On the synology (same ssh client)
Synology> ls -als Alien*
1052568 -rwxrwxrwx 1 admin users 1077823664 Dec 10 2013 Alien (1979).mp4
1777868 -rw-rw-rw- 1 transmis users 1820526113 Dec 11 2013 Alien Resurrection (1997).mp4
1633276 -rwxrwxrwx 1 admin users 1672470145 Dec 10 2013 Aliens (1986).mp4
2197232 -rw-rw-rw- 1 transmis users 2249956095 Dec 12 2013 Alien³ (1992).mp4[/FONT][/COLOR]
On the ubuntu box:
[COLOR=#000000][FONT=Verdana]locale[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]LANG=en_AU.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]LANGUA[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]GE=en_AU:en[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]LC_CTYPE="en_AU.[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]UTF-8"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]LC_NUMERIC="en_AU.UTF[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]-8"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]LC_TIME="en_AU.UTF-8"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]LC[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]_COLLATE="en_AU.UTF-8"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]LC_MO[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]NETARY="en_AU.UTF-8"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]LC_MESS[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]AGES="en_AU.UTF-8"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]LC_PAPER=[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]"en_AU.UTF-8"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]LC_NAME="en_AU[/FONT][/COLOR][COLOR=#000000][FONT=Verdana].UTF-8"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]LC_ADDRESS="en_AU.UT[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]F-8"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]LC_TELEPHONE="en_AU.UTF[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]-8"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]LC_MEASUREMENT="en_AU.UT[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]F-8"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]LC_IDENTIFICATION="en_AU.UTF-8"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]LC_ALL=

I figure once I can see the names correctly from a terminal or ssh, then the samba connections will also work
I know I can rename these, but I would rather fix the issue, so future file names do not get the same problem[/FONT][/COLOR]

Thanks for any help.

---

### Post by glubbish on 2015-02-23
The issue occurred when using wget with ftp to populate this host from the synology. ReFtp of the files gave the proper file names.

---

