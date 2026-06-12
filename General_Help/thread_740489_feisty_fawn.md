---
title: "feisty fawn"
date: 2008-03-30
forum: General Help
---

### Post by Jeenyus on 2008-03-30
I use Feisty Fawn and the other day I got an error message saying that I was out of disk space and I accidentally ignored it.  The next time I went to log on I got this message "GDM could not write to your authorization file.  This could mean that you are out of disk space or that your home directory could not be opened for writing.  In any case it is not possible to log in, please contact your system administrator."

The only thing I can think of that would have filled up my disk space is that when I download torrents, I copy the files to a shared FAT32 partition where I keep my media files for XP and Ubuntu, then delete them off the Ubuntu partition.  If somehow deleting them doesn't completely remove the files then they easily could have filled up the space.

Any advice or solutions would be greatly appreciated, I haven't tried playing around with it too much.  Thank you.

Also sorry for the incredibly vague post title, it was an accident.

---

### Post by Fixman on 2008-03-30
Go to options->sessions (or something *like* that), and select failsafe terminal. Then, log in and write:

```

rm -r .Trash
mkdir .Trash

```

If it still gives you an error, you can try

```

cd ..
sudo chmod 777 $USER

```

---

### Post by Jeenyus on 2008-03-31
Still no luck, it wouldn't let me log into the Failsafe Terminal so I tried booting into recovery mode and typing the commands into that Terminal-like line and it said that the .Trash directory did not exist when i tried to delete it.

Any other suggestions?  Thanks much!

---

