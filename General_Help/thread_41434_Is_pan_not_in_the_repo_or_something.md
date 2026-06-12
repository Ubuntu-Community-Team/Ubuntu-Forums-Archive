---
title: "Is pan not in the repo or something?"
date: 2005-06-13
forum: General Help
---

### Post by Liam on 2005-06-13
I've got universe and multiverse enabled, and've reloaded multiple times, but it's not showing up.

Anybody have any idea what gives?

---

### Post by bored2k on 2005-06-13
[QUOTE=Liam]I've got universe and multiverse enabled, and've reloaded multiple times, but it's not showing up.

Anybody have any idea what gives?[/QUOTE]
 [http://ubuntuguide.org/#pan](http://ubuntuguide.org/#pan)

Yes it is. Try sudo apt-get update && sudo apt-get install pan.

---

### Post by GrammatonCleric on 2005-06-13
Have you added the extra repos?

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

-G

---

### Post by Liam on 2005-06-13
Yes and yes:

```

$ sudo grep http /etc/apt/sources.list
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary multiverse
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe
deb http://security.ubuntu.com/ubuntu hoary-security multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security multiverse
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

$ sudo apt-get update
[Hit everything OK]

$ apt-cache search pan | grep ^pan
panorama - A framework for 3D graphics production
pantomime-dev - Objective-C library for mail handling
pantomime1 - Objective-C library for mail handling (development files)

See what I mean?

I've gotta admit, *I'm* a little confused.

---

### Post by eyequeue on 2005-06-14
[QUOTE=Liam]
```

deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu hoary multiverse
deb http://us.archive.ubuntu.com/ubuntu hoary universe

```

I've gotta admit, *I'm* a little confused.[/QUOTE]

It's possible you've been bitten by the issues with the us.archive.ubuntu.com mirror.

Edit (using sudo) the above three lines and change the hostname to just archive.ubuntu.com, then ```
$ sudo apt-get update && sudo apt-get install pan
```

OH WAIT!

Your sources.list is missing something very important!

You have:
```
deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary-updates main restricted

```

Notice that the above is **not** the same as
```

deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary main restricted

```

You very definitely need to add the latter two lines to your sources.list (and may as well strip the us. part from them for now, too.) Pan is in main, and you did not have the main hoary repository included.

Do that, and **then** run ```

$ sudo apt-get update && sudo apt-get install pan
```

---

### Post by Liam on 2005-06-14
[QUOTE=eyequeue]You very definitely need to add the latter two lines to your sources.list (and may as well strip the us. part from them for now, too.) Pan is in main, and you did not have the main hoary repository included.

[/QUOTE]

#-o

Doh. I should have noticed that. Thanks.

---

