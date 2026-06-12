---
title: "Corrupted file system HELP"
date: 2006-07-10
forum: General Help
---

### Post by manumahajan on 2006-07-10
I have been using ubuntu for the past six months and have been highly impressed. Recently, did a dist-upgrade to dapper and have been enjoying it to the fullest and im really happy to say that hadn't booted into windows for over three months until today...

when i started my laptop today, after reaching 'Checking root file system' during the boot process it started doing a file system check with the following message - 'contains a file system with errors, check forced' and it started giving me lots of errors. The process could not complete and it asked me to run a fsck manually. On running that program i got a lot of errors relating to 'inode size being reported incorrectly or something like that' I pressed control c and exited out of the program.

I have very little knowledge about the ext3 file system and Im relatively new to linux.

Please help me and tell me what should i do at this stage. My hard disk seems to be ok as i can boot into windows and it seems to be working fine. Are there any tools that i can run from windows to examine and correct the file system. 

I have at least five days of work on that partition for which i do not have any backup. Please help me as i am stuck and guide me how to proceed.

Also is there any utility that i can run from the command line and backup my data on a cd as i am able to access the file system once the file check errors are displayed?

---

### Post by RAOF on 2006-07-10
Do the fsck and let it finish.  It's the filesystem repair utility.  That should fix things.  Once that's done, you should be back working again.

---

### Post by hanzomon4 on 2006-07-10
Boot into ubuntu, but don't login... 

Press ctrl+alt+F1 login and type
```
sudo telinit 1
``` when asked for a password enter your user password

next type ```
mount -o remount,ro/
```

and last type ```
fsck /dev/whatever drive your root partition is on
```

let it run, and if it finds errors look to see if there is a y at the end...if there is press y.

---

### Post by manumahajan on 2006-07-10
Thanks for the useful advice.

I ran fsck. It found hundreds of errors and all of them had a 'y' option. most of them talked about cross linking of inodes( i have no idea what that means).

The good thing is that now i can boot into my system and gnome seems to be functioning properly but I noticed that some software have become corrupt. For example the update manager crashes after boot. Also i have lost data from at least one folder. I had a working installation of mysql 5 and a lot of files have from that directory have disappeared and Im unable to run the database server now. I do have backups so it is not a problem but i need to know the cause of the damage.

How can I find out if there is any physical damage to my harddisk and if there are any bad sectors... say, something like scandisk in windows...

---

### Post by RAOF on 2006-07-10
The cause of the data loss is almost certainly not properly unmounting the drive.  If you always shut down your system using the "Shut Down" button, this shouldn't happen.  If you turn off your system (or reboot it, for that matter) without doing that, the file system may end up in an inconsistent state, like you found.  This also happens when your system completely locks up.

Basically, it's generally caused by the system not finishing to write to the disc before it gets turned off/restarted.  Because linux tends to aggressively cache reads/writes in memory rather than going to the actual hard disc, this can happen long after the actual write request has gone thorugh.

---

### Post by RavenOfOdin on 2006-07-10
If your hard drive manufacturer distributes a hard disk checker this would be a good thing to get as well. Put it on a floppy and load it at boot time.

---

### Post by manumahajan on 2006-07-11
> **RAOF said:**
> Basically, it's generally caused by the system not finishing to write to the disc before it gets turned off/restarted.  Because linux tends to aggressively cache reads/writes in memory rather than going to the actual hard disc, this can happen long after the actual write request has gone thorugh.

I think I have understood what the cause of the problem might have been. Breezy didn't support mysql 5 install using apt-get so I installed it from a binary and used to manually start and shutdown the server from the command line. Although i always shutdown the computer it is possible that sometimes i would have not remembered to shutdown mysql before shutting down my computer and maybe that explains why mysql got corrupted.

Thanks for the help.

---

