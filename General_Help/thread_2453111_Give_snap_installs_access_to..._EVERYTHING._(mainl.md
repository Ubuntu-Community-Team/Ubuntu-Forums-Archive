---
title: "Give snap installs access to... EVERYTHING. (mainly glimpse accessing /var)"
date: 2020-11-03
forum: General Help
---

### Post by david503 on 2020-11-03
I have to begin with an opinion: I hate snap packages. Ok moving on:

Ubuntu 18.04
Glimpse 0.2.0

Ok my Glimpse can't read or save to anything in /var.  I want (for obvious reasons) to save jpg files to directories under /var/www/

How do I let it do that?   I have /var set to 777 and owned by the same user I'm running glimpse as.  I try to save (or just even view in the save dialogue) the /var directory and it still says permission denied.

Hell, how do I make *all* or *any* snap installs be able to see and write to everything everywhere it could if it wasn't a snap package. Yes, I know security is part of the whole point of snap, whatever, I don't care, I hate snap, I don't want the headache. 

Thanks.

---

### Post by yaminb on 2020-11-03
I think the first step would be to contact Glimpse Snap creators of the issue. I'm no SNAP expert, but I know that they can list various rights they need to access in snapcraft.yaml.

The other thing is you can always try to install the snap in devmode. This normally gives you more rights.
Though of course, you shouldn't do this on the regular.
snap install --devmode ...

---

### Post by TheFu on 2020-11-03
snaps cannot write anywhere except under /home/ and if the snap packaging team decided, perhaps, under /media/ and /mnt/, if we setup a "connection". Those 2 other places are not automatic.
A command:
```
$ snap connections <application-name> --all
```
[https://snapcraft.io/docs/removable-media-interface](https://snapcraft.io/docs/removable-media-interface)

There isn't any way for snaps to write anywhere else. That's part of the snap design. If this doesn't work for you, look for a PPA version of the tool.

---

### Post by david503 on 2020-11-03
Ug. Ok thanks, I'll go "complain" in the Glimpse forums.  I pity the people who have the crazy idea of using glimpse to make and edit image files that are served up to internet world wide web sites.  What an odd uncommon thing to use it for!

---

### Post by CatKiller on 2020-11-03
If the snap's author has set it up, you can use [classic confinement](https://snapcraft.io/docs/snap-confinement), which lifts the sandboxing restrictions.

Setting permissions to 777 is a terrible idea.

---

### Post by ActionParsnip on 2020-11-04
> **CatKiller said:**
> 
Setting permissions to 777 is a terrible idea.

+1

---

