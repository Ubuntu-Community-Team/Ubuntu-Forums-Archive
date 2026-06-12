---
title: "I messed my groups"
date: 2007-07-07
forum: General Help
---

### Post by ataiger on 2007-07-07
I dont know much about groups, but I realized that the group 'games' was my primary group and tried to fix it. I eventually had two primary groups, one that has my username, and another, 'games'.

I think I typed "sudo usermod -g games kiwoon(my username)" or something like that, and now, when I type "groups kiwoon" in terminal, I have only two groups, kiwoon and games.

I dont understand the situation well and 'sudo' seems to be not working. I am no more in admin group so I cannot run synaptic or many tools.

Is there any way to fix this problem?

---

### Post by ataiger on 2007-07-07
Some additional info:
(kiwoon: my user id)
```
$ id kiwoon
uid=1000(kiwoon) gid=1000(kiwoon) groups=1000(kiwoon),60(games)

$ groups kiwoon
kiwoon : kiwoon games

$ usermod -G admin kiwoon
usermod: &#50676;&#49632;&#44544; &#54028;&#51068; &#51104;&#44552;&#51012; &#54624; &#49688; &#50630;&#49845;&#45768;&#45796; // cannot lock password file or something like that
```

---

### Post by ataiger on 2007-07-07
I believe there is no way out. When I went out of the group 'admin' or 'adm' something, that was it. I think I must reinstall Ubuntu.

To help some people who might suffer my problem, just to inform, my mistake was that I wrote
```
usermod -G games (username)
```
I had to write
```
usermod -a -G games (username)
```
-a for append.

I couldn't find any well written documentation about users and groups. I think there must be one, but it is too hard to find it for me.

EDIT: gpasswd can be a better solution.

---

### Post by cewan on 2007-07-17
You don't have to reinstall. Simply reboot in failsafe mode. This will start up the system in terminal mode, and logged in as root. From here you can easily add your user to the group admin again!

---

### Post by emparq on 2007-07-17
Having recently gone through the same situation, I discovered that my original settings for groups was backed up in:

```
/etc/group-
```

...so in recovery mode, you can do the following:

```
# always a good rule of thumb to make a backup before writing to ANY system file
cp -a /etc/group /etc/group.bak

# overwrite the existing 'group' file with the system's backup copy
cp -a /etc/group- /etc/group

```

...reboot.

---

### Post by emparq on 2007-07-17
...as an aside, the command I think you wanted was:

```
usermod -a -G games myuserid
```

note the '-a' flag, that's for appending, instead of overwriting.

> **emparq said:**
> Having recently gone through the same situation, I discovered that my original settings for groups was backed up in:

```
/etc/group-
```

...so in recovery mode, you can do the following:

```
# always a good rule of thumb to make a backup before writing to ANY system file
cp -a /etc/group /etc/group.bak

# overwrite the existing 'group' file with the system's backup copy
cp -a /etc/group- /etc/group

```

...reboot.

---

