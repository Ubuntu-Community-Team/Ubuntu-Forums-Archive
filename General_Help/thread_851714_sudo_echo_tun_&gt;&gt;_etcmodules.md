---
title: "sudo echo tun &gt;&gt; /etc/modules"
date: 2008-07-06
forum: General Help
---

### Post by boblemur on 2008-07-06
hey all,

im trying to write a script to install hamachi, but first i need to add tun to the loaded modules, and when i put sudo at the start of the echo command.. it gets access denied because the echo is run as sudo but the pipe to file isnt.. i was wondering if i could get it to run as root when pipeing

i was thinking i could go

chown <user> 
and then chown root after editing but  it seems rarther clumsy...

---

### Post by scragar on 2008-07-06
use ```
sudo su
echo tun >> /etc/modules
exit
``` to temp gain root privilages, that way your line doesn't need boosting to root, or try:
```
echo tun >> sudo /etc/modules
```

---

### Post by aroch1 on 2008-07-06
It's not the most elegant solution ever, but the quickest one I could think of at this time of night:

```
echo "tun" | sudo tee -a /etc/modules
```

Like I said, not the most graceful solution ever, but much *much* better than chowning it to the user and then back to root.

---

### Post by boblemur on 2008-07-06
yeh i would rarther not be logging in as root, as the root account then needs to be enabled for the script to work, i tried the second one ( was my original guess ) and it actualy makes a file sudo and puts tun /etc/modules in it...

---

### Post by boblemur on 2008-07-07
thanks very much, yeh that works perfectly for what i need, ill keep tee in mind... slowly learning all the commands...

thanks again

---

### Post by aroch1 on 2008-07-07
You're very welcome.  I just learned tee myself recently, but its a very useful utility to keep in mind.

---

### Post by bodhi.zazen on 2008-07-07
tee is very cool.

You can (FYI):

```
sudo sh -c "echo tun >> /etc/modules"
```

---

