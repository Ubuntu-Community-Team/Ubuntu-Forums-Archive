---
title: "What's the best way for a remote backup?"
date: 2019-03-22
forum: General Help
---

### Post by ELMIT on 2019-03-22
I got a droplet with Ubuntu 14.04 on Digital Ocean. I want to rebuild it with 18.04.

However, Digital Ocean asked to rebuild the droplet.

What is the best way to make a backup and download it to my desktop (Ubuntu 18.04), examine the files and prepare for a new droplet.

I don't have much space there left of the 80 GB. So, a backup way that lets me download pieces would be better than a big file.
What files can I omit to backup. I guess the entire /var/log might be not be needed anymore.

---

### Post by ELMIT on 2019-03-22
I found something on the Internet:

```

rsync -avzP --delete -e ssh user@server_IP:source-directory /destination_directory_on_local_machine/

```

It seems a perfect solution, doesn't it?

1. create a local account on my desktop: remotebackuper with a home directory /mnt/newdrive/backup/./digitalocean/
That /./ makes sure, that the user cannot leave that directory

2. at digital ocean I make a directory listing and remove not to backup directories, like /,  /lost+found, /tmp, /proc, 
/ to make sure that I don't backup vmlinuz*, initrd* and swapfile

3. since I don't sync, but backup, I can omit the "--delete" option
Would the following command be correct, to backup the home directory of the remote server to my local directory /mnt/newdrive/backup/digitalocean/home ???
```

rsync -avzP -e ssh remotebakuper@<local IP>:  home /digitalocean/home

```

---

### Post by ELMIT on 2019-03-22
working on it, ... but cannot get it to work.

1. I must login at digital ocean, since as root I cannot login there and root access is necessary to fetch all directories

2. I have a different port, ... figured out that I need to use then ' ' to get this

3. I use $HOSTNAME to make sure it would come into the right directory tree of all my digital ocean backups

That resulted in this command at digital ocean:

```
sudo rsync -avzP /bin -e 'ssh -p77' remotebackuper@123.123.123.123:/$HOSTNAME/bin
```

I expected, that the remote /bin directory would be put into the $HOSTNAME directory with the subdirectory /bin

However, ....
```
sending incremental file list
rsync: mkdir "/example.com/bin" failed: No such file or directory (2)

```


I tried many other combinations, ... but nothing worked!

---

### Post by maglin2 on 2019-03-23
I claim no expertise whatever  in this, but might a gui app which supports incremental remote backup be a way forward?
I use back in time for local incremental backups to external hdd. It works very well in this mode, and I see that it also supports remote backup to a host   [https://backintime.readthedocs.io/en/latest/settings.html#ssh](https://backintime.readthedocs.io/en/latest/settings.html#ssh)

---

### Post by ELMIT on 2019-03-23
Solved:

1. I had to install sshpass  so that I could add a password to the ssh

sudo apt-get install sshpass
sshpass -p your_password ssh user@hostname

2. I removed the / after the IP and the destination directory
sudo rsync -avzP /bin -e 'sshpass -p SuperSecret ssh -p77' remotebackuper@123.123.123.123:$HOSTNAME

I hope I saved somebody some search time ;-)

---

