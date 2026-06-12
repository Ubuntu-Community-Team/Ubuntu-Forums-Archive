---
title: "Move select app setting directories out of /home?"
date: 2007-08-29
forum: General Help
---

### Post by clove on 2007-08-29
I would like to relocate certain application settings directories (the hidden directories that reside in /home by default) to another directory.  The reason is that many apps store usernames and passwords in plain text in these directories and I would like to move these into my truecrypt container, so they are available for the app to use after I mount the truecrypt container.

I don't want to change the default directory away from /home, but rather pick and choose which app directories go elsewhere.

I know the proper way to go about this is to encrypt the entire /home partition and have it mount during login, but I found this task next to impossible, so I gave up and created a 100gb Truecrypt file that I mount after login, which creates a subdirectory under /home with my personal files.

Is this possible?

Thanks.

---

### Post by be4truth on 2007-08-30
It looks to me that you are fairly new to Linux. I don't recommend that you change the standard Ubuntu setup until you know what you do. I guess you will have quite some problems afterwards as the Operating system looks for the programs and config files in standard locations. To move the whole home directory is something commonly done but to part it .... I wouldn't do that as a beginner.

---

### Post by bmorency on 2007-08-30
how about making a sym link? maybe you can make it point to the folder where the data actually is?

```
ln -s /home/user/.appname /home/user/encrypted_folder
```

replace the encrypted folder path with the real one.

---

### Post by clove on 2007-08-30
> how about making a sym link? maybe you can make it point to the folder where the data actually is?

Thank you!!! This is exactly what I was looking for.  Except I believe you have it flip-flopped.  The way I did it was first move the app directory over to the encrypted container, and then make the sym link to that:

```
ln -s /home/user/encrypted_dir/.appname /home/user
```

Now, when I mount my truecrypt container, all the app setting directories appear as links and everything runs perfectly, when I dismount the encrypted container, there's no trace of anything. (Only problem is if I forget to mount the truecrypt container and start one of the apps, it will create a new directory because it thinks it's being run for the first time.)

I really didn't like the idea of all my login usernames and passwords floating around in plain text on a laptop that could easily be stolen.  Now everything will be nice and safe.

Also, I found that libcrypt-simple works nicely to encrypt login information for apps like Checkgmail.

---

