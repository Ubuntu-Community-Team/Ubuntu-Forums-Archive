---
title: "Setting up So called &lt;-- Cron Jobs --&gt;"
date: 2013-06-03
forum: General Help
---

### Post by chetanmadaan on 2013-06-03
Hi -

i have always used Cpanel for hosting our websites and setting up cron using using the Cpanel interface is so easy. I am starting to use and explore ubuntu... there are some SSH commands i would like to run on and hourly or 30 mins basis.

is there a way to do this using and interface or command line.

Here is what i am trying to do...

on a website... whenever a new file is uploaded via web browser... by default it's owned by apache or so called www-data. I am trying to CHOWN them back to the user's directory they are in... so that the user can edit those files using FTP.

**Make sense?**

---

### Post by Lars Noodén on 2013-06-03
Cron is rather simple to set up if once you understand the configuration file.  The good news is that it is a plain tab-delimited text file with no bells or whistles:

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

But if you are watching a single directory or two for changes you might be interested in inotify instead.  That is a little harder to figure out but will run a script or program whenever a watched directory or file changes.

---

### Post by CatKiller on 2013-06-03
Isn't there a permissions setting to define new file ownership/permissions? I don't know the details, but I remember something like that.

---

### Post by sandyd on 2013-06-03
> **CatKiller said:**
> Isn't there a permissions setting to define new file ownership/permissions? I don't know the details, but I remember something like that.

GID/UID sticky bit

For example, if you set a folder to be owned by sandyd:sandyd

```
chmod 4744 /path/to/file
```
Will cause new files/directories in the folder to be created with *owner*:sandyd, where *owner* is the creator of the file/directory

```
chmod 2744 /path/to/file
```
Will cause new files/directories in the folder to be created with sandyd:*group*, where *group* is the group of the user that created the file/directory

---

### Post by capscrew on 2013-06-03
> **sandyd said:**
> GID/UID sticky bit

For example, if you set a folder to be owned by sandyd:sandyd

```
chmod +t /path/to/file
```
Will make the group "sticky" which will cause new files/directories in the folder to be created with *owner*:sandyd, where *owner* is the creator of the file/directory

```
chmod g+s /path/to/file
```
Will make the owner "sticky" which will cause new files/directories in the folder to be created with sandyd:*group*, where *group* is the group of the user that created the file/directory

The sticky bit doesn't create inheritance.  The SGID and SUID bits do that.  The sticky bit is to prevent deletion of your files in a world writable directory.  See [[COLOR="#FF1100"]https://help.ubuntu.com/community/FilePermissions[/COLOR]]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by sandyd on 2013-06-03
> **capscrew said:**
> The sticky bit doesn't create inheritance.  The SGID and SUID bits do that.  The sticky bit is to prevent deletion of your files in a world writable directory.  See [[COLOR="#FF1100"]https://help.ubuntu.com/community/FilePermissions[/COLOR]]("https://help.ubuntu.com/community/FilePermissions")

fixed

---

### Post by bab1 on 2013-06-03
> **sandyd said:**
> GID/UID sticky bit

For example, if you set a folder to be owned by sandyd:sandyd

```
chmod 4744 /path/to/file
```
Will cause new files/directories in the folder to be created with *owner*:sandyd, where *owner* is the creator of the file/directory

```
chmod 2744 /path/to/file
```
Will cause new files/directories in the folder to be created with sandyd:*group*, where *group* is the group of the user that created the file/directory

Actually on the mode 2755 forces the group to be the same group ownership as is on the directory you are in.  You do need the bits on the group and others to be 55 not 44.  This allows the user to read the contents of the directory or traverse it.  The default umask is 0002 now and that is 0775 for directories and 0664 for files.

---

### Post by chetanmadaan on 2013-06-03
I Quote!

If i make owner sandy and group sandy too... the files are not writable using any php script.

So, i make owner sandy and group www-data. it works that way... May be i am doing it wrong.

:)

---

### Post by bab1 on 2013-06-03
> **chetanmadaan said:**
> I Quote!

If i make owner sandy and group sandy too... the files are not writable using any php script.

So, i make owner sandy and group www-data. it works that way... May be i am doing it wrong.

:)

Aren't we talking about inheritance here?  You can manually change the owner and group anytime you like.  if you don't set inheritance other users will ***not*** automatically create directories and files with the same group ownership.

---

### Post by Lars Noodén on 2013-06-03
One thing to point out about setting and unsetting SGID and SUID bits is that although you can set them in octal mode (1775, 2755, etc), you can't unset them in octal mode.  In order to unset them you have to use the symbolic mode (u=rwxs,g=rwxs,o=rx).

---

### Post by Dave_L on 2013-06-03
> **Lars Noodén said:**
> ...But if you are watching a single directory or two for changes you might be interested in inotify instead.  That is a little harder to figure out but will run a script or program whenever a watched directory or file changes.

I didn't know such a thing as inotify existed. I found some packages in synaptic that provide an inotify shell interface, and figured out how to use inotifywait (from package inotify-tools) to accomplish something more simply than I had been doing with cron.

Thanks! :D

---

