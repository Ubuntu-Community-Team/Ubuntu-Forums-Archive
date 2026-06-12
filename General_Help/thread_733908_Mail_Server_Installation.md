---
title: "Mail Server Installation"
date: 2008-03-24
forum: General Help
---

### Post by Tymierb on 2008-03-24
I'm having some trouble installing a mail server under Ubuntu 7.10. When I run the command:

```
sudo apt-get install postfix postfix-tls libsasl2 sasl2-bin libsasl2-modules popa3d
```

It returns this:

```
Reading package lists....Done
Building Dependency tree
Reading state information...Done
Note, selecting postfix instead of postfix-tls
Package libsasl2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
     libsasl2-2
E: Package libsasl2 has no installation candidate
```

It seems to me like this  installation package is no longer available. I'm using a tutorial or "walk-through" of a full server installation available here (scroll to "Mail Server Installation"):

[http://www.mysql-apache-php.com/]("http://www.mysql-apache-php.com/")

Can anyone tell me where to find this missing package?

---

### Post by SpaceTeddy on 2008-03-25
have you done a "sudo apt-get update" to make sure that you have the latest sources ?

if not - you can download the package [here]("http://packages.ubuntu.com/gutsy/libsasl2-2") (this should never be neccessary). also, i have not found any special repositry they are in, so they should be found in main - please make sure that all repositories are enabled in your software sources.

---

