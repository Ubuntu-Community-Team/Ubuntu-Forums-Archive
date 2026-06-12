---
title: "[SOLVED] chown went wrong, broke openoffice.org"
date: 2008-06-17
forum: General Help
---

### Post by cacycleworks on 2008-06-17
Hey everyone, here's a great mistake I made...

I tried to start up openoffice and it gave me a cute little popup box saying: "The application cannot be started. The interface language cannot be determined." I hit OK and it died. Hmph.

Googling around had about 3 answers, all of which implied a new install. One of them said to rm the .openoffice folder... hmmmm...


```
18:15 chris@outside ~$ ls -al
total 2246864
drwxr-xr-x 57 chris    chris      4096 2008-06-17 18:12 .
drwxr-xr-x  7 root     root       4096 2008-06-14 00:07 ..
-rw-r--r--  1 chris    chris      5337 2008-06-17 18:12 ooow.kcrash
drwx------  3 www-data chris      4096 2008-06-12 20:11 .openoffice.org2

```

Do we see a problem here? :)

Well, I was working on my httpd files and mistyped a ```
sudo chmod -R www-data:chris *
``` command. I realized it was taking too long very quickly and ^C ... then I saw what I did and then issued a ```
sudo chmod -R chris:chris *
``` and went on my merry way. 

What I needed to do was ```
sudo chmod -R chris:chris .*
```, which would also chmod the hidden files. 

So if someone gets that error, it could be related to ooo not being able to read the config directory. I also got a krash out of it and will see about sharing that with the ooo team. I mean, like, really, couldn't they foresee that someone would alter their config directories so that they're unreadable?! :lolflag:

I posted this to the forum so that Google could help others learn from my mistake. :)

Yaay,
Chris

---

