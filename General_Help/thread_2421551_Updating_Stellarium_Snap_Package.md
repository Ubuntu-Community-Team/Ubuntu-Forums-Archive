---
title: "Updating Stellarium Snap Package?"
date: 2019-06-23
forum: General Help
---

### Post by Daveski17 on 2019-06-23
Hello, I'm running Ubuntu 16.04 LTS. Snaps are a bit new to me. I have the version 0.19.0 of Stellarium from the Ubuntu Software repo.

[ATTACH=CONFIG]283489[/ATTACH]

Stellarium 0.19.1 has just been released. 

[https://stellarium.org/en_GB/](https://stellarium.org/en_GB/)

[ATTACH=CONFIG]283490[/ATTACH]

Will the snap version of 0.19.0 eventually automatically update to 0.19.1? If not, how do I update it?

Thanks.

---

### Post by kpatz on 2019-06-23
I don't know about the snap, but if you add Stellarium's PPA to your apt sources, you can install the latest Stellarium that way. 

```
sudo snap remove stellarium
sudo add-apt-repository ppa:stellarium/stellarium-releases
sudo apt update
sudo apt install stellarium
```

---

### Post by PaulW2U on 2019-06-23
Yes, snaps automatically update. I've read somewhere that the default is that a check for updates is made four times each day.

You can force a refresh of all snaps with the command
```
sudo snap refresh
```
or for individual snaps with
```
sudo snap refresh <snap_name>
```

---

### Post by kpatz on 2019-06-23
The snap will update once Canonical updates the snap in their repository, whenever that happens.

You can get 0.19.1 now from the Stellarium PPA, using the commands in my previous post.

---

### Post by PaulW2U on 2019-06-24
> **kpatz said:**
> The snap will update once Canonical updates the snap in their repository, whenever that happens.
Actually, the Stellarium snap **isn't** an official Canonical snap although it is maintained by a Canonical employee, presumably in his spare time. The latest update hasn't yet been made available in the [Snap Store]("https://snapcraft.io/stellarium-plars") although as you say it is available using a PPA which is maintained by the  Stellarium team. Any update to the PPA will always be released before the snap is updated.

@Daveski17, you asked if snaps automatically update and I answered that they do. Of course that is always dependent on the maintainer continuing to provide updates. :wink:

---

### Post by Daveski17 on 2019-06-24
> **kpatz said:**
> I don't know about the snap, but if you add Stellarium's PPA to your apt sources, you can install the latest Stellarium that way. 

```
sudo snap remove stellarium
sudo add-apt-repository ppa:stellarium/stellarium-releases
sudo apt update
sudo apt install stellarium
```

OK thanks, I was trying to avoid adding the PPA.

---

### Post by Daveski17 on 2019-06-24
> **PaulW2U said:**
> Yes, snaps automatically update. I've read somewhere that the default is that a check for updates is made four times each day.

You can force a refresh of all snaps with the command
```
sudo snap refresh
```
or for individual snaps with
```
sudo snap refresh <snap_name>
```

Thanks, that's really useful.

---

### Post by Daveski17 on 2019-06-24
@kpatz & PaulW2U , thanks for the info. I'll wait it out to see if it updates lol.

---

### Post by Daveski17 on 2019-07-09
[ATTACH=CONFIG]283597[/ATTACH]

And it's just updated!

---

