---
title: "Per-user language support?"
date: 2007-09-04
forum: General Help
---

### Post by robinl on 2007-09-04
Is it possible to have interface language that's specific to the user in Ubuntu? For example can I set user A to be English, user B to be French and user C to be Chinese?

---

### Post by ebash on 2007-09-04
Yes it's possible and I did it a long time ago. The following page explains how you can do it: [http://www.cyberciti.biz/tips/gnome-language-encoding-different-than-console.html]("http://www.cyberciti.biz/tips/gnome-language-encoding-different-than-console.html").

The idea is to edit the file .dmrc for each user and to add the proper locale. For instance if you want to set the language to slovak the file should look like:

```

[Desktop]
Session=default
Language=sk_SK.UTF-8

```

If it doesn't work make sure that the permissions of the file are -rw-------, if in doubt do:

```
sudo chmod 600 .dmrc
```

Of course, you must install the languages packs before, this can easily be done with a few clicks:
```
Main menu >> System >> Administration >> Language Support
```

---

### Post by robinl on 2007-09-08
OK thanks a lot.

---

### Post by pespie on 2008-04-17
Hi All,

For me, this solution does nothing ...

I suppose it should be one of the very first things that should be VERY EASILY managed by a multi-user system and user graphic interface. I'm very disappointed with this problem.

I use freenx on a Ubuntu machine, and another user connect to this machine from Windows and nxclient from NoMachine.
Everything work so nicely ... except the user interface language : the server is normally in French (because I'm French ...), and the other user is Chinese, and does not speak French but English.
Problem : I can't provide him with an English interface. In fact, I could, only if I put the entire computer in English. Not so comfortable.

Anybody has a good idea (I mean, one which works) ?

Thanks a lot
Patrice

---

