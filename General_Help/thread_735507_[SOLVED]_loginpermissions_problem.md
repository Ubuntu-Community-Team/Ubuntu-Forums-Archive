---
title: "[SOLVED] login/permissions problem"
date: 2008-03-25
forum: General Help
---

### Post by fiat42lux on 2008-03-25
First I ran out of space on my root partition. After panicking for a while I figured out what was the problem and cleared some space by uninstalling some non-critical packages. Now $ df reports 183M available on the root partition. I've been running just fine with less space than that for some time now, so I have good reason to believe it should suffice.
When I start up and login normally now, the "GDM could not write to your authorisation file" message appears no longer -- yay. However:
> Your session only lasted less than ten seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix the problem.

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "fiat42lux"
/etc/gdm/Xsession: Beginning session setup...

(gnome-session:5700): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
could not create per-user gnome configuration directory "/home/fiat42lux/.gnome2/": Permission denied
Starting in recovery mode, I run: 
```
root@Elbeest:/# chmod -R 644 /home/fiat42lux
login
Elbeest login: fiat42lux
Password:
fiat42lux@Elbeest:/$ cd /home/fiat42lux
-bash: cd: /home/fiat42lux: Permission denied
fiat42lux@Elbeest:/$
```
Now, I r still basically noob, but that last behavior strikes me as rather strange -- I just set the permissions as root, and yet I have none. It seems likely to me that the login problem and the problem reading my home directory are one and the same, but with chmod seemingly on strike, I'm at my wits' and resources' end. 
Anyone have a hint for me? I would appreciate it.

(I'm running Feisty.)

---

### Post by pointone on 2008-03-25
"chmod 644" will remove the execute bit from the directory, which prevents the user from stepping into it. chmod is working perfectly here, actually! You want "chmod 744", I believe. You should still be able to read/write files in the directory (as in "cat /home/fiat42lux/testfile"). The execute bit is what matters to "cd".

However, the original problem was likely insufficient disk space. Even if it worked flawlessly for some time, you really ought to have more than 200 MB free. At least 10% free of your total partition size if generally recommended, as it keeps the filesystem in a much better state. Low free space = all sorts of wacky errors.

---

### Post by fiat42lux on 2008-03-26
Aha!
That did it, thanks very much. I probably should have noticed that, but I didn't know cd requires x instead of r... the more you know. What threw me off right at the start was that I was actually told by one of the previous login error messages (from when the disk was full) to set exactly those permissions:
> Your $home/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.
It seems to me Ubuntu wasn't being entirely honest with me there... :p
Now to address the space problem... Thanks again for the tip, pointone.

---

