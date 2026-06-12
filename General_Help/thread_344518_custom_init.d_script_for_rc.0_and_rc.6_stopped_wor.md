---
title: "custom init.d script for rc.0 and rc.6 stopped working with Edgy"
date: 2007-01-23
forum: General Help
---

### Post by sander marechal on 2007-01-23
Hello,

After my upgrade from Dapper to Edgy, my custom backup script stopped working. This script is located in /etc/init.d/backup.sh and is symlinked from /etc/rc.0 and /etc/rc.6. This worked fine on Dapper. The script itself still works if I run it in a terminal, but it's no longer executed automatically at shutdown or restart.

What's up? Something to do with the init->upstart change?

---

### Post by sander marechal on 2007-01-26
Hello? Anyone? I'd really like my automated backup script working again.

---

### Post by matthewstory on 2007-01-26
try just reloading it  . . . 

cd /etc/init.d/
sudo cp backup.sh backup.sh.back
sudo update-rc.d --force backup.sh remove
sudo update-rc.d backup.sh defaults

Should do the trick nicely.

---

### Post by matthewstory on 2007-01-26
also you'll want to make sure that the opening line of your script is:

#!/bin/sh

not 

#!/bin/bash

don't know why this makes a difference with the update-rc.d scripts, but sometimes it does.

---

### Post by sander marechal on 2007-01-29
The update-rc.d script didn't work for me. It scattered symlinks in all rc*.d directories (while I only need 0 and 6) but the script is still not executed.

I'll have to look into the sh vs bash issue. I'll try that tonight.

Also, I should mention hat my scripts are symlinked as K00* so they are executed first before anything else at shutdown or reboot. Maybe level 00 stopped working between dapper and edgy?

---

### Post by seppelrockt on 2007-03-11
Could you please share you script with us (even if it is not working anymore)? I am currently working on a backup solution for my notebook and maybe I can learn something from your script. Thanks in advance!

---

### Post by sander marechal on 2007-03-11
> **seppelrockt said:**
> Could you please share you script with us (even if it is not working anymore)? I am currently working on a backup solution for my notebook and maybe I can learn something from your script. Thanks in advance!

I've posted a tutorial on my blog about the technique I use back in September. Here you go:

[http://www.jejik.com/articles/2006/07/easy_local_and_remote_backup_of_your_home_network/](http://www.jejik.com/articles/2006/07/easy_local_and_remote_backup_of_your_home_network/)

The reason why it didn't work on Edgy was probably due to the fact that my dapper->edgy upgrade was totally borked. Everything seemed to work fine on the outside but there were *many* problems on the inside of the system (my own fault probably. I used apt-get to upgrade). I "solved" it by backing up, wiping my drive and installing Debian Etch ;-D

---

### Post by seppelrockt on 2007-03-12
Thanks, I found you blog post already. Good to hear that your approach still works with Edgy (hope this is true for Feisty as well).

---

