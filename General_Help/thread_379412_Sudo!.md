---
title: "Sudo!"
date: 2007-03-08
forum: General Help
---

### Post by utnubu1 on 2007-03-08
Oh no....


ben@ben-desktop:~$ sudo -i
sudo: must be setuid root


ben@ben-desktop:~$ su
Password:
su: Authentication failure
Sorry.


/usr/ben/sudo 
Permission -rwxr-xr-x
File Owner - root
File group - ben

Im not sure how this happended is there any way to fix?

---

### Post by etank on 2007-03-08
Try to do a ```
sudo chown root.root /usr/bin/sudo
```
If that does not work then I think that you can boot with a livecd and do it.

---

### Post by melancholeric on 2007-03-08
is it setuid?

chmod 4755 /usr/bin/sudo

---

### Post by utnubu1 on 2007-03-08
Ive done both these things through live cd but it still says
sudo: must be setuid root
any idea?

---

### Post by cookfromfrozen on 2007-03-08
When you work through the LiveCD, you are not actually touching your real system but a "virtual" system running from the CD.  Thus any changes you make in the LiveCD are not preserved.

Since you can't gain "root" privileges through sudo (because it's broken), you'll need to go into the recovery console to make the changes that have been suggested.

To do this, restart the machine, and when you see the "GRUB loading..." message and a countdown timer, hit escape and pick the Ubuntu option with "recovery mode" in brackets.

This will take you to a console where you may input commands as the root user.  What has been suggested already should hopefully fix it.

If not, you may want to re-install sudo.  From the recovery console, try this command:
```
apt-get install -reinstall sudo
```

---

