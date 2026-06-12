---
title: "Automatic apt"
date: 2005-08-01
forum: General Help
---

### Post by Pan007 on 2005-08-01
Can one run update on startup?
How?

I have a bunch of computers that are used by students. I don't want them to run Ubuntu update manager. So my question is:

Can Ubuntu be updated under startup and how to set this up.

---

### Post by strikeforce on 2005-08-01
make a bash script to do this.  And place it in your /etc/rcS.d/ 

I'm assuming and I've never done it but if its in there and its owned by root it will run as root.  I know in Fedora it does however I'm  not sure in ubuntu

```

#!/bin/sh

apt-get update; apt-get upgrade


```

---

### Post by Xian on 2005-08-01
You could look at using [cron-apt](http://www.debian-administration.org/articles/162).
The package is in the Hoary universe repos.

---

### Post by Pan007 on 2005-08-01
If I change 'sources.list' to only have hoary-security, then it only updates security issues in hoary and nothing else. 

Is this a secure way to go? I think so.

I will then create a scipt that runs on startup and change my 'sources.list' to only check hoary-security main restricted

comment this please

---

### Post by Pan007 on 2005-08-01
Is there a way in the script to automatic install upgrades, updates.

Now the user have to answer Y/n if there are upgrades, updates.

---

### Post by charlieg on 2005-08-01
Y'know, --help and man are your friends.  The lord helps those who help themselves.  I get the impression you didn't even try to figure this one out for yourself.
```
$ apt-get --help
...
  -y  Assume Yes to all queries and do not prompt
...
```

---

### Post by Pan007 on 2005-08-01
Sorry....I did, and I did find out your tip.

My script are now like this:

```
#!/bin/sh

apt-get -y upgrade; apt-get -y update
```

I also edited my sources.list to only include as mentioned above.

Hopfully this will work I supposed.......

---

### Post by angkor on 2005-08-01
I hope you didn't copy-paste that script, cause it says 'upgarde' in stead of 'upgrade'  ;-)

---

### Post by Pan007 on 2005-08-02
Fixed typing error.....it was late.....sorry folks.

But again...has anyone any comment on the script, and the fact that I'm running it on startup.

Is it OK to do it?
Can this f**k up the system, or is it a safe way to get upgrades?

---

### Post by heimo on 2005-08-02
[QUOTE=Pan007]Sorry....I did, and I did find out your tip.

My script are now like this:

```
#!/bin/sh

apt-get -y upgrade; apt-get -y update
```

I also edited my sources.list to only include as mentioned above.

Hopfully this will work I supposed.......[/QUOTE]

Well.. If I were to do this, I'd run update (updates package db) before upgrade. But I wouldn't do it, because I want to keep control of which packages are upgraded and see if there is any configuration file (syntax) changes. Automatic upgrades can bork your system, but serious borks are very rare on a stable release like Hoary. I'd probably just use some notifier on desktops I personally use and apt-cron or selfmade cron scripts on servers.

If I'd do what you want to do - I'd use something like this   ```
apt-get update && apt-get upgrade -y
```

---

### Post by Pan007 on 2005-08-03
Thanks for your comment......

I run a schools network with 6 different locations. It would be a problem for me to drive to all these locations to manually update the Ubuntu boxes. This is way I wanted to try out this automatic apt thing.

Are there any other way to do this?
(I don't want to give student access to update / upgrade.)

---

### Post by heimo on 2005-08-03
Oh! I'm not quite sure, haven't had to do anything like that in production. I'd probably look for what others have done and I know that one way to do is to make local repository / mirror (which clients will use to upgrade from). This approach saves bandwidth and gives some contol of what will be upgraded.

However, don't trust to my word here. I really suggest you to go look for best practises to manage larger Linux networks / upgrades on these scenarios. I'd be happy to hear about your solution when you've decided what to do.

---

### Post by Pan007 on 2005-08-03
I will, because of school startup in 2 weeks, try the soulution as described above.

Setting up my own repos server is a thing I will look at later.

First I have to get,

30 Dell Optiplex 170L with 17'' LCD
Nearly 100 Dell Latitude D505 with IPW2200B/G
Some Dell Latitude D810 with IPW2200B/G
15 Toshiba Satelite A10
and some old desktop's to work as smooth as possible within these two weeks.....

---

### Post by heimo on 2005-08-03
Oh man... That's a bunch of computer in two weeks. Couple sleepless nights approaching. Good luck.

---

