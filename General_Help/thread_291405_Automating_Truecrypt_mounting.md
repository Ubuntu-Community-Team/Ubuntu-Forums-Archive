---
title: "Automating Truecrypt mounting"
date: 2006-11-02
forum: General Help
---

### Post by cage cat donnie on 2006-11-02
I have some low-security info on a partition I want to protect.  I have the disk networked with a windows system, and I want to be able to access the partition while in windows.  I don't want all my data flopping in the wind on windows, so I created a truecrypt partition.  The security of a "user" profile is enough in linux, but I am lazy and I don't want to go to a lot of effort to mount the thing.

So..  How do I write a script that either automatically runs when I log in OR runs off a button on the panel so that I don't have to enter any passwords.  It is OK to have the password visible in the script.  As I said, it is low security.   

Any advice?    Thanks

---

### Post by Joe_CoT on 2006-11-02
this is the command:

```
truecrypt -u -p yourpassword /path/to/cryptfile /media/yourmountpoint
```

You can simply put that in a script file, make it executable, and then either add it to your start up programs in system -> preferences -> sessions, or add a panel launcher for it.

---

### Post by cage cat donnie on 2006-11-03
Thanks, that works great!

For the benefit of others who might be interested, I also had to allow truecrypt to run by users other than root, so that I wouldn't have to deal with sudo inside the script. 
```

sudo chmod u+s /usr/bin/truecrypt
```

---

