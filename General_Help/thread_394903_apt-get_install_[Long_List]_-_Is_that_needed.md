---
title: "apt-get install [Long List] - Is that needed?"
date: 2007-03-27
forum: General Help
---

### Post by quicksilver1234 on 2007-03-27
Going through the tutorial more...
[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p5]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p5")
Apache
```
apt-get install apache2 apache2-common apache2-doc apache2-mpm-prefork apache2-utils libapr0 libexpat1 ssl-cert (1 line!)
```
Do I HAVE to put all of that on one line?
Does it work just as well if I install one element at at time, just slower?
```
apt-get install apache2
apt-get install apache2-common
apt-get install apache2-doc
```

---

### Post by dfreer on 2007-03-27
should work just fine, although it would be a bit slower because you have to put each line in individually. is there a reason you don't want to put it all on one line?

---

### Post by quicksilver1234 on 2007-03-27
yeah, I'm just enough dyslexic,  that typing out long cryptic lines of code is very difficult. the letters dance after a while.

---

### Post by dfreer on 2007-03-27
lol yeah.
BTW, the ISP-Server Setup quite a bit of overkill if you are simply setting up a web server. If you don't mind, what all will you be using your website for?

---

### Post by quicksilver1234 on 2007-03-27
I plan on hosting my site and my partner's personal websites and, eventually, a set  of affiliate marketing sites that use PHP and Mysql.  Then I'll make so much money, I'll be able to move to Canada. [grin]
I'm a web dev, so I know how to code web pages and php but I want to understand how the computer works. So I figured I'd set up a web host as part of the learning process

---

### Post by quicksilver1234 on 2007-03-27
I used to have an old Redhat as my server, but it got compromised by a hacker. I decided to upgrade and Ubuntu LAMP looked like it did what I wanted. The command line interface is giving me fits however, I'm so used to graphical interfaces. (I came to computers as a mac user in the 1980s).

---

### Post by dfreer on 2007-03-27
> Then I'll make so much money, I'll be able to move to Canada. [grin]
Ah, the american dream. lol. Good Luck!

---

### Post by zvacet on 2007-03-27
Why don´t you install GUI? if you prefer Gnome
```
sudo aptitude install ubuntu-desktop
```

and if you are for KDE

```
sudo aptitude install kubuntu-desktop
```

---

