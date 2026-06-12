---
title: "Messed up permissions to a directory, please help"
date: 2018-06-29
forum: General Help
---

### Post by chuckc1981 on 2018-06-29
Hello,

I was playing around with permissions and I messed up permissions to my rancid directory.  I these two commands caused rancid to stop working\lost access.

I was trying to give read only access to all users, however this caused clogin to stop working-
sudo chmod -R ugo+r /var/lib/rancid

 I read that this would fix my previous error but it broke it so that I lost all access now-
 sudo chmod 600 /var/lib/rancid


How can I give just my rancid user owner permissions to this directory and everything under it?  I've tried using chown with no luck yet.
/var/lib/rancid

This is for 
Description:    Ubuntu 16.04.1 LTS

Thanks,
Chuck

---

### Post by TheFu on 2018-06-29
Please post the output for **ls -al /var/lib/rancid** using "code tags" so it is readable.  The directories and a few representative files are required to help.

```
sudo chmod 600 /var/lib/rancid 

```will definitely break things.
BTW, that is an example of what code tags should look like, so please be certain that is what you get.

**But first, you'll need to **
```
sudo chmod a+x /var/lib/rancid 

``` to get the directory listing to work.  Directories **must** have execute permissions to be entered and read permissions for files inside to be viewed.

Basic permissions stuff. Could it be time for a refresher on permissions?

---

### Post by chuckc1981 on 2018-06-29
```
chuck@observium:/var$  ls -al /var/lib/rancid
ls: cannot access '/var/lib/rancid/downreport': Permission denied
ls: cannot access '/var/lib/rancid/.nano': Permission denied
ls: cannot access '/var/lib/rancid/.cloginrc': Permission denied
ls: cannot access '/var/lib/rancid/.sudo_as_admin_successful': Permission denied
ls: cannot access '/var/lib/rancid/logs': Permission denied
ls: cannot access '/var/lib/rancid/rtrfilter': Permission denied
ls: cannot access '/var/lib/rancid/bin': Permission denied
ls: cannot access '/var/lib/rancid/.cache': Permission denied
ls: cannot access '/var/lib/rancid/.': Permission denied
ls: cannot access '/var/lib/rancid/?': Permission denied
ls: cannot access '/var/lib/rancid/observium': Permission denied
ls: cannot access '/var/lib/rancid/.subversion': Permission denied
ls: cannot access '/var/lib/rancid/.config': Permission denied
ls: cannot access '/var/lib/rancid/.ssh': Permission denied
ls: cannot access '/var/lib/rancid/rancid-cvspurge': Permission denied
ls: cannot access '/var/lib/rancid/getipacctg': Permission denied
ls: cannot access '/var/lib/rancid/..': Permission denied
ls: cannot access '/var/lib/rancid/.bash_history': Permission denied
ls: cannot access '/var/lib/rancid/SVN': Permission denied
total 0
d????????? ? ? ? ?            ? ?
d????????? ? ? ? ?            ? .
d????????? ? ? ? ?            ? ..
-????????? ? ? ? ?            ? .bash_history
l????????? ? ? ? ?            ? bin
d????????? ? ? ? ?            ? .cache
-????????? ? ? ? ?            ? .cloginrc
d????????? ? ? ? ?            ? .config
-????????? ? ? ? ?            ? downreport
-????????? ? ? ? ?            ? getipacctg
l????????? ? ? ? ?            ? logs
d????????? ? ? ? ?            ? .nano
d????????? ? ? ? ?            ? observium
-????????? ? ? ? ?            ? rancid-cvspurge
-????????? ? ? ? ?            ? rtrfilter
d????????? ? ? ? ?            ? .ssh
d????????? ? ? ? ?            ? .subversion
-????????? ? ? ? ?            ? .sudo_as_admin_successful
d????????? ? ? ? ?            ? SVN

```

After running the new chmod command-

```

chuck@observium:/var$ sudo chmod a+x /var/lib/rancid
[sudo] password for chuck:
chuck@observium:/var$ ls -al /var/lib/rancid
total 84
drwxrwxrwx  2 rancid rancid  4096 Sep 15  2016 ?
drwxrwxrwx 10 rancid rancid  4096 Jun 27 10:26 .
drwxr-xr-x 51 root   root    4096 Sep 15  2016 ..
-rw-rw-rw-  1 rancid rancid 14687 Jun 29 11:05 .bash_history
lrwxrwxrwx  1 rancid rancid    19 Feb  7  2016 bin -> /usr/lib/rancid/bin
drwxrw-rw-  2 rancid rancid  4096 May  8  2017 .cache
-rw-rw-rw-  1 rancid rancid   886 Jun 21 16:21 .cloginrc
drwxrw-rw-  3 rancid rancid  4096 Apr 19  2017 .config
-rwxrwxrwx  1 rancid rancid  3739 Feb  7  2016 downreport
-rwxrwxrwx  1 rancid rancid  5185 Feb  7  2016 getipacctg
lrwxrwxrwx  1 rancid rancid    16 Feb  7  2016 logs -> ../../log/rancid
drwxrwxrwx  2 rancid rancid  4096 Sep 15  2016 .nano
drwxrwxrw-  4 rancid rancid  4096 Jun 29 11:01 observium
-rwxrwxrwx  1 rancid rancid  3232 Feb  7  2016 rancid-cvspurge
-rwxrwxrwx  1 rancid rancid  5864 Feb  7  2016 rtrfilter
drwxrwxrwx  2 rancid rancid  4096 May  1  2017 .ssh
drwxrwxrw-  3 rancid rancid  4096 Sep 15  2016 .subversion
-rw-rw-rw-  1 rancid rancid     0 Sep 15  2016 .sudo_as_admin_successful
drwxrwxrw-  6 rancid rancid  4096 Sep 15  2016 SVN


```

---

### Post by chuckc1981 on 2018-06-29
I'm getting this now in my cloginrc log, how can I remove world read\write from /var/lib/rancid?  Thank you for the help so far

```

10.24.0.69 clogin error: Error: /var/lib/rancid/.cloginrc must not be world readable/writable

```

---

### Post by deadflowr on 2018-06-29
Remove world from rw like
```
sudo chmod o-rw /var/lib/rancid/.cloginrc
```

I don't think you need to set it for the whole directory.
Just that one file.

---

### Post by chuckc1981 on 2018-06-29
Thank you, I think I understand the permissions now too...this is how I think of it

sudo chmod UserGroupOther+-ReadWriteExecute FilenameOrDirectory

---

### Post by TheFu on 2018-06-29
```
drwxrwxrwx 10 rancid rancid  4096 Jun 27 10:26 .
```

That is just wrong. Anyone on the machine can delete every file inside that directory. That is **never** a good idea for logs.
If you can't restore the permissions from a backup, I'd remove-purge rancid and reinstall. Permissions are the first line for a secure system.  Often, there are important details that need to NOT be shared with the world inside log files.

Next time, make some notes or just tar the directory to a temp location so you can keep track of owner, group and permissions BEFORE screwing around with permissions.  This works for config files too.  Backups have 1001 uses. Always a good idea.

---

### Post by deadflowr on 2018-06-29
>  I'd remove-purge rancid and reinstall
That would make life easier, starting from scratch.

(I should have scrolled up. I missed the output post.)

---

### Post by TheFu on 2018-06-29
> **deadflowr said:**
> That would make life easier, starting from scratch.

(I should have scrolled up. I missed the output post.)

I think the useful output was added after-the-fact.  Partially my fault because I didn't provide the commands in order. Just said to run *this* cmd first, but that was below the other commands. I should try to post more sequentially.

---

