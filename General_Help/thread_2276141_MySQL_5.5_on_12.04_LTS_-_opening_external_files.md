---
title: "MySQL 5.5 on 12.04 LTS - opening external files"
date: 2015-04-30
forum: General Help
---

### Post by sandydejax on 2015-04-30
I used to program in C for DOS, but it's just too hard to manage memory beyond 4 MB on a DOS system.  I thought that Linux would give me the access of DOS with newer hardware and more power but I'm lost here.
   I'm trying to port an old home-rolled database with megabyte-plus files into MySQL.  I've installed MySQL and demonstrated I can play with directly-input data.  I've gotten a small table of real data into a clean .TXT file, but the statement "LOAD DATA INFILE <file location and name>" returns

ERROR 13 (HY000): Can't get stat of <file location and name>.

I've seen similar here for exporting, but it's not quite the same.  If I strip the location, I get

Can't get stat of '/var/lib/mysql/ships/NATOHULL.TXT'

and the other threads here seem to say I should just dump my data file into that folder, but /mysql/' is locked.  Using the GUI to access permissions gives me "You are not the owner and cannot change these permissions."  How do I get MySQL access to my data files, or alternately get my data files into where it wants to read them from?  I can follow instructions but I _don't_ understand Linux yet.

Thanks!

---

### Post by sandydejax on 2015-04-30
More info: I have added the data folders to the list of apparmor allowances with

sudo gedit /etc/apparmor.d/usr.sbin.mysqld and
sudo /etc/init.d/apparmor reload

As suggested by [**[COLOR=#000000]LaurentEdel[/COLOR]**]("http://ubuntuforums.org/member.php?u=1251011") in thread #822084 "MySQL file access" but nothing has changed.

---

