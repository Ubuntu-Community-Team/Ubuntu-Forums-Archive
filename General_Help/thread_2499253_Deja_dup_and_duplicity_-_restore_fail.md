---
title: "Deja dup and duplicity - restore fail"
date: 2024-07-20
forum: General Help
---

### Post by bejibe on 2024-07-20
New and ignorant Ubuntu user. Hardly able to use a command line.

 I had an old PC that I installed with Ubuntu version 22.04 LTS. I  used the Ubuntu proposed backup tool DEJA DUP to start backing up a few  selected files. A few weeks later, the old PC crashed. Bye bye.

 I am now using a PC that I boot Windows on, and sometime on an external Drive for Ubuntu, same version as above. I want TO RESTORE my one year old arquive

 I have tried a full backup with DEJA-DUP tool and it crashes. I also have tried a full backup with a SU command line

 > sudo duplicity restore file:///PathToBackupDIR PathToDestinationDir
 
and it crashes with exactly the same error message. Here it is:

 > Traceback (innermost last):
File "/usr/bin/duplicity", line 92, in <module>
with_tempdir(main)
File "/usr/bin/duplicity", line 75, in with_tempdir
fn()
File "/usr/lib/python3/dist-packages/duplicity/dup_main.py", line 1568, in main
do_backup(action)
File "/usr/lib/python3/dist-packages/duplicity/dup_main.py", line 1651, in do_backup
restore(col_stats)
File "/usr/lib/python3/dist-packages/duplicity/dup_main.py", line 736, in restore
restore_get_patched_rop_iter(col_stats)):
File "/usr/lib/python3/dist-packages/duplicity/dup_main.py", line 788, in restore_get_patched_rop_iter
file_names.append(backup_set.volume_name_dict[vol_num])
KeyError: 1
 
I don't have an older full archive, it was my first one ever done.

 If I want to restore selected files of a sub-folder from a arquive, sometime it works with DEJA-DUP for SOME files and NOT OTHER files,  sometime with the full back-up date, sometime the incremential back-up  date. it's crasy! in one same sub-folder and one back-up date, some files can  be restored, other files give error message.

 In this case, I got the message:

 > Local and Remote metadata are synchronized, no sync needed.
    Last full backup date: none
    GnuPG passphrase for decryption: 
    Traceback (innermost last):
      File "/usr/bin/duplicity", line 92, in <module>
        with_tempdir(main)
      File "/usr/bin/duplicity", line 75, in with_tempdir
        fn()
      File "/usr/lib/python3/dist-packages/duplicity/dup_main.py", line 1568, in main
        do_backup(action)
      File "/usr/lib/python3/dist-packages/duplicity/dup_main.py", line 1651, in do_backup
        restore(col_stats)
      File "/usr/lib/python3/dist-packages/duplicity/dup_main.py", line 736, in restore
        restore_get_patched_rop_iter(col_stats)):
      File "/usr/lib/python3/dist-packages/duplicity/dup_main.py", line 758, in restore_get_patched_rop_iter
        backup_chain = col_stats.get_backup_chain_at_time(time)
      File "/usr/lib/python3/dist-packages/duplicity/dup_collections.py", line 1011, in get_backup_chain_at_time
        raise CollectionsError(u"No backup chains found")
     duplicity.dup_collections.CollectionsError: No backup chains found

 ANY HELP?

---

### Post by currentshaft on 2024-07-22
What is "DEJA DUP" and how did you install it?

---

### Post by donald187 on 2024-07-22
Deja Dup (package deja-dup) is the backup program that comes automatically installed with Ubuntu.  It's a front end for Duplicity.  It's simply labeled as Backups in the applications.

---

### Post by TheFu on 2024-07-22
> **bejibe said:**
>  ANY HELP?

If the help.ubuntu.com documentation isn't sufficient, there are 50 other backup tools that you can try to see which works best for your needs. I've never used the default backup tool installed by Ubuntu.

One thing that is important to understand about all Duplicity-based backup tools is that a full backup needs to be re-run every month with versioned backups only between those full backups.  There are easier options - for certain values of "easier" depending on what you want to backup and your backup storage.  Many require native Linux file systems, so if you are backing up to NTFS or a CIFS NAS storage, then you are sorta limited / [s]screwed[/s].

Duplicity checks all the best practices for backups, so on paper, it seems like the ideal tool.  Search these forums for the number of issues people using dejaDup or duplicity or Duplicati have when it is time to restore.  Backups that cannot be restored are just wasted time and space.

---

### Post by donald187 on 2024-07-23
I used to get errors like that sometimes when using Duplicity on a new install.  It was always something I had done wrong.  I used to use Deja Dup and there's little configuration.  Perhaps the computer name is different and that might do it.  I seem to recall a computer name setting in Deja Dup.  But this was a number of years ago that I used it and the interface has changed since then.

---

