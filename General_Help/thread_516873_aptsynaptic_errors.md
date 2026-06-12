---
title: "apt/synaptic errors"
date: 2007-08-03
forum: General Help
---

### Post by clu on 2007-08-03
After an update the other night I can no longer use synaptic or apt-get.

Here is the error I get when loading synaptic:
```
E: ERROR: could not create state directory /var/lib/synaptic - mkdir (17 File exists)
E: _cache->open() failed, please report.
```

When trying 'apt-get update'
```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
```


Anyone have any ideas on what to do?

Any help would be greatly appreciated.

Thanks

---

### Post by atlfalcons866 on 2007-08-03
did you try using sudo? Like Sudo apt-get update?

---

### Post by clu on 2007-08-03
> **atlfalcons866 said:**
> did you try using sudo? Like Sudo apt-get update?
Ya it gets the same error with 'sudo apt-get update'


'sudo aptitude update' produces a similar error but asks if I'm root.    I guess something is wrong with my permissions.
```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Couldn't lock list directory..are you root?
```

---

### Post by staticsage on 2007-08-06
Apt and synaptic can not "lock" the directory if it is in use by another application (typically a hung apt or synaptic).

Try doing

```
sudo killall synaptic
sudo killall apt-get
```

Then proceed with your update as normal. This problem started happening with me with one of the recent updates.

---

### Post by Seisen on 2007-08-06
You can also try

```
sudo dpkg --congfigure -a 
```

---

### Post by clu on 2007-08-06
I entered
```
sudo killall synaptic
sudo killall apt-get
```

Received
```
synaptic: no process killed
apt-get: no process killed
```



I entered 
```
sudo dpkg --configure -a
```
but still receive the errors.

:confused:

---

### Post by kast on 2007-08-08
Same issue here,  still looking for a the solution. will post back if i find it! :)

---

