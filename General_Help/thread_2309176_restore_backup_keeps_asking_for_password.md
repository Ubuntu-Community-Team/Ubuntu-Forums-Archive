---
title: "restore backup keeps asking for password"
date: 2016-01-08
forum: General Help
---

### Post by gavin15 on 2016-01-08
My external backup drive, has password encryption and now trying to backup to a new laptop with ubuntu already installed and Deja Dup as standard.  I'm sure I tested and carefully noted down the password.  When I go to restore it asks for the encrypted password, but when I enter it, the screen keeps requesting as if it's not correct.  Here is visual the stage 5 of backup 
[http://www.linuxlookup.com/howto/backup_and_restore_ubuntu_1404_lts_desktop](http://www.linuxlookup.com/howto/backup_and_restore_ubuntu_1404_lts_desktop)

I wondered if there's is some permissions needed for the folder I'm restoring the backup to?

---

### Post by ajgreeny on 2016-01-08
> **gavin15 said:**
> My external backup drive, has password encryption and now trying to backup to a new laptop with ubuntu already installed and Deja Dup as standard.  I'm sure I tested and carefully noted down the password.  When I go to restore it asks for the encrypted password, but when I enter it, the screen keeps requesting as if it's not correct.  Here is visual the stage 5 of backup 
[http://www.linuxlookup.com/howto/backup_and_restore_ubuntu_1404_lts_desktop](http://www.linuxlookup.com/howto/backup_and_restore_ubuntu_1404_lts_desktop)

[COLOR="#FF0000"]I wondered if there's is some permissions needed for the folder I'm restoring the backup to?[/COLOR]

[COLOR="#FF0000"]What folder is that?  [/COLOR]

We can not give you an answer if we don't know the destination folder, but as a general rule, you and deja-dup run by you, should be able to write to any folder in your home, but not to anything in the root filesystem.  To write to the root filesystem you will need your normal user password that you use for sudo commands.

My only real uncertainty, is that I have never used deja-dup so my answer is from first principles, not personal experience.

---

