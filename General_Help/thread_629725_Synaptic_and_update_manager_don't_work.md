---
title: "Synaptic and update manager don't work"
date: 2007-12-02
forum: General Help
---

### Post by molom on 2007-12-02
Please help me,
I'm running Xubuntu 7.10 and my first wireless card didn't work. So I got a new netgear one and it did work. Pidgin works and so does firefox. But synaptic only detects installed files (Which means if you type open office on the search for example only the installed files come up) and the update manager doesn't come with any updates.
How can I fix this? If there's no solution I'll have to go back to linux mint.

---

### Post by swerner on 2007-12-02
Are you sure that the "Status" filter (bottom left) is set to "All"?

---

### Post by molom on 2007-12-02
> **swerner said:**
> Are you sure that the "Status" filter (bottom left) is set to "All"?

Yes it is set. The update manager also doesn't connect to the internet. The only things that come up as uninstalled are programs that have an ubuntu logo next to them nothing else.

---

### Post by zvacet on 2007-12-02
Do you have all repos open?Chek in system>administration<software sources
Look inn sources list to be sure that you don&#733;t have any # sign in front of lines.

```
sudo mousepad /etc/apt/sources.list
```

if it ´s everything O.K. run this command

```
sudo aptitude update
```

---

### Post by molom on 2007-12-02
> **zvacet said:**
> Do you have all repos open?Chek in system>administration<software sources
Look inn sources list to be sure that you don&#733;t have any # sign in front of lines.

```
sudo mousepad /etc/apt/sources.list
```

if it ´s everything O.K. run this command

```
sudo aptitude update
```

That... FIXED IT!!! I went to software sources and all the boxes weren't ticked. I wonder why? I'm very greatful. Thankyou. Good luck with everything.

BTW. Now I can leave Xubuntu on :)

---

