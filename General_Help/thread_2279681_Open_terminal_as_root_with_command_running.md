---
title: "Open terminal as root with command running"
date: 2015-05-25
forum: General Help
---

### Post by triplemaya on 2015-05-25
I want to have a menu item that opens a terminal as root and runs nethogs. Root is a requirement, so:

gnome-terminal -e nethogs

does not work

Nor does sudo, gksudo, su, or gksu

---

### Post by Lars Noodén on 2015-05-25
What about this?

```

gnome-terminal -x /usr/bin/sudo /usr/sbin/nethogs

```

---

### Post by triplemaya on 2015-05-25
Thanks. Works great. But I still have to type in the password when the terminal comes up.

---

### Post by Lars Noodén on 2015-05-25
Then you'll want to edit your [sudo configuration](http://manpages.ubuntu.com/manpages/trusty/en/man5/sudoers.5.html) using [visudo](http://manpages.ubuntu.com/manpages/trusty/en/man8/visudo.8.html).  Using 'visudo' plain will edit the file with [nano](http://manpages.ubuntu.com/manpages/trusty/en/man1/nano.1.html).

```

visudo

```

Or setting the environment variable $EDITOR to another editor will open the configuration file with the other editor.

```

EDITOR=/usr/bin/gedit visudo

```

Once in the configuration file, you'll need to add a line something like the following at the very end of the file:

```

%triplemaya ALL=(ALL) NOPASSWD: /usr/sbin/nethogs 

```

Except replace, if necessary, "triplemaya" with the group your account is a member of.

---

### Post by Lars Noodén on 2015-05-25
Just an afterthought about the nethogs line in gnome-terminal, you might need to specify which network interface to use, if you have something other than eth0.

```

gnome-terminal -x /usr/bin/sudo /usr/sbin/nethogs wlan0

```

---

### Post by triplemaya on 2015-05-25
Thanks. Very helpful instruction on how to edit visudo with gedit.

However, script still has the behaviour, requiring password typed in when the terminal comes up.

Thanks also for the wlan0 hint. Got it.

---

### Post by Lars Noodén on 2015-05-25
Ok.  If it's still requiring a password, then check to see what is really in sudoers by listing what your account is allowed:

```

sudo -l

```

---

### Post by triplemaya on 2015-05-25
Thanks.

This seems to look right.

User triplemaya may run the following commands on mate:
    (ALL : ALL) ALL
    (root) NOPASSWD: /usr/lib/linuxmint/mintUpdate/checkAPT.py
    (ALL) NOPASSWD: /usr/sbin/nethogs

---

### Post by Lars Noodén on 2015-05-25
Looks fine to me, too.  I'm not sure what to look at.  I tried a few combinations here to see if I could make some similar problem but cannot.  I presume that since you used visudo everything parses ok

```

visudo -sc

```

---

### Post by triplemaya on 2015-05-25
Yup. That's ok:

pc # visudo -sc
/etc/sudoers: parsed OK
/etc/sudoers.d/README: parsed OK
/etc/sudoers.d/mintupdate: parsed OK

AHA! In fact, it is all ok. Just tested again and it works perfectly. 
Must have taken a while to update something.

Thanks once again Lars. Your instructions have been so clear and informative. Ubuntu forums is very lucky to have you.

---

