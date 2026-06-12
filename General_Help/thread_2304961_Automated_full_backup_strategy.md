---
title: "Automated full backup strategy?"
date: 2015-12-01
forum: General Help
---

### Post by toddk63 on 2015-12-01
I have Xubuntu 14.04 OS that I use as a server.  The OS resides on a 16 GB CF-IDE "disk". The size is currently about 10 GB uncompressed. I currently use Clonezilla to occasionally backup the CF disk.  I have even on one occasion used it to restore from a crash.  This approach certainly gets everything back as it was, but it can't be automated to make regular backups.

What I want to do is scheduled backups, with a GUI rsync (or similar) , on everything needed to restore from a total HDD crash of the OS.  I think a full restore involves:
    - re-installing the OS from a live distro
    - re-installing apps with "dpkg --set-selections </root/backup-list-o-pkgs"
    - restoring configuration files i.e. /etc/, others? 
    - restore data (if any)

What do I need in addition to /etc/?

What about apps from 3rd party repositories?  Could I just backup and restore everything on root(/)?  Would that have all the apps and their config files included?

Can I automate the creation of the application list?

What can I exclude?

Looking for some suggestions.

Thanks,

Todd K.

---

### Post by sandyd on 2015-12-01
Use cron do so something like this:
```

dpkg --get-selections > /media/backup/dpkglist
## Backup custom packages
cp -R /root/packages  /media/backup/packages
## Backup /etc
cp -R /etc /media/backup/etc
## Additional Sources
cp -R /etc/apt/sources.list.d /media/backup/sources
## Sources.list
## Apt Keys
apt-key exportall > /media/backup/aptkey
cp /etc/apt/sources.list /media/backup/sources.list
## Additional data here

```
Restoring 
```

## Restore Sources
cp /media/backup/sources.list /etc/apt/sources.list
cp  /media/backup/sources/* /etc/apt/sources.list.d/
## ap
## Reload dpkg list of installed packages
apt-cache dumpavail > /tmp/packages
dpkg --merge-avail /tmp/packages
## Install custom built packages
dpkg -i  /media/backup/packages/*.deb
apt-get -f install
## Install additional packages
apt-get update
apt-get install dselect
dselect update
dpkg --set-selections < /media/backup/dpkglist
apt-get dselect-upgrade -y
#Restore /etc
cp -R /media/backup/etc/* /etc

```

Above is just an example, probably should adapt to your own needs.

If your managing multiple servers, I find using a configuration management system (Puppet/Chef/Salt/Ansible) works quite well and makes reinstalls and reconfigurations a snap.
You can also use some version management like git for /etc as long as you don't place large files in /etc and prune the history when it gets too big.

---

### Post by scoutchorton on 2015-12-01
There is a program that comes with Ubuntu (and probably might come with Xubuntu) for doing backups. 

[ATTACH=CONFIG]265881[/ATTACH]

All flavors of Ubuntu are just different default programs; weather it is Lubuntu with the LXDE (Lightweight Desktop Enviroment), or Ubuntu Server (with LAMP, FTP, and other server materials), they have core programs that are the same. So Backups should be a program on multiple distros. If not, should be installable if you look around.

Good luck! :D

Also, you can choose what to back up with this. Default, it backs up the /home/user/ folder (excluding Downloads, maybe because mine is pretty big). So you can change it to back up / and you should be good!

---

### Post by toddk63 on 2015-12-01
Sandyd,  thanks for that.  Excuse my noobness...I looked into every command you provided to try and understand it.  I could not find /root/packages directory.  Does that mean I do not have any custom packages installed?

<<## Backup custom packages>>
<<cp -R /root/packages  /media/backup/packages>>

I presume the recipe you gave me is fairly complete.  Pretty much all settings reside in /etc ?

I found some data that configures my Plex Media Server in /var/lib so I may include that as well.

Todd K.

---

