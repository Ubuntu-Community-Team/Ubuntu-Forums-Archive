---
title: "Full system backup to another machine?"
date: 2005-04-01
forum: General Help
---

### Post by Sham on 2005-04-01
Hi all,

I have a machine running warty which I would like to setup for scheduled backups to one of my boxes in the basement which is running SuSE 9 (not my choice, sysadmin chaps insisted).

How would I go about this? I guess I would like my box to compress all my folders and sftp them to a destination directory on the remote machine. Is there anything that will do this?

Any other suggested methods would be greatly appreciated.

Cheers

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=Sham]Hi all,

I have a machine running warty which I would like to setup for scheduled backups to one of my boxes in the basement which is running SuSE 9 (not my choice, sysadmin chaps insisted).

How would I go about this? I guess I would like my box to compress all my folders and sftp them to a destination directory on the remote machine. Is there anything that will do this?

Any other suggested methods would be greatly appreciated.

Cheers[/QUOTE]
 apt-cache search remote backup

will return a list of programs that might be usefull

do :

apt-cache show X

where X=packagename to show more information about a package.

I've played around with backuping my /etc with ibackup and it works great after you have configured it. /etc is the directory where your configuration files reside. I'm almost positive you can edit the script and use it to backup other directories too (like /home/username) but it's primary intended for configuration backups.

---

### Post by bored2k on 2005-04-01
You could also [after succesfully doing what demon is saying], create scheluded cron jobs for it .

---

### Post by Sham on 2005-04-01
[QUOTE=demon666_nl]apt-cache search remote backup

will return a list of programs that might be usefull

do :

apt-cache show X

where X=packagename to show more information about a package.

I've played around with backuping my /etc with ibackup and it works great after you have configured it. /etc is the directory where your configuration files reside. I'm almost positive you can edit the script and use it to backup other directories too (like /home/username) but it's primary intended for configuration backups.[/QUOTE]

Thanks for the speedy reply! Can I ask, how does it connect to the remote machine when it transferes the tarball? do you need to supply a username and password in the config file?

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=Sham]Thanks for the speedy reply! Can I ask, how does it connect to the remote machine when it transferes the tarball? do you need to supply a username and password in the config file?[/QUOTE]
 yeah I believe you just have to type it into a config file.

It's a script so if it doesn't support the filetransfer method you prefer you can hack/edit it. I can't remember what it supports natively.

You can encrypt your tarball also.

---

### Post by Sham on 2005-04-01
I just apt-got ibackup, but I dont appear to have a config file to edit in /etc or .ibackuprc

Any ideas?

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=Sham]I just apt-got ibackup, but I dont appear to have a config file to edit in /etc or .ibackuprc

Any ideas?[/QUOTE]
 sudo updatedb
and then either (one of these three will find it for you):
locate ibackup | grep conf
locate ibackup | grep etc
locate ibackup

---

