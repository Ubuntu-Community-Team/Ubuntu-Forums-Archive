---
title: "KVM and rdesktop problem"
date: 2007-07-22
forum: General Help
---

### Post by andytof47 on 2007-07-22
Hi all I'm using photoshop via the seamlessrdp which is fine when launched from the shell, but I have a couple of questions that are bugging me.

1) when I launch kvm without sudo I am denied access 
the problem for this is I can't make an icon to launch kvm windowsxpsp2.....

2)using this command from the shell 
```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Adobe\Adobe Photoshop CS2\Photoshop.exe" 127.0.0.1:3389 -u test -p test
```
works fine and also produces an error that reads out
```
WARNING: Remote desktop does not support colour depth 24; falling back to 16

```

But when I make a launcher I get a login screen and then it just hangs.......


any help????

---

### Post by andytof47 on 2007-07-22
ok the launcher is fixed now but I still get the issue of access denied if I launch KVM without sudo........ 

any help is appreciated

BTW
for those who just get a blue screen hangin when you try to log into ur VM make sure you only log in once per session ---- this helped me out....

---

