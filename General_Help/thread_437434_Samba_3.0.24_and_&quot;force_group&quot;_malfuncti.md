---
title: "Samba 3.0.24 and &quot;force group&quot; malfunction ?"
date: 2007-05-08
forum: General Help
---

### Post by lolife.se on 2007-05-08
I've recently upgraded my home file server from Gentoo, to Xubuntu 7.04. Everything seems to work OK now, except one thing - browsing into Samba is quirky.

When I access from this Windows XP computer, on which I use a username/password that matches a user on the server, everything works fine. But if I access from any other Windows computer, in SHARE mode I get an error, in USER mode I get an empty user login (no default username at all, which is odd). I've used the same config from the Gentoo installation, which worked as it should then.

In the log for one of those machines, in SHARE mode I get "find_forced_group: forced user nobody is not a member of forced group smbadmin. Disallowing access."

The thing is, I have put a lot of "defaults" under [GLOBAL] that is true for almost all shares, eg...

```
guest account = nobody
....
public = yes
writeable = yes
write list = +writeenabledgroup
force group = +writeenablesgroup
force create mode = 775
force directory mode = 775
```

As I said, this worked fine before, but now it complains about not being member in the forced group, even when accessing IPC$. But isn't the plus-sign supposed to tell Sambe to check if the user is even a member of the forced group **before** trying changing the primary group.

So, is Samba broken, or have Samba changed in this regard? Does the plus-sign even matter anymore? I'd rather not put all those defaults into each and every share if I don't have to (if that even helps, since it would only move the problem to the share, no?).

---

### Post by falstaff on 2007-11-07
I agree that this worked before as you describe, and with gutsy not anymore! I used Edgy (6.10) before, and i could use the force group option with the + sign...

I used a workaround:
One share for public (read) access, another share of the same directory for write access. Its ugly, but after hours of tring i just accepted it as solution :(

Bye
falstaff

---

