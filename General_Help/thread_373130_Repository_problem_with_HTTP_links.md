---
title: "Repository problem with HTTP links"
date: 2007-02-28
forum: General Help
---

### Post by nastavirss on 2007-02-28
I seem to have a problem with any of the http links that i give in my repository. It gives me an error connecting for all the HTTP links. The FTP links seem to work fine.

Kindly Help!!

Thank You

---

### Post by ~LoKe on 2007-02-28
Example?

---

### Post by nastavirss on 2007-02-28
my repository listing :

```
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src ftp://archive.ubuntu.com/ubuntu dapper main restricted universe multive$
## MAJOR BUG FIX UPDATES produced after the final release
deb ftp://archive.ubuntu.com/ubuntu dapper-updates main restricted universe mul$deb-src ftp://archive.ubuntu.com/ubuntu dapper-updates main restricted universe$
## UBUNTU SECURITY UPDATES
deb ftp://security.ubuntu.com/ubuntu dapper-security main restricted universe m$deb-src ftp://security.ubuntu.com/ubuntu dapper-security main restricted univer$
## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at ow$deb ftp://archive.ubuntu.com/ubuntu dapper-backports main restricted universe m$deb-src ftp://archive.ubuntu.com/ubuntu dapper-backports main restricted univer$

```

this is the error that i get. 
```
nastavirss@sriramajayam:/etc/apt$ sudo apt-get update
Err http://archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 91.189.89.6 80]
Ign http://archive.ubuntu.com dapper Release
Ign http://archive.ubuntu.com dapper/main Packages

```

---

### Post by ~LoKe on 2007-02-28
> ## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

Try that?

---

### Post by nastavirss on 2007-02-28
No it does not workt

---

### Post by ~LoKe on 2007-03-01
Same error?

---

### Post by nastavirss on 2007-03-01
yes i am getting the same error.

---

### Post by ~LoKe on 2007-03-01
Let's try this:
> ## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

---

### Post by nastavirss on 2007-03-01
i am still getting the same error

---

### Post by nastavirss on 2007-03-01
but for the same thing, if i change everything to "ftp" it works fine.

This is fine for the standard repositories. But if i want to add other repositories, even the "ftp" does not work.

---

### Post by zanglang on 2007-03-01
Might be a silly question, but can you access [http://archive.ubuntu.com](http://archive.ubuntu.com) or [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) in your web browser (and if you use a proxy, *without* the proxy)?

---

### Post by nastavirss on 2007-03-01
yes i am able to access the http links using my browser

---

### Post by lars18th on 2007-04-16
Look at this thread, it worked for me.

[http://ubuntuforums.org/showthread.php?t=380431](http://ubuntuforums.org/showthread.php?t=380431)

---

