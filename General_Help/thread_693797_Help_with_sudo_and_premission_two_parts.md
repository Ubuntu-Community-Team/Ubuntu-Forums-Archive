---
title: "Help with sudo and premission two parts"
date: 2008-02-11
forum: General Help
---

### Post by bone2006 on 2008-02-11
I was following an old post I saw here with some steps, except it seems that maybe things changed in ubuntu in a new release.  The instructions were

sudo echo /usr/local/lib >>  /etc/ld.so.conf

but as soon as type this command it says:
bash: sudo: Permission denied

It seems that the /usr/local/lib has premissions of 755 and that /etc/ld.so.conf is 644, so seems like maybe sudo is being applied to maybe just the first and not the second, but not sure what to do?

Thanks in advance

---

### Post by taurus on 2008-02-11
```
sudo echo /usr/local/lib >> **sudo** /etc/ld.so.conf
```

Or just edit /etc/ld.so.conf

```
gksudo gedit /etc/ld.so.conf
```
and add this line to the end of it.

```
/usr/local/lib
```

---

### Post by bone2006 on 2008-02-11
before posting I tried what you suggested by putting sudo after >> and I received the same error.  I ended up just doing a chmod 755 and then running the line, then just hitting the arrow key back up and changing it back to 644 after the command was ran.................seemed to work

But for my own notes I would be nice if it could be done in one line.

---

