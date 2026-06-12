---
title: "Repositories down!"
date: 2007-02-11
forum: General Help
---

### Post by Faolan84 on 2007-02-11
the repositories at [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) are down. this is the main server for the united states so if you are having problems with apt-get or synaptic this is probably why.

---

### Post by FuturePilot on 2007-02-11
Yeah, I think you're right. I just tried an apt-get update and half of them failed. Anyone else confirm this?

---

### Post by styracosaurus on 2007-02-11
I also cannot connect to the us.archive.ubuntu.com repositories.

---

### Post by FuturePilot on 2007-02-11
Well I tried again and it worked:confused:

---

### Post by ardchoille42 on 2007-02-11
A temporary fix, if needed:

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

```
This makes a backup of /etc/apt/sources.list.
Then..

```

sudo sed -i 's/us.archive/archive/g' /etc/apt/sources.list

```
This changes all instances of [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) to [http://archive.ubuntu.com/](http://archive.ubuntu.com/)
Then..

```

sudo apt-get update && sudo apt-get upgrade

```
This updates the sources and then upgrades your applications.

If you want/need to restore the original /etc/apt/sources.list..
```

sudo rm /etc/apt/sources.list && sudo cp /etc/apt/sources.list.backup /etc/apt/sources.list
sudo apt-get update

```

---

