---
title: "Login Error"
date: 2007-03-22
forum: General Help
---

### Post by Toksin on 2007-03-22
Hi,

I had the same problem as in this thread : [http://ubuntuforums.org/showthread.php?p=2289401](http://ubuntuforums.org/showthread.php?p=2289401) and followed the instructions in that thread to fix it.

However now when I log in it immediately logs out and says

> Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.

My ~/.xsession-errors file reads as follows:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/ :0.Xservers" -h "" -l ":0" "toksin"
/etc/gdm/Xsession: Beginning session startup...

(gnome-session:4879) : libgnomevfs-WARNING **:  Unable to create ~/.gnome2 directory: Premission denied
Could not create per-user gnome configuration directory '/home/toksin/.gnome2/' : Permission denied
```

Same thing happens when I try to log in with a failsafe session.

---

### Post by ayoli on 2007-03-22
you may try:
```
chmod -R 664 ~/gnome* 
```
edit: the code you fellow in the post you linked above is to much restrictive i think
.dmrc file wants that *others* don't be able to write your own files so 664 mode or even 750 should be enough

---

### Post by Muzik83 on 2007-03-22
Hey

It looks as if the permissions on your home directory are messed up.  The howto you looked at said the following:

chown -R $(whoami) /home/$(whoami)
chmod 644 /home/$(whoami)
chmod 644 /home/$(whoami)/.dmrc

The file which you are having problems with is your .gnome2 folder.  Try the following

sudo chown -R toksin /home/toksin
sudo chmod 700 /home/toksin/.gnome2
sudo chmod 755 /home/toksin

If this doesnt work, would you be able to paste the output from:
ls -lRa /home/

(this will show all your filenames and permissions)

---

### Post by Toksin on 2007-03-22
> **Muzik83 said:**
> Hey

It looks as if the permissions on your home directory are messed up.  The howto you looked at said the following:

chown -R $(whoami) /home/$(whoami)
chmod 644 /home/$(whoami)
chmod 644 /home/$(whoami)/.dmrc

The file which you are having problems with is your .gnome2 folder.  Try the following

sudo chown -R toksin /home/toksin
sudo chmod 700 /home/toksin/.gnome2
sudo chmod 755 /home/toksin

If this doesnt work, would you be able to paste the output from:
ls -lRa /home/

(this will show all your filenames and permissions)


That fixed me, thanks mate!

---

### Post by thingy on 2007-03-22
umm assuming the problem is that the permissions in your home folder are screwed up.
If so, to fix them, do the following:

To fix dir permissions:

> 
find /home/toksin -type d -exec echo chmod u+rwx '{}' \;


To fix file permissions:

> 
find /home/toksin -type f -exec echo chmod u+rw '{}' \;



**Note:** Currently, the above two commands don't actually change the permissions. They just show you what commands would have ben run to change the permissions. If the commands look right to you, then just remove the "echo" part and run it again. e.g.


> 
find /home/toksin -type d -exec chmod u+rwx '{}' \;
find /home/toksin -type f -exec chmod u+rw '{}' \;



DO NOT run this as root! Im not taking any responsibility if you hose your system!
Read the find man page if you want to know what the parameters do.

---

