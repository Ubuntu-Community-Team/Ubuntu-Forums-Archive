---
title: "Backuppc not working after reboot"
date: 2007-10-30
forum: General Help
---

### Post by moschops on 2007-10-30
I have noticed that Backuppc does work for me after a reboot - the webserver is running but reports:

```
Error: Unable to connect to BackupPC server
```

in its UI.  

I found that after a reboot I could manually start the server with:

```
sudo /etc/init.d/backuppc start
```

and all would be fine, at least until the next reboot.

I have since discovered that this problem is because I set up backuppc to to use an external drive for storage and made a sym link from /var/lib/backuppc to /media/backup/backuppc which is as has been suggested elsewhere because simply changing the config files to point directly at your external drive causes problems elsewhere.

I believe I found out why backuppc isn't starting at boot time because if the external drive isn't mounted at the time it starts the script throws out this error (I see it during boot on the console too):

```
mkdir /var/lib/backuppc: File exists at /usr/share/backuppc/bin/BackupPC line 1791
```

looking at the script I noticed line 1791 says:

```
   mkpath($LogDir, 0, 0777)  if ( ! -d $LogDir );
```

Maybe my understanding of Perl is wrong but shouldn't this be:

```
    if ( ! -d $LogDir ) { mkpath($LogDir, 0, 0777); }
```

???  When I changed it to that BackupPC was able to start okay...

Plus shouldn't there be some way to start BackupPC later in the boot - after any external drives have been mounted?  I know how to change the order of execution of things in the /etc/init.d dir using the 'bum' tool - but I 'm not sure when those drives would be mounted - perhaps the only thing I can do is put the starting of BackupPC server right at the end of boot up?

---

