---
title: "What can cause the /etc/hosts file not working?"
date: 2023-05-03
forum: General Help
---

### Post by danielchau1 on 2023-05-03
Hello,

I am facing a problem that I cannot add resolve domains/hostname by editing /etc/hosts on a newly installed machine...any idea why?


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292161&stc=1[/IMG]

Thanks
Daniel

---

### Post by TheFu on 2023-05-03
a) please don't post images of text.  Post the text instead.  Please.

b) check the /etc/nsswitch.conf file.  There needs to be a line like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns 
```

Whether anything other than files and dns are needed on that line is debatable.  Above is what a 22.04 system has.  Order on the line matters.  If I had any issues, I'd remove the mdns4_minimal and NOTFOUND parts, leaving:
```
hosts:          files dns 
```

---

### Post by danielchau1 on 2023-05-03
Hello [COLOR=#000000]TheFu[/COLOR],

[COLOR=#000000]The  /etc/nsswitch.conf already have 
```
[/COLOR]hosts:          files dns[COLOR=#000000]
```

I am using 22.04

I am also noticed that I have 
```
search .
```
in /etc/resolv.conf

I am not sure if this is the cause.

Thanks
Daniel[/COLOR]

---

### Post by TheFu on 2023-05-03
Does the system find localhost?  google.com?

The problem could be with the name resolver/caching on the system.  I usually disable that and point my DNS to two LAN-based DNS servers here. I don't need any local caching and resolvconf/resolved (from systemd) seem to just get in the way.

---

