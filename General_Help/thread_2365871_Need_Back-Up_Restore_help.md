---
title: "Need Back-Up Restore help"
date: 2017-07-11
forum: General Help
---

### Post by aviator1 on 2017-07-11
Dear Friends:

I spent the last week here with the help of CatKiller, 1Fallen, and a few others fighting a never ending battle with logon issues. I ended up doing a clean re-install and all is well.

However, I used deja-dup to back-up things, and now cannot seem to retrieve anything. 

Needless to say, I miss all my years of bookmarks, and email addresses.

Anyone have any hints, or other methods. I backed up to an external drive.

Thanks for any help.

Regards

---

### Post by deadflowr on 2017-07-11
Is the external drive properly mounted?
And is the storage location properly set in Backups >> Storage Location?

Also, double check the external drive that it actually has the backups on it.
(I'd open the Files program and navigate to the drive (in the left panel area) and check it to see.)

And,
Did you set a backup password?
(And do you remember the password?)

Right now we're just tossing pasta against the wall and trying to see what sticks.

---

### Post by aviator1 on 2017-07-11
> **deadflowr said:**
> Is the external drive properly mounted?
And is the storage location properly set in Backups >> Storage Location?

Also, double check the external drive that it actually has the backups on it.
(I'd open the Files program and navigate to the drive (in the left panel area) and check it to see.)

And,
Did you set a backup password?
(And do you remember the password?)

Right now we're just tossing pasta against the wall and trying to see what sticks.

Do not understand what "Properly Mounted" means. Have seen it here, but just do not know. It is connected and I can navigate to it and in it.

Interestingly (to me) is that I can type Backup in the search bar and I get a lot of backup folders. Some empty and some with backups in them. However, when I just navigate to the drive, I do not see them.

When I open the backup icon, I get a selection for the external drive and a space to add the folder. I type int he folder access info media/dave/2 TB External/ALL/Backup-1 using correct case. I get an error that says "No Backups to Restore"

I believe they are there, I'm just not doing something right to get to them. I did set a password and know it.

Thank for any assistance

---

### Post by aviator1 on 2017-07-11
Have to be off for about an hour.

---

### Post by deadflowr on 2017-07-11
Is there really a space between 2 and TB (and TB and External), if so, try adding an escape like
```
/media/dave/2\ TB\ External/ALL/Backup-1
```
I think if it has spaces, then it might only be seeing something called /media/dave/2

---

### Post by aviator1 on 2017-07-11
> **deadflowr said:**
> Is there really a space between 2 and TB (and TB and External), if so, try adding an escape like
```
/media/dave/2\ TB\ External/ALL/Backup-1
```
I think if it has spaces, then it might only be seeing something called /media/dave/2

Yes, there is a space. I tried it without a space with no luck.

However, I am now back to having a boot problem that I had posted about earlier.

Still need to solve the backup thing.

I tried /media/dave/2\ TB\ External/ALL/Backup-1, but got Error creating directory: Permission denied 

Thanks for your help.

---

### Post by aviator1 on 2017-07-11
The space is there

```
dave@dave-desktop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.5M  1.6G   1% /run
/dev/sda2       219G  5.4G  202G   3% /
tmpfs           7.8G  2.0M  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda1       511M  3.4M  508M   1% /boot/efi
tmpfs           1.6G   64K  1.6G   1% /run/user/1000
/dev/sdd1        30G  2.1G   28G   7% /media/dave/Lexar
/dev/sdc1       917G  708G  163G  82% /media/dave/2TB External
dave@dave-desktop:~$ 


```

---

### Post by deadflowr on 2017-07-11
Can you use the navigate way to set the folder?
(In the Storage Location clicking on the Folder button and going to the open folder dialog box left pane should show the 2TB External drive.
Then clicking on the drive should show the Backups folder, when you click on that the main windows area should get populated with the backup folders and files.
(They should all read something like duplicity-blah-blah-blah; duplicity is the actual backup utility that is used, deja-dup is just a frontend for that)

If all that has been done, another thing I thought about was if the backups were saved as your user or under a different name?
(Example would be if you ran the backup as root, then maybe root owns the backups, then you'd probably need to run as root to restore them, and the same may be said if done as another user;
like if you backed up as joe and now you're dave. Or something like that.
If that makes sense...
convoluted-ly)

(I hope we are not going in circles)

---

### Post by aviator1 on 2017-07-12
> **deadflowr said:**
> Can you use the navigate way to set the folder?
(In the Storage Location clicking on the Folder button and going to the open folder dialog box left pane should show the 2TB External drive.
Then clicking on the drive should show the Backups folder, when you click on that the main windows area should get populated with the backup folders and files.
(They should all read something like duplicity-blah-blah-blah; duplicity is the actual backup utility that is used, deja-dup is just a frontend for that)

If all that has been done, another thing I thought about was if the backups were saved as your user or under a different name?
(Example would be if you ran the backup as root, then maybe root owns the backups, then you'd probably need to run as root to restore them, and the same may be said if done as another user;
like if you backed up as joe and now you're dave. Or something like that.
If that makes sense...
convoluted-ly)

(I hope we are not going in circles)

I still have a boot problem from another thread that we thought was fixed. Let me get that done first, and I will return to this thread.

Thanks very much for your assistance.

Regards.

---

### Post by oldfred on 2017-07-12
Just a comment.
Do not use spaces in labels, mount points or anywhere you use Linux.
I suggest under_score, CamelCase, or justaname, but spaces have to be delimited or quoted to work correctly and invariable cause issues.

---

### Post by HermanAB on 2017-07-13
A space is a delimiter.

If you really have to use spaces, then use quotes.

Chances are that your backups are/were on a different drive/directory because of that.

---

