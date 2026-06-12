---
title: "how do i download programmes and tranfer them to another computer"
date: 2007-11-06
forum: General Help
---

### Post by brotell on 2007-11-06
I am about to remove vista from laptop that will not be connected to the internet. I will then install Ubuntu.
How can I do updates and transfer other pro grammes to the laptop. My desktop is connected to the internet.

Ta Terry

---

### Post by kd7swh on 2007-11-06
One easy way would be to download the packages you want from the ubuntu package archive.

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

it will be hard to keep everything up to date this way but it will work as long as you know what it is that you want.

---

### Post by birdbrain on 2007-11-06
[LIST=1]
[*]Do you have them networked together?

[*]Is your desktop running Ubuntu?
[/LIST]

If your desktop runs Ubuntu then you can transfer files found here:
```
/var/cache/apt/archives/
```

This is where programs that are downloaded by apt or synaptic are stored.

You will need some sort of Internet connection to update...why worry about updating the computer if it is not going to be on the net?

---

### Post by antmenj on 2007-11-07
> **birdbrain said:**
> [LIST=1]
[*]Do you have them networked together?

[*]Is your desktop running Ubuntu?
[/LIST]

If your desktop runs Ubuntu then you can transfer files found here:
```
/var/cache/apt/archives/
```

This is where programs that are downloaded by apt or synaptic are stored.

You will need some sort of Internet connection to update...why worry about updating the computer if it is not going to be on the net?

So if I wanted to instal a new hard drive could I copy that directory to a cd and store all **updates** and **program**s so I don't have to download them again?

---

### Post by zvacet on 2007-11-07
[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

---

### Post by brotell on 2007-11-07
Thank you problem solved

Terry

---

