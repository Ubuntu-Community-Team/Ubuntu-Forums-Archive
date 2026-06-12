---
title: "Gitlab defaulting to gitlab.example.com"
date: 2020-05-29
forum: General Help
---

### Post by dbee on 2020-05-29
Installed gitlab and must have missed a step. Some of the links default to gitlab.example.com/*

I can correct it by manually changing the url to gitlab.localhost.com/*

But it is annoying. How do i change it ?

Also, installed a local smtp server (postfix) and command line has changed from old command line to ...
```

dara@server1:

```
Not a big deal. but how do i get back to my previous hostname ?

---

### Post by TheFu on 2020-05-29
No. localhost.com is not yours to take.
If you use avahi, use gitlab.local
If you don't use avahi, then you don't need the .local, but you'll need to handle name resolution on your own.
Don't use any valid TLD, please. It will just cause issues.

---

### Post by dbee on 2020-06-03
sorry my bad.

I meant how do i direct it to gitlab.localhost/mygitproject ?

Of course, I don't own localhost.com. Where is the variable in the gitlab installation that replaces the 'example.com' with the 'localhost' setting  ?

---

### Post by TheFu on 2020-06-03
Using localhost is problematic because EVERY COMPUTER with a network stack thinks of itself as "localhost".  Please pick some other TLD.  Heck, gitlab.local would be ok.  mDNS w/ avahi  appends .local to every computer on your network that supports zeroconf.

People commonly use .lan as well.   .lan is the domain name.  gitlab would typically be the hostname or a web-server configured virtual web servername.  This is controlled by the webserver settings, usually in the sites-available/ directory.

i've never installed gitlab.  Only responded because the example.com was definitely wrong.  i'm only responding now because localhost is just as wrong and highly likely to only work on the same machine.  if you are already on the machine, what's the point of gitlab?  Use git from the shell.

---

