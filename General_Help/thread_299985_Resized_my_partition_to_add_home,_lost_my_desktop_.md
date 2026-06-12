---
title: "Resized my partition to add /home, lost my desktop settings and a few other things"
date: 2006-11-15
forum: General Help
---

### Post by trmiv on 2006-11-15
So I followed the pyschocats tutorial on using gparted to resize my partition and add a /home partition.  It appears to have worked for the most part, but when I boot into ubuntu and log in, instead of seeing my customized gnome desktop (different window borders, icons, background, cursors, etc),I see the default ubuntu one. Also the keyring manager acts like it's never been setup when I try to access my wireless.  Was there something that didn't get copied over that I need to move?

So then I followed the instructions at the end of the psychocats tutorial on what to do when the process doesn't work.  When I do that and boot I get an error that says "Your home directory is listed as `/home/myusername' but it does not appear to exist.  Do you want to log in with the / (root) directory as your home directory?

---

### Post by dcstar on 2006-11-15
> **trmiv said:**
> So I followed the pyschocats tutorial on using gparted to resize my partition and add a /home partition.  It appears to have worked for the most part, but when I boot into ubuntu and log in, instead of seeing my customized gnome desktop (different window borders, icons, background, cursors, etc),I see the default ubuntu one. Also the keyring manager acts like it's never been setup when I try to access my wireless.  Was there something that didn't get copied over that I need to move?

In your old home directory there will be lots of hidden files, unless you copied these then you may have problems (like you described).

---

### Post by trmiv on 2006-11-15
I followed [this tutorial]("http://www.psychocats.net/ubuntu/separatehome") to the letter.  Doesn't that copy all the hidden files?

---

### Post by koenn on 2006-11-15
I suspect that your user account does not have sufficient permissions to the /home directory and/or to /home/*username* and the files therein.

In your file browser, rightclick  /home/*yourusername*, select properties -> permissions. You should have
owner : your username
group : your user name
owner : read, write, execute

---

### Post by trmiv on 2006-11-15
I'll take a look at that when I get home.  I ended up just recreating my desktop though.  Another thing that was gone was my Firefox settings and favorites.  But my files were still on the desktop and in my home directory.

---

### Post by trmiv on 2006-11-16
I tried to change the permissions on the folder, I must have messed it up because now I'm really screwed.  When I try to log in now, I get an error saying "Your session only lasted less than 10 seconds" and it allows me to view an error log.  The log says:

trying to create local folder /home/ted/.kde: Permission Denied

Then there are a few more lines and this:

(gnome-session:4998): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission Denied
Could not create per-user gnome configuration directory `/home/ted/.gnome2/`:Permission Denied


Am I better of just reinstalling?

---

### Post by trmiv on 2006-11-16
Help. ](*,)

---

### Post by koenn on 2006-11-16
boot to recovery mode (from grub boot menu)
run the following commands:
```

sudo su
cd /home
ls -al

```
post the result and we'll have a look.

---

### Post by trmiv on 2006-11-16
Here's what it says:

```

drwxr-xr-x 3 root root 4096 2006-11-15 00:05 .
drwxr-xr-x 22 root root 4096 2006-11-14 22:29 ..
drw-r--r-- 36 ted ted 4096 2006-11-15 21:31 ted

```

---

### Post by koenn on 2006-11-17
assuming your username is ted, i find a few things strange:
1- user ted has no x (execute) permission on /home/ted. you must have at least execute permission on a directory to switch ( cd ) to it, so maybe the missing x is enough to keep you or other programs (gnome, kde) out of your home, which can make them crash or fail
2- the group "ted" has only 'read'. On my, prettyu standard, ubuntu, that would be read and execute. 

You can change this by executing (as root / with sudo)
```

chmod 771 /home/ted 
```
Then, do
```
cd /home
ls -al
``` again; you should see something like

```

**drwxrwx--x **36 ted ted 4096 2006-11-15 21:31 ted 
```

Then reboot and log on as ted, see if it works.

---

### Post by trmiv on 2006-11-17
When I do that I am able to log in, but when I do I get an error that says:

User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  Users $HOME directory myst be owned by user and not writable by other users.

---

### Post by trmiv on 2006-11-17
Fixed it!  I did this:

```

cd /home/ted
chown ted:ted .dmrc
chmod 600 .dmrc

```

---

### Post by trmiv on 2006-11-17
I hate bumping my own threads, but I'm not out of the woods yet.  So now I can log in, but I have another problem as seen in [this thread]("http://ubuntuforums.org/showthread.php?t=301954").  Also, I can't do things like save files to my own desktop, save various settings, when I try to download add-ons with firefox, they won't install.

---

### Post by Wordlet on 2006-11-17
I think you might have the /home partition mounting as read only System settings - > Advanced - > Disk and file systems and make sure your name is there and it's not mounted as read only.

This will probably also fix the other problems...if it is the source.

---

### Post by trmiv on 2006-11-17
Not to sound completely dense, but I can't find this: System settings - > Advanced - > Disk and file systems

Also, I created another user and it has none of these problems.  If push comes to shove I can use that, but I'd really like to get "ted" working correctly because I did a lot of work to get the settings, fonts, etc the way I like them.

---

### Post by Wordlet on 2006-11-17
It's in the K Menu near the bottom "System Settings" it should be a picture of a hard drive..and if you're on edgy you need to click 'Advanced' near the top to get to the proper menu.

---

### Post by trmiv on 2006-11-17
Oh, this is gnome not KDE.  Probably why I'm not seeing it. :D  Anyway I can check the same thing in gnome?

---

### Post by RFScheer on 2006-11-17
Change your ownership for all files and dirs in your /home by 

sudo chown -R ted:ted /home

If that doesn't do it then go a bit further and change permissions to

sudo chmod -R 755 /home

and let us know.

I'm uneasy with changing permission like that on all files in your /home directory.  You might want to use 700 instead to keep the whole world out.  But the important thing is does that help?

---

### Post by trmiv on 2006-11-17
The second command did it!  I had actually already done:
sudo chmod 755 /home but I didn't do the -R.  Apparently that was the key.  Thank you!

---

### Post by Wordlet on 2006-11-18
Just for future reference..the -R affected every file in the home directory..instead of just home. R = recursive.

---

