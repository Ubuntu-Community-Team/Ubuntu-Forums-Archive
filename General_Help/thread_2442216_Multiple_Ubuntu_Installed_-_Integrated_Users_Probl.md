---
title: "Multiple Ubuntu Installed - Integrated Users Problem"
date: 2020-04-30
forum: General Help
---

### Post by ronaldmartin on 2020-04-30
I installed Ubuntu Studio, Ubuntu normal, and Ubuntu minimal. Ubuntu Studio has a different root/user than the Ubuntu installations.

I wanted to use the root/user from the Ubuntu installations as a user on the Ubuntu Studio, and so, I went to the Ubuntu Studio Users' set-up dialogue and filled it out, and something went wrong; I cannot use the Ubuntu root/user in any of the installations - I can only login to the Ubuntu Studio root/user.

While waiting for a reply, I am going to try removing the user that I created at the Ubuntu Studio Users' dialogue, and see if that gets me back to as it was.

Anybody understand what I am trying to do and what happened???

---

### Post by ronaldmartin on 2020-04-30
Removed the user, and I still cannot login to the other Ubuntu installations. Darn!

I hoping to be able to avoid having to reinstall the three installations, again. I've spent the past week, since the release of 20.04, trying several installation schemes until I finally was satisfied with this, until I screwed it up with this brilliant idea of having cross-integrated multiple users.

---

### Post by oldfred on 2020-05-01
I have multiple Ubuntu installs and keep /home inside / and have separate data partition(s) that I mount into each install so I have same data available.
Typically my other installs are test or new versions and any changes I do in setting, I usually do not want changed in my main working install.
But I only have one user.

If really wanting multiple users in multiple installs, know that user is 1000, 1001, 1002 etc. So order of creation becomes important so same name applies to each user.

---

### Post by HermanAB on 2020-05-01
Well, these kind of experiments is what virtualization is for.  That way, you don't screw your host installation.

So, read up on Virtmanager.

---

### Post by ronaldmartin on 2020-05-01
> **oldfred said:**
> I have multiple Ubuntu installs and keep /home inside / and have separate data partition(s) that I mount into each install so I have same data available.
Typically my other installs are test or new versions and any changes I do in setting, I usually do not want changed in my main working install.
But I only have one user. That's kind of what i want to do. I have done multiple installs with a single user, but I wanted to try something different this time, because Ubuntu Studio uses Xubuntu desktop which I don't really like, except for Thunar since Nautilus has turned into something slowwwww.

> **oldfred said:**
>  If really wanting multiple users in multiple installs, know that user is 1000, 1001, 1002 etc. So order of creation becomes important so same name applies to each user. Yeah, I noticed that, and I did not understand it. I'll try redoing that, and see if I get anywhere.

---

