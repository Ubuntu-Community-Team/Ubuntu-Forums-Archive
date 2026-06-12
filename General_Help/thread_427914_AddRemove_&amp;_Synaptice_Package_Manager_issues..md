---
title: "Add/Remove &amp; Synaptice Package Manager issues."
date: 2007-04-29
forum: General Help
---

### Post by Omicronpk on 2007-04-29
Hi there. Erm, Add/Remove closes down while loading. And the Synaptic Package Manager does the same when i go to Settings - Repositories. I have no idea why it is doing this or how to fix it (just installed dapper drake today you see). Searched the forums and obviously my searching skills aren't up to scratch as i'm sure the topic has been touched on before but i'm unable to locate it. I would really appreciate some help.

Thank you. :)

---

### Post by taurus on 2007-04-29
What happens when you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Omicronpk on 2007-04-29
> **taurus said:**
> What happens when you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

Thanks for reply. 

I get this ->

```

magnus@magnus-laptop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Reading package lists... Done
magnus@magnus-laptop:~$ sudo aptitude upgrade
```

Also, my source.list seems to have dissapeared from /etc/apt :confused:

---

### Post by taurus on 2007-04-29
No sources.list!  What's the output of this command then?

```
ls -la /etc/apt
```

---

### Post by Omicronpk on 2007-04-29
Ah i got it to work. 

I followed this tut. 

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Thank you again :)

---

