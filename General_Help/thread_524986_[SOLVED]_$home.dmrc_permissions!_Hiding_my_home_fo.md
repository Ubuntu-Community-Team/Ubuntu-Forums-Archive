---
title: "[SOLVED] $home/.dmrc permissions?! Hiding my home folder..."
date: 2007-08-13
forum: General Help
---

### Post by Kilgore_Trout on 2007-08-13
If I were to have, say, done a recursive permission change to my home directory because I didn't know what I was doing :oops:... is there a way to change them back to what they were? 

To make a short story long, I was using the Feisty LiveCD and foolishly changed the owner of /home and my user directory to "Ubuntu Live CD User".

After rebooting into my system, I was greeted with a $home/.dmrc error message that said that the permissions for /home needed to be 644.

I remembered that my user directory was originally set for owner and group "1000", so i did:

```
sudo chmod -R 644 /home
```

and

```
sudo chmod -R 1000 /home/mfrac
```

Reboot, and I get another error message related to $home/.dmrc and I believe an .ice file? (I'll have to check when I get home).

Is there a way to undo what I did?

Thanks

---

### Post by Bachstelze on 2007-08-13
Moved in a new thread per user request.

---

### Post by Kilgore_Trout on 2007-08-13
Update: 

This is the message I get when I try to log in:

"Your home directory is listed as 'home/mfrac' but it does not appear to exist.  Do you want to long in with the / (root) directory as your home directory?  It is unlikely anything will work unless you use a failsafe session."

If I change the session to GNOME failsafe and accept the above message, I get: 

"Users $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writeable by other users."

After I hit OK, I get another error message stating that my GNOME session lasted less than 10 seconds.

Any ideas?

---

### Post by Kilgore_Trout on 2007-08-14
Update to update:

I tried a solution that I found in another thread for what seemed to be a similar problem.

I booted to restore mode and entered:

```
sudo chmod 644 /home/mfrac/.dmrc
sudo chown mfrac /home/mfrac/.dmrc
sudo chmod -R 755 /home/mfrac
sudo chown -R mfrac /home/mfrac
```

and no dice.  Same error messages.

Any hope to avoid a fresh install?  (This had to happen while I was trying to partition an external drive so I could backup my system. Ugh.)

---

### Post by Laplace's Daemon on 2007-08-14
I actually had this problem just yesterday.   For some reason that I cannot explain, my chown -R was moving through every /home directory, even though I was calling it only in one of my users.  This was giving me some measure of trouble with logging in to multiple accounts.  Don't know if this might be your problem, however...

You might want to go through (or post the results of, if you don't mind the internet being to see the contents of your home directory) an ls -al /home/mfrac/ and make sure that everything has the proper ownership (mfrac for user and group for most files) and is set to 644 or whatever it needs to be set to.

---

### Post by Kilgore_Trout on 2007-08-15
I did:

```
ls -al /home/mfrac
```

and although I couldn't figure out how to scroll up in restore mode, all of the files that I could see had "-rwxr-xr-x" permissions.  From what I gather, this is the same as "755". :-?

Also strange... when I boot from the Live CD and open GParted, it automatically mounts all of the drives/partitions in the system.  In my /home partition, the "mfrac" directory shows up as a file instead of a folder.  Could this be the problem?  Is there a way to change it to a  folder? :?:

---

### Post by Laplace's Daemon on 2007-08-17
Looking over your first post again, I think I might see the (or at least a) problem.  When you originally did```
sudo chmod -R 644 /home
```you took away execute permission for everything in /home, which means that nothing has permission to list the contents of your /home directory (and maybe other things too, I'm not too sure on the specifics).  Let's test this out to make sure I'm right.  Do```
ls -l /
```This should return the permissions "drw-r--r--" for /home, which is 644.  If this is the case, run```
sudo chmod a+x /home
```to give everyone execute permission for that directory.  Also make sure that both owner and group of /home are root.  If not, run```
sudo chown root:root /home
```Make sure not to do either of these recursively.

If I am wrong about the permissions on /home, then we'll have to try something else.

Next let's move up the tree a bit.  After your attempts to fix everything in your third post, all of your permession settings will be all messed up (I did this once two and had to find a (slow) way out).  First, do```
ls -l /home
``` and make sure that all of the uses directories are set to "drwxr-xr-x".  If not, use "sudo chmod 755 mfrac" or any other user names you have.  Also make sure that both owner and group are set correctly.

From your last post, it looks like all your files now have execute permission, which you don't want.  I've been reading the man page for chmod and doing a little experimenting and it looks like your best bet will be to issue the commands:```
sudo chmod -R a-x+X /home/dfrac/*
sudo chmod -R a-x+X /home/dfrac/.*
```In my experience, simply using the wildcard (*) doesn't pick up the hidden files, so you will have to issue both commands.  Now do ```
ls -al /home/mfrac/
```to make sure it all worked.  Directories should have "drwxr-xr-x" and files should have "-rw-r--r--".  By the way, you can scroll up in a terminal by pressing Shift+Page Up, and down with Shift+page Down.  Alternatively, you could pipe the output into less with ```
ls -al | less
```or, if you have color enabled and it comes out ugly in less```
ls -al --color=never | less
```

I hope that at least some of this is helpful.

---

### Post by Kilgore_Trout on 2007-08-17
SUCCESS!!! 

Thanks so much, Daemon.

i logged into the failsafe terminal and ran 

```
ls -l /
```

The permissions for home came up as drw-r--r-- 

So I did what you said and ran

```
sudo chmod a+x /home
```

and

```
sudo chown root:root /home
```

Tried to log back in, and BINGO.  I'm in.

Thanks again.

---

