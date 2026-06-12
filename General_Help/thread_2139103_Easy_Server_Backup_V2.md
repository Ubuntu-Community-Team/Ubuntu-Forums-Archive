---
title: "Easy Server Backup V2"
date: 2013-04-26
forum: General Help
---

### Post by strid3r on 2013-04-26
Here is a program to make automatic backups of your web directory and all mysql databases with security and ease of use in mind.
All backups are compressed and encrypted with des3

Screenshots:

[http://i.imgur.com/qDTB2Nd.png]("http://i.imgur.com/qDTB2Nd.png")
[http://i.imgur.com/BlCsnPn.png]("http://i.imgur.com/BlCsnPn.png")


Download:

[ATTACH]241794[/ATTACH]


Usage:

To make a backup
```
backup
```

To restore web server to previous point
```
restore
```

To decrypt a file
```
dcrypt [filename].crypt [output]
```

Installation:

Extract and run install.sh with sudo
```
tar -xvzf ebackup.tar.gz
cd ebackup
chmod +x install.sh
sudo ./install.sh
```

Follow the prompts to change the default values and choose option 1 when ready to install.



Notes:

To make automatic nightly backups at midnight add the following to cron

```
sudo crontab -e
```
```
0 0 * * * /bin/backup
```

This program will automatically generate a long password to encrypt/decrypt your files and store it as /root/backuppw.txt
Make a local backup of this file, as all backups made after installation will be encrypted with this password.

---

