---
title: "Access denied to /var/lib/mysql"
date: 2013-04-20
forum: General Help
---

### Post by johncroc on 2013-04-20
I am trying to set up mysql on my Ubuntu 12.10 machine.  I need the data to be stored on on a particuler drive (because there is room there).  I don't remember the mysql install asking me where data should be stored, so I re-installed it and the second time around it didn't ask me anything (assume it used whatever settings were present from the initial install).

I looked up "moving the datastore" and found [this]("http://www.turnkeylinux.org/forum/support/20121114/change-default-mysql-database-location"), which calls for me to get into /var/lib/mysql.  When I try to cd /var/lib/mysql I get "Permission Denied"  it's the /mysql directory that's denying me.  I tried "sudo cd mysql" (from the /var/lib directory) and still get permission denied.  If I try "su -" I'm prompted for the root passord, which I don't know.  Apparently I could change that password if I wanted, but my instincts tell me I'm starting down the proverbial rabbit hole and that there MUST be an easier way.  I just can't believe that either moving the existing db (just schema, no data) or creating a new db on another drive isn't something that people do every day and that there's some easy way to get into that directory.

Can anyone help?

John

P.S. I recognize that the question of how to move the db is more appropriately asked in some other forum, but the question of directory permissions is (I think) an Ubuntu admin question which I believe is appropriate here.  If not, please direct me to the appropriate forum.

---

### Post by diesch on 2013-04-20
[LIST]
[*] If you want a root shell use *sudo -i* instead of *su -*
[*] You can configure the data folder in the file */etc/mysql/my.cnf*, section *mysqld*, variable *datadir*
[*] If you want the data folder to be on a partition of its own you can just mount that partition on */var/lib/mysql/* using */etc/fstab*
[/LIST]

---

### Post by johncroc on 2013-04-20
I wish I could say that your suggestions worked.  In case I typed something incorrectly I have included exactly what I typed and Ubuntu's resonses:
> john@sahara:~$ sudo -i mysql stop
[sudo] password for john: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
john@sahara:~$ man sudo
john@sahara:~$ cd /etc/mysql
john@sahara:/etc/mysql$ ls
conf.d  debian.cnf  debian-start  my.cnf
john@sahara:/etc/mysql$ edit my.cnf
Warning: unknown mime-type for "my.cnf" -- using "application/octet-stream"
Error: no write permission for file "my.cnf"
john@sahara:/etc/mysql$ sudo edit my.cnf
[sudo] password for john: 
Warning: unknown mime-type for "my.cnf" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"
john@sahara:/etc/mysql$ sudo -i nano my.cnf
john@sahara:/etc/mysql$ ls
conf.d  debian.cnf  debian-start  my.cnf
john@sahara:/etc/mysql$ sudo -i nano my.cnf
john@sahara:/etc/mysql$ ^C
john@sahara:/etc/mysql$ 


As you can see, I did a man sudo to make sure I understood what I was doing and wasn't making some silly error.

John

---

