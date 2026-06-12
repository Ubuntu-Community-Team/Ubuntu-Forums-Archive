---
title: "Ubuntu moves to new server"
date: 2022-10-24
forum: General Help
---

### Post by jack1966 on 2022-10-24
hi all
when Ubuntu moves to new server
I use the below command to zip the old server's folders (partially excluded)
[COLOR=#ff0000]
tar -cvpzf backup.tgz --exclude=/proc --exclude=/root --exclude=/boot --exclude=/dev/mapper --exclude=/etc/fstab --exclude=/lost+found --exclude=/home --exclude=/mnt --exclude=/sys /
[/COLOR]
[COLOR=#ff0000][FONT=Consolas]tar -xzvpf backup.tgz -C /[/FONT][/COLOR]
The following error occurs during startup
new server:
Device mapper fails
System is functioning normally
old server:
raise network interfaces
Checked network settings and saw no errors
Apache2 some time to restart
The website (domain name) cannot be resolved after accessing the website after nearly two hours of operation
Open the default website directly with IP and it works fine


Strangely ~ old and new servers ~ seems to be a problem with name resolution
(failed)raise network interfaces
but
Bind9 restart problem did not improve
apache2 restart but it works again

How can they be fixed?

Thanks

---

### Post by TheFu on 2022-10-24
Are you changing the IP and hostname and crypto-keys for the new server or do you intend to take the old server out of production completely?

Different programs will need to be handled differently.  The way to migrate a server with a DBMS is different than the way to migration a reverse-proxy server is different from how to migrate a media center server.  They each have special considerations.

BTW, why use tar?  Tar was created when 250MB was considered huge.  Use a better tool.  If you will take the old server down, before bringing the new server up, I'd use 'rsync.'  Or if it is virtual machine, I'd use the built-in VM migration method depending on the hypervisor used.  
[https://libvirt.org/migration.html](https://libvirt.org/migration.html) - for any supported by libvirt
[https://linuxcontainers.org/lxd/docs/master/migration/](https://linuxcontainers.org/lxd/docs/master/migration/)  for lxd/lxc

If you are permanently migrating, I'd exercise my backup/restore process.   Practice makes perfect.

---

### Post by jack1966 on 2022-10-25
Reference when looking for information
[http://community.bwbot.org/topic/2918/%E5%9C%A8ubuntu-20-04%E4%B8%8A%E4%BD%BF%E7%94%A8systemback](http://community.bwbot.org/topic/2918/%E5%9C%A8ubuntu-20-04%E4%B8%8A%E4%BD%BF%E7%94%A8systemback)
Enter the following two lines of command
[COLOR=#333333][FONT=Ubuntu]sudo sh -c 'echo "deb [arch=amd64] [/FONT][/COLOR][http://mirrors.bwbot.org/](http://mirrors.bwbot.org/)[COLOR=#333333][FONT=Ubuntu] stable main" > /etc/apt/sources.list.d/systemback.list'[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]sudo apt-key adv --keyserver '[/FONT][/COLOR][hkp://keyserver.ubuntu.com:80'](hkp://keyserver.ubuntu.com:80')[COLOR=#333333][FONT=Ubuntu] --recv-key 50B2C005A67B264F[/FONT][/COLOR]
But when it comes to installing sudo apt-get install systemback it stops (because the desktop package is to be installed) and does not continue
Could it be because of this?

---

### Post by TheFu on 2022-10-25
I suspect you need to open a new thread, since the last post doesn't seem related at all to migration to a new server.

1 thread per question.  Be certain to choose a short, but clearly descriptive title for the thread so people comfortable with that issue can see it and choose if they can help or not.

---

### Post by jack1966 on 2022-10-25
Thanks for your valuable comments
Reference systemback:
[https://github.com/BluewhaleRobot/systemback](https://github.com/BluewhaleRobot/systemback)

---

