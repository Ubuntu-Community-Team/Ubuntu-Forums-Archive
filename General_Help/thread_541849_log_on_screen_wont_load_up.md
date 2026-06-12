---
title: "log on screen wont load up"
date: 2007-09-03
forum: General Help
---

### Post by joshbax on 2007-09-03
hey all, i have ubuntu 7.04 on my dell inspiron 6000 laptop, loving it so far etc.

but a few weeks ago, the log-on screen failed to load after i changed a few options.

it just has the circle with the grey bits in rotating, until i restart it.

i can, however, use the recovery console to boot up, only by typing startx.

but this logs me in as root etc, and i cant play dvd's, go online (i cant here anyway, am living in greece with this internet cafe), but its a less than ideal situation.

basically, is there some simple command i can enter to re-set the log on screen to default?


cheers, josh

---

### Post by taurus on 2007-09-03
Do you remember what are those options that you've changed?  Maybe you just need to change them back.

---

### Post by damaged0972 on 2007-09-03
I have exactly the same issue. I was changing the password for the root user and setting up a guest user, so just such a thing couldn't happen. Unfortunately I have only just gotten Linux to work and have no idea how to navigate or change things in the terminal. Funny thing is I was going through an e-book I just downloaded and now I cannot access that book through my windows partition.

---

### Post by mustali on 2007-09-03
probably some setting in the gnome configuration is messed up. I ran into this problem some time ago and I was able to get around it by removing the .gnome2 directory in the home directory. 
try the following:

```

cd 
mv .gnome2 .gnome2.old
sudo /etc/init.d gdm restart

```

Note that this will reset your gnome desktop settings to the default ones.

HTH.

---

### Post by joshbax on 2007-09-04
that sounded like the thing i needed to do, but, it just told me that /etc/init.d  was not a command and when i tried without the sudo, cause i am already root, it just told me that /etc/init.d is a directory...

i just need to re-set gdm. i dont care about personal profiles, but atm i cant even use memory stick and things, cause root wont load them up.

thanks for any help!

---

### Post by taurus on 2007-09-04
You mean

```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

---

### Post by mustali on 2007-09-04
I missed the '/'. sorry. 

thanks for correcting the typo, taurus!

---

### Post by joshbax on 2007-09-10
hey, i will try those commands later. the internet is so intermittent here...

i put those in the recovery console, yeh?

---

### Post by mustali on 2007-09-10
you could but it is not necessary.

this could also be done.
Go to a different console Ctrl+F1 and login
Stop gdm: sudo /etc/init.d/gdm stop
mv .gnome2 .gnome2.old
sudo /etc/init.d/gdm restart

---

### Post by joshbax on 2007-09-13
done those commands, no probs, but then it re-launches the stuck spinning disc.

i need to completely re-set the log on window i think! back to uber-defaults!

---

