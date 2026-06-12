---
title: "rdiff-backup error: directory exists, but does not look like a rdiff-backup directory"
date: 2024-01-08
forum: General Help
---

### Post by freeflyjohn on 2024-01-08
I am getting the following error when running an initial rdiff-backup on a freshly formatted USB HDD....

```

Fatal Error: Destination directory

/media/backupStorageOS

exists, but does not look like a rdiff-backup directory.  Running
rdiff-backup like this could mess up what is currently in it.  If you
want to update or overwrite it, run rdiff-backup with the --force
option.

```

I am running rdiff-backup via a bash script as sudo and the script is stored in /bin/backupscripts/

The HDD is connected to a USB port on my Ubuntu server (running on a Dell T30 PowerEdge).

The issue seems to have started since I added the USB HDD to fstab as follows...

```
UUID=f0845195-37c9-444a-99e2-c413de292acb /media/backupStorageOS/ ext4 noatime,nodiratime,x-gvfs-name=BackupStorageOS,noauto 0 2
```

Previously I did not run the rdiff-backup script as sudo and the scripts were in my home folder.

Since moving the script to /bin/backupscripts/ to run it as sudo, I did not get this error when the HDD was mounted in the /media/username folder.  The error only occured since adding the USB HDD to fstab.

I recall 'TheFu' advising that the USB HDD should be added to fstab  (rather than in the /media/username folder) to maintain UUID etc

I know I can use the --force option, but I've never had to do this  before when running rdiff-backup, so I want to understand why its now  become an issue and make sure I am doing it correctly.

---

