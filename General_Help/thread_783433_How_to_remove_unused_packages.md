---
title: "How to remove unused packages"
date: 2008-05-05
forum: General Help
---

### Post by Jordanwb on 2008-05-05
On my laptop I uninstalled Firefox and installed Konqueror. However when I uninstalled Firefox it didn't uninstall unrequired dependancies. Is there a way to remove them?

Thanks.

---

### Post by tamoneya on 2008-05-05
```
sudo apt-get autoremove
```

---

### Post by Jordanwb on 2008-05-05
Thanks. I'll do that right now.

---

### Post by danbuter on 2008-05-05
use aptitude, not apt-get.

---

### Post by Jordanwb on 2008-05-06
What's the difference?

---

### Post by danbuter on 2008-05-06
aptitude finds all the dependencies, apt-get does not.

---

### Post by Jordanwb on 2008-05-06
Good enough for me. Thanks.

I ran "sudo aptitude autoremove" and it said there is no such command "autoremove", I couldn't find any subcommand dealing with removing unneeded packages.

---

### Post by danbuter on 2008-05-07
Didn't notice the first reply was wrong. It's 'sudo aptitude autoclean'.

---

### Post by Jordanwb on 2008-05-07
Okay I'll give that a try. Cool Avatar avatar.

---

### Post by Monicker on 2008-05-07
> **danbuter said:**
> aptitude finds all the dependencies, apt-get does not.

Since when?  apt-get also handles all the dependencies.

---

### Post by agim on 2008-05-07
I have heard that aptitude and apt-get shouldn't both be used. That you have to use one or the other, because they create different databases to handle packages.

Better check before using both.

---

### Post by kaens on 2008-05-07
> **Monicker said:**
> Since when?  apt-get also handles all the dependencies.

Aptitude is a bit smarter about it. Granted, I've never had much of a problem with apt-gets dependency resolution, but I've heard some horror stories.

---

### Post by Six_Digits on 2008-05-07
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)
[http://www.pthree.org/2007/08/12/aptitude-vs-apt-get/](http://www.pthree.org/2007/08/12/aptitude-vs-apt-get/)

I love that page...

---

### Post by Monicker on 2008-05-07
> **kaens said:**
> Aptitude is a bit smarter about it. Granted, I've never had much of a problem with apt-gets dependency resolution, but I've heard some horror stories.

I've been using apt-get for years.  I've never had a problem with it and dependencies.

---

### Post by Monicker on 2008-05-07
> **Six_Digits said:**
> [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)
[http://www.pthree.org/2007/08/12/aptitude-vs-apt-get/](http://www.pthree.org/2007/08/12/aptitude-vs-apt-get/)

I love that page...

Interesting.  I must just be lucky then.  I've never had any of the problems mentioned, ever since starting with Debian Woody. Not under Ubuntu either.

---

### Post by chrisgaffrey on 2009-04-16
I found that aptitude autoclean did not find the package I was looking to remove.

---

