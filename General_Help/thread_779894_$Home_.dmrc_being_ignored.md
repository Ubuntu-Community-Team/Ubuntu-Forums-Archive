---
title: "$Home .dmrc being ignored"
date: 2008-05-03
forum: General Help
---

### Post by Tsukino Kyuuketsuki on 2008-05-03
Ok, so I don't know what I did (say I don't remember...) but when I log in I get this message:

> Users $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. The file should be owned by user and have 644 permissions. Users $Home directory must be owned by user and not writable by others.

It's annoying but it also gets me worried... I don't know what I did to get this message.

I already tried

```
chmod 0644 /home/username/.dmrc
```

I don't know what else I could do to fix this. Thanks in advance for any help ^^

---

### Post by qpieus on 2008-05-03
I checked my file and it has permissions of 600, not 644 like your error says (and I don't get that error). What are the permissions on the file right now?```
ls -la ~/.dmrc
```
Also, what are the permissions on your home folder?```
ls -la /home/*username*
```

Here's a link you can read for more info:

[https://answers.launchpad.net/ubuntu/+question/7296](https://answers.launchpad.net/ubuntu/+question/7296)

---

### Post by Tsukino Kyuuketsuki on 2008-05-03
Thank you ^^! The link did help me...

```
sudo chmod 700 /home/username
```

Solved the problem. I still wonder what I did to get that error...

---

### Post by djrakun on 2008-05-22
I started getting that error just after an upgrade from Gutsy Gib to Hardy Heron.  I did a fresh install of Hardy on my other PC and didn't have any issues.  I think the file permissions got changed during the upgrade somehow

---

