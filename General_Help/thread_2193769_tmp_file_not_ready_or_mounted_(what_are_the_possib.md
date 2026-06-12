---
title: "/tmp file not ready or mounted (what are the possible culprits?)"
date: 2013-12-14
forum: General Help
---

### Post by FenrirXIII on 2013-12-14
lately, i have experience /tmp file not ready or mounted on a couple of boots.... not necessarily on simulations boots but i guess at random times. it does get "pretty cold" (<-- and thats putting it lightly) in my room and thats the only reason i can think of...

---

### Post by Bashing-om on 2013-12-15
FenrirXIII; Hi !

The main thing that pops to mind is - file system corruption.
Have you ran any of the file system checks ?
The easiest, fastest - less invasive:
Terminal codes:
```

sudo touch /forcefsck
sudo shutdown -r now

```
Which will set the system to run a file system check at next boot. and then reboot to check the filesystem then.

If the problem continues, may I suggest a through file system check/repair from a liveDVD environment ( can not fix a file system when in use) ?

'buntu is smart
[INDENT][INDENT]real smart
[/INDENT][/INDENT]

---

