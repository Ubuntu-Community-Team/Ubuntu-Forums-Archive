---
title: "Can't login: 'too many links'"
date: 2008-05-07
forum: General Help
---

### Post by felipelavinz on 2008-05-07
I upgraded from Gutsy to Hardy about one week ago without any troubles until now. Today, I've been unable to login to my normal GNOME session, getting a message that says that my session closes after less than 10 seconds and that there might be a problem with my installation or my HD might be out of space... well, it's not out of space.

Here's the error message that I get on ~/.xsession-errors:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=es_CL.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

** (seahorse-agent:6447): CRITICAL **: can't create directory: /tmp/seahorse-BT2oBJ: Demasiados vínculos
```

There on the last line, "Demasiados vínculos" means "Too many links"

I can get into the fail safe GNOME session but I have no idea how to fix this. /tmp/seahorse-BT2oBJ doesn't exists when I login, the part after "seahorse-" changes every time I restart my PC.

I tried to remove the seahorse package using synaptic, but I can't get into it, I get a message that says something like "unable to execute /usr/sbin/synaptic as root -  can't copy the Xautorization user file". I tried to do it with aptitude (on a terminal) but it also marks a lot of other packages since it depends on ubuntu-desktop

---

### Post by felipelavinz on 2008-05-09
Ok, so at last I could fix it.

As I wrote on the previous post, the problem was that it was impossible to create anything on /tmp, which is a real pain since that's used to create temporal files and links for several actions in Linux, for instance, gksu authentication.

Thanks to [this thread]("http://ubuntuforums.org/showthread.php?t=350015") I found out that it would be possible that it was a filesystem error and the way to fix it was using fsck, which is something like "chkdsk" for windows.

I couldn't run it when logged in on a normal session, so to use it I rebooted into recovery mode, got into a terminal as root, unmounted my root partition and then run fsck. I used "fsck -afpv" for automatic repair, forced check, automatic repair (yeah, I don't know why there are two options for it, but I used it anyway) and verbose, respectively.

After a few minutes, I could see that there were some errors on the root filesystem and they were repaired by fsck. The damaged files were moved into "/lost+found". I rebooted once again, and finally got into my normal session.

---

