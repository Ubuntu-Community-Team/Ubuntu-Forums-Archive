---
title: "Security Issue - Fork Bomb"
date: 2007-03-03
forum: General Help
---

### Post by OffHand on 2007-03-03
Why  isn't Ubuntu protected against fork bombs by default? This doesn't make sense to me. 

For those who do not know what a fork bomb is read:

[http://en.wikipedia.org/wiki/Fork_bomb](http://en.wikipedia.org/wiki/Fork_bomb)

Now by default Ubuntu is not protected against fork bombs, while you can easily do this by editing /etc/security/limits.conf and add the following line:

```
*           	 hard    nproc           512
```

You can check what the settings are on your system with the following command:

```
ulimit -u
```

It will probably show 'unlimited', which opens the door for fork bombs.

/discuss

---

### Post by christhemonkey on 2007-03-03
Found this mildly amusing:
> **Canonical forkbombs **include this one on Unix (using the Bash shell) (Explanation):
*snip*
(probably shouldnt as this is quite a serious thing, but still....)

---

### Post by OffHand on 2007-03-03
> **christhemonkey said:**
> Found this mildly amusing:


(probably shouldnt as this is quite a serious thing, but still....)

hehe yeah, that made me laugh too  :)

---

### Post by OffHand on 2007-03-04
up

---

### Post by parktownprawn on 2007-03-04
i've always though the term wabbit was more colourful than fork bomb  (although according to wikipedia a wabbit is a kind of fork bomb)

I once accidentally crashed my departments network with a wabbit. By mistake i deleted the first character of my .bashrc to read

!/bin/bash

rather than 

#!/bin/bash

so that if i logged on, suddenly I was logged on 10000+ times and the whole system became pretty unusable.

it was sort of scary to see that accidentally deleting one character in an  unprivileged  
account could do some much damage. fortunately i wasn't too unpopular with the sysadmin since it was really their fault for not configuring /etc/security/limits.conf. 

ps. don't try this at home

---

### Post by kinematic on 2007-03-04
strange that ubuntu isn't protected by default since debian is :confused:

---

### Post by n00b buntu on 2007-05-09
Ubuntu also doesnt have SELinux, and Fedora does by default. What's up with that?

---

### Post by n00b buntu on 2007-05-09
Ubuntu should have encrypted partitions by default too.

---

### Post by PriceChild on 2007-05-09
Please don't hijack this thread into what Ubuntu should have.

Ok so with the forkbomb protection... why don't one of you file a bug and report the number here? Ask me for help if you don't know how.

---

### Post by ubuntu27 on 2007-05-14
> **OffHand said:**
> Why  isn't Ubuntu protected against fork bombs by default? This doesn't make sense to me. 

For those who do not know what a fork bomb is read:

[http://en.wikipedia.org/wiki/Fork_bomb](http://en.wikipedia.org/wiki/Fork_bomb)

Now by default Ubuntu is not protected against fork bombs, while you can easily do this by editing /etc/security/limits.conf and add the following line:

```
*           	 hard    nproc           512
```

You can check what the settings are on your system with the following command:

```
ulimit -u
```

It will probably show 'unlimited', which opens the door for fork bombs.

/discuss

Thank you OffHand.

So, I opened /etc/security/limits.conf and saw that it has:

```

#*                    soft    core            0
#*                    hard    rss             10000
#@student       hard    nproc         20
#@faculty        soft    nproc          20
#@faculty        hard    nproc         50
#ftp                  hard    nproc         0
#@student        -       maxlogins    4
```

And you said to add

```
*           	 hard    nproc           512
```

Should I put "#" before * ?


Oh, wait, if this works like the source.list... 

# means to ignore? So that means that I should just add that code without #, right?

---

### Post by parktownprawn on 2007-05-15
> **ubuntu27 said:**
> 
Oh, wait, if this works like the source.list... 

# means to ignore? So that means that I should just add that code without #, right?

yes # means ignore

---

### Post by rich.bradshaw on 2007-05-15
# is a comment in pretty much every config file as far as I know. It's always a comment in shell scripts, except for in front of the shebang i.e. #!/bin/bash.

---

