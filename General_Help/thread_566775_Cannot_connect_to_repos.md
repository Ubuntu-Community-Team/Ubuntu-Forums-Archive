---
title: "Cannot connect to repos"
date: 2007-10-03
forum: General Help
---

### Post by fadastic on 2007-10-03
Well...basically, I'm trying to get some programs from Synaptec package manager, and all of my connections are timing out. Anyone know why?

---

### Post by por100pre1 on 2007-10-03
I don't know why, but I suggest you to use this:

```
gksudo software-properties-gtk
```

A window will appear. Select another server, you will be given the option to select the fastest server. 

Hope it helps. :)

---

### Post by strabes on 2007-10-04
Paste the output of this command:```
sudo aptitude update
```

---

### Post by fadastic on 2007-10-04
> **por100pre1 said:**
> I don't know why, but I suggest you to use this:

```
gksudo software-properties-gtk
```

A window will appear. Select another server, you will be given the option to select the fastest server. 

Hope it helps. :)
Unfortunately not. I'm not able to connect to the servers for some reason. Even if I try to type in the location of a file (like [http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)) in Firefox it times out.
> **strabes said:**
> Paste the output of this command:```
sudo aptitude update
```

```
0% [Connecting to archive.ubuntu.com (91.189.89.8)]

```

It basically times out at all of them.

---

### Post by zvacet on 2007-10-04
```
cat /etc/apt/sources.list
```

Post it here.

---

### Post by fadastic on 2007-10-04
I have all the right sources. Oddly enough, today I'm able to connect and nothing on my side has changed. Would it be possible that my ISP was blocking traffic, or something?

---

### Post by por100pre1 on 2007-10-04
> **fadastic said:**
> I have all the right sources. Oddly enough, today I'm able to connect and nothing on my side has changed. Would it be possible that my ISP was blocking traffic, or something?

Maybe there was an issue with your ISP's domain name servers. To add some extra DNS servers can help in those cases:

```
gksudo network-admin
```

In the DNS tab add these DNS servers:

208.67.222.222
208.67.220.220

---

