---
title: "Increase linux-swap size"
date: 2017-07-11
forum: General Help
---

### Post by damnporthos on 2017-07-11
Recently, I have noted that when I close down my laptop, it doesn't suspend nor hibernate and thus my bettery dies really quickly. After checking some posts over the topic and trying a set of commands to activate the function, I stepped into this one: [https://askubuntu.com/questions/768136/how-can-i-hibernate-on-ubuntu-16-04](https://askubuntu.com/questions/768136/how-can-i-hibernate-on-ubuntu-16-04).

After checking my partition's status, I found out that the swap one was about half the size it should be:[IMG]http://i.imgur.com/QfeIQjh.png[/IMG]

I do not remember how, but some weeks ago I was able to remove these 3.81 GB from /home in order to access Intel Rapid Start Technology.

Unfortunately, now I haven't be able to reduce /home's size nor increase linux-swap. (The contrary is possible though)
I also can't unmount /home. 

I'm using Ubuntu Gnome 16.04.2 LTS on this laptop: [https://support.hp.com/us-en/document/c03605161/?docNotFound=true](https://support.hp.com/us-en/document/c03605161/?docNotFound=true)

---

### Post by jim_deadlock on 2017-07-12
You can't unmount /home while you're using it. You have to boot a live session from DVD/USB and then you'll be able to manipulate it via Gparted.

Make sure you back up your stuff first though, what you're about to do can potentially go badly, I would also suggest that when you shrink your /home make the gap at the end, not the start, it's easier for Gparted to do it that way, less chance of mishap.

EDIT: by the way, your swap partition is not in use, are you aware of that? If not then maybe it's not the size of it that's the problem, just the fact that it's not in use. If this is the case then you can enable it like so....

Identify the UUID of your swap partition:
```
sudo blkid
```

Edit /etc/fstab with sudo and add:
```
UUID=<your uuid> none            swap    sw
```

Reboot

---

