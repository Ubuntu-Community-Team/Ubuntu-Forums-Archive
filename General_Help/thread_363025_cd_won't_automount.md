---
title: "cd won't automount"
date: 2007-02-16
forum: General Help
---

### Post by mykalreborn on 2007-02-16
i have a problem i just can't figure out. 
ubuntu doesn't autorun my cd's anymore. when i insert a cd i have to mount it manually. the funny thing is that when i insert a blank cd it asks me if i want to write it. also, i've uninstalled ubuntu-desktop . can that be the problem?

---

### Post by mykalreborn on 2007-02-16
bump...
i've read this thread ([http://www.ubuntuforums.org/showthread.php?t=349325&highlight=cd+automount)](http://www.ubuntuforums.org/showthread.php?t=349325&highlight=cd+automount)), but i can't understand what this guy's saying. 
thanks again!

---

### Post by bodhi.zazen on 2007-02-18
He is basically talking about permissions ...

Can you post the output of :

```
ls -al /bin/mount
```

And we can see if you have the same problem ?

basically the problem in the other thread is that the permissions of /bin/mount were changed.

They should be : > -rw**s**r-xr-x 1 root root 70564 2006-07-09 19:44 /bin/mount

To fix this, if yo do not have the correct permissions,

```
sudo chmod 4755 /bin/mount
```

And FYI a good review on permissions :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

See the bottom section (6)

---

### Post by akshaysrinivasan on 2007-02-18
Maybe you forgot to add gnome-volume-manager to your startup ?

---

### Post by mykalreborn on 2007-02-18
thanks bodi.zazen, but i don't think that's it. for the sake of it here is the output:
```
-rwsr-xr-x 1 root root 75088 2006-05-16 04:43 /bin/mount

```

@akshaysrinivasan:
i had some problems with gnome-volume-manager. the day before yesterday it gave me three errors that it crashed. almost at the same time so they were stacked one over the other. i chose to restart the application, but i guess it didn't work.
and in the System>Preferences>Sessions tab i can see gnome-vm in the running programs menu and in the startup programs it says "gnome-volume-manager --sm-disable"

any thoughts?
oh, and thanks for replying.
and off-topic. what does "akshaysrinivasan" mean? :D

---

### Post by mykalreborn on 2007-02-24
the problem was in the /etc/fsatb file. i don't know exactly what it was, but i copied the line for the cd from the original file and it worked. :D

---

