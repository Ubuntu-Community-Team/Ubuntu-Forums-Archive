---
title: "ecryptfs and backup from cron as root"
date: 2013-01-02
forum: General Help
---

### Post by finite9 on 2013-01-02
I encrypted my home directory during a 12.10 install on my home server but ive having trouble figuring out the best way to backup my home directory in a cron job.

the cron job is run as root, and im not logged in so my home directory is not decrypted during the cron job.

Is there a way to make this work, either by scripting in the passphrase on the command line (yes im aware its unsecure) with something like ecryptfs-mount-private or is there a better way to handel this?

---

### Post by thnewguy on 2013-01-02
If you put your password in a script or on the command line then there really isn't any point in encrypting your files. It would be about the same as installing a lock on your front door and leaving the key in the lock.

There are a few things I would try in your situation, depending on your home set up.

1. Drop the encryption on your server. This makes things easy.
2. Try running your backup script as your regular user. Regular users can have their own cron jobs, though I'm not sure if running a job as a regular user will automatically unencrypt your files or not. Might be worth a try.
3. Create an image of your entire /home partition for your backup rather than worrying about specific files. This will increase the size & time involved, but it will insure a complete copy of all of your users' folders are backuped up and still encrypted.
4. You didn't say where your files are backed up to. Can you have another machine, like a laptop, login to your server as you and perform the backup on scheduled basis? Something like "ssh myserver run-backup" placed in a cron job on a client machine will work for some cases.

---

### Post by finite9 on 2013-01-03
I put 

```
su finite9 -c ""
```

around the cron job entry and this unlocks my encrypted home, unlike ssh which doesn't automatically.  working now.

---

