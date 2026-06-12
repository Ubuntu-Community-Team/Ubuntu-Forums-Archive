---
title: "Unable to perform backup"
date: 2007-01-11
forum: General Help
---

### Post by philavia on 2007-01-11
Dear all,

First of all thank you for your help.  I read a lot your posts and  they permit me to use and configure properly Ubuntu since 5.04.  Now I have installed 6.10 (not really happy with this version, but this is another story).

Since years, I try, without success, to perform backups under Linux.  I live since I started using Linux (1997) with a "Damocles" sword.  The only solution that I apply is from time to time performing a copy of important file onto an USB disk.  Far from efficient.

Here is the list of my latest experiences, maybe someone amongst you will be able to lead me into the correct direction.

**Configuration**
Ubuntu 6.10
Portable computer Vaio VGN-S5M
Not enough free space on the HD to place the backup locally, they must be placed on a NAS.
Drive NAS QNAP TS-201
Shared directory : Public
Sub-directory : Public/backup_vaio which will contain the backup files of the Vaio.
Like you see, the NAS is accessible through Samba.

**Manual copy of files**
sudo mount //192.168.123.99/Public /media/backup
sudo cp /home/philippe /media/backup/backup_vaio/

Of course, it works, but it is the same principle (but slower) as copying manually, from time to time, the files on an USB disk.  Furthermore, there is no copy of the links, there is no permission associated with files ...

Not a backup solution.

**Using tar**
sudo mount //192.168.123.99/Public /media/backup
sudo tar cvpfz "/media/backup/backup_vaio/20070111.tgz" "/home/philippe"

The file "20070111.tgz" is created (huge size, of course) but when I try to open it with "file-roller", I get:

gzip: stdin: Input/output error
tar: Fin prématurée (EOF) rencontrée dans l'archive.
tar: Erreur non récupérable: fin de l'exécution immédiate

Conclusion : Not a solution, backup must be reliable and readable.

**rsync**

sudo mount //192.168.123.99/Public /media/backup
sudo rsync -az /home/philippe /media/backup/backup_vaio/
sudo umount /media/backup/

During "rsync" command execution, there are lot of messages :

rsync: chown "/media/backup/backup_vaio/...<snip> ... <snip>..." failed: Operation not permitted (1)

It seems to be logical as the filesystem used does not permit to change rights, ... .
On the other side, it does not stop the execution of "rsync".

The bad news is that after a few minutes, "rsync" stops with the following message :

io timeout after 30 seconds -- exiting
rsync error: timeout in data send/receive (code 30) at io.c(171) [sender=2.6.8]
rsync: writefd_unbuffered failed to write 120 bytes [generator]: Broken pipe (32)
rsync error: error in rsync protocol data stream (code 12) at io.c(1119) [generator=2.6.8]

Conclusion : does not work, I does not trust it for my beloved data 8) .

**Simple Backup**
_Configuration:_
General : Manual backups only
Include : /var /home /usr/local /etc
Exclude : Paths : /media /var/cache /var/spool /var/tmp
Exclude : File types : none
Exclude : Regex : none
Exclude : Max size : none
Destination : Use custom backup directory : /media/backup/backup_vaio/
Time : never ( ???? I suppose that it does not need to be configured for a "Manual backup only") 
Purging : Enabled : Logarhitmic

_Backup now !_

A backup run is initiated in the background. The process id is: 8396.

ps ax gives :
8396 ?        Z      0:00 [sbackupd] <defunct>

No idea of how it works and what happened.

Conclusion : useless.

**backup-manager**
I will not copy the configuration file used, it will be too long, but I can say that I carefully read the manual, and I am sure that it was properly configured.

sudo mount //192.168.123.99/Public /media/backup
sudo backup-manager

It starts nicely, then after some tilme :

Impossible de créer /media/backup/backup_vaio/vaio-home.20070111, voir /tmp/bm-tarball.log.Xo6960 pour les détails.
Lors de la génération des archives, 1 erreur(s) se sont produite(s).

The error in the above mentionnes file is :

---- exception type = [BUG] ----------
[source]
	File compressor.cpp line 310 : it seems to be a bug here
[most outside call]
-----------------------------------

Error while saving /home/philippe/.Trash/evolution/mail/local/Inbox.ibex.index: Error while writing to file: Erreur d'entrée/sortie
Error while saving /home/philippe/.Trash/evolution/mail/local/Inbox.cmeta: Error while writing to file: Erreur d'entrée/sortie
INTERNAL ERROR, PLEASE REPORT THE PREVIOUS OUTPUT TO MAINTAINER


After that, nautilus hangs and prevent me to :
- navigate to /media/backup
- Visualize the network with the "Serveurs réseau" icon on the desktop.
- All icons on the network disppears.

After 10 minutes (coffee break), everything stabilizes, I am able to :
- Use nautilus,
- Desktop icons are back,
- I am able to visualize the icon "Serveurs réseau" of the desktop, and see that a "dar" file of 216Mo was created, but is incomplete and corrupted.

I try to unmount /media/backup/ through the icon on the desktop (right click / Eject) I get:

Erreur : impossible de déterminer le véritable chemin d'accès à ce périphérique: Aucun fichier ou répertoire de ce type

Via a console "sudo mc", I am able to visualize /media/backup/backup_vaio and the useless "dar" files.

Then I do : sudo umount /media/backup/ and it works, the icon disapears from the desktop and /media/backup is properly unmounted.

Conclusion : useless

Well, well.....

Sorry for all error messages in french, I hope that you will be able to see what they means.

Unable (since years) to perform backup with Linux.
Any idea, I have lost all my resources and motivations with this issue (I look with envy to the right : my office computer running XP and performing a perfect backup with Norton).

Many thanks in advance.

---

