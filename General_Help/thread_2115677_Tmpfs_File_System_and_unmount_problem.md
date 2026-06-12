---
title: "Tmpfs File System and unmount problem"
date: 2013-02-13
forum: General Help
---

### Post by UltimateCat on 2013-02-13
;)Hi:

I'm trying to help a friend of mine that's running Ubuntu 12.04.

His System specs:
(X)ubuntu 12.04, heavily customized XFCE desktop, LightDM with KDE  greeter, fully updated until a few days ago. Running on an SSD, using  open-source graphics drivers.

Having trouble gettin tmpfs to work properly if it can be lined with pam_ mount to give automatic mountaing/unmounting of the HOME a root on login/logout?

He explained to me that logging thru the graphical interface causes the problem, logging in thru virtual terminal doesn't-
He tried this cmd:
```

mount -t tmpfs -o uid=1000,gid=1000,size=100m,mode=0700 none /home/user (at this point I logged in as myself) umount /home/user
```
This command was used in hope that it would help-
Still the problem exist's...
So I told him from what I have learned that:
 Some desktops also use fuse mounts within  the users home directory. So a "mount" listing might show these hanging  around as well, and that too would prevent a dismount.

He tried a '(think) fuser mount point when it hangs-
```

mount -t tmpfs -o size=100m,uid=[testuser-uid],gid=[testuser-gid],mode=0700 none /home/testuser
```
And this also-
```
Logout as root, and log in as testuser.
Logout as testuser, log in as root.
Attempt to unmount /home/testuser - this fails for me with 'Device is busy'

```

My friend Rob is using ' Winbind' could that  be the problem?

This is a bit beyond me now and I am not sure how to rectify this-
Please give me a few suggestions.....I'm not sure what to try ](*,)

---

### Post by UltimateCat on 2013-03-02
Anyone? 
:confused:

---

### Post by UltimateCat on 2013-04-18
It's been well over 4 weeks since I posted this thread--
Please, does anyone know how I can help my friend fix this?

---

