---
title: "Backing up directories remote FTP"
date: 2017-06-08
forum: General Help
---

### Post by tmoflash2 on 2017-06-08
Hello,

I have a few servers running Minecraft. I need to back up the directors. I am able to mount locally and remote. I just cannot get it to synch. 

Here is what I am trying to do.

I have a VPS I want to send all the directories to. I have 4 other Dedis (all servers are using Ubuntu 16.04)

I created this on each Dedi: [COLOR=#24292E][FONT=-apple-system]mkdir /mnt/offsite_backup

[/FONT][/COLOR][COLOR=#24292E][FONT=-apple-system]Then I ran this command: curlftpfs directory:[/FONT][/COLOR][COLOR=#2C2C2C][FONT=&quot]example_password[/FONT][/COLOR][COLOR=#24292E][FONT=-apple-system]@VPS_IP /mnt/offsite_backup/

[/FONT][/COLOR][COLOR=#24292E][FONT=-apple-system]I created a backup.sh located in /var/backup.sh

I put this inside of backup.sh

[/FONT][/COLOR][COLOR=#969896]#!/bin/bash[/COLOR]

TIME=[COLOR=#183691]`date +%b-%d-%y`[/COLOR]

FILENAME=SERVERS-backup-[COLOR=#333333]$TIME[/COLOR].tar.gz

SRCDIRServers=/srv/daemon-data/
DESDIRServers=/mnt/offsite_backup/Backups/Server-2  <----- this changes based on the different servers

tar -cpzf [COLOR=#333333]$DESDIRServers[/COLOR]/[COLOR=#333333]$FILENAME[/COLOR] [COLOR=#333333]$SRCDIRServers

Then:


[LIST]
[*]crontab -e"
[*]Go to the end of the page
[*]Paste in the following: "00 1 * * * bash /var/backup.sh"
[*]Save and Exit; //Command to start backps
[/LIST]
[COLOR=#24292E][FONT=-apple-system]curlftpfs directory:[/FONT][/COLOR][/COLOR][COLOR=#2C2C2C][FONT=&quot]example_password[/FONT][/COLOR][COLOR=#333333][COLOR=#24292E][FONT=-apple-system]@VPS_IP /mnt/offsite_backup/


I run all of this and everything seems happy with no errors, but it never backups anything. Any ideas?[/FONT][/COLOR]


[/COLOR]

---

### Post by tmoflash2 on 2017-06-09
Or maybe a better way to do what I am trying to complete.

I would like to set up a backup system for specific directories.

Using remote servers.

I would like this to be automated every 24 hours and only keep 7 days worth of backups.

---

