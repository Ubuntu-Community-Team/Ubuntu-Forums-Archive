---
title: "Java Applets Crash Firefox"
date: 2006-11-06
forum: General Help
---

### Post by redbluemangle on 2006-11-06
I've followed the java runtime installation guide and succeeded in installing java but when I go to a page with a java applet like(chat.intelligentmachinery.net) the applet loads up and I can even see the outline of the javachat for an instant but then firefox crashed. Not halt, nothing, firefox just vanishes. Any ideas?

---

### Post by geco on 2006-11-07
> **redbluemangle said:**
> I've followed the java runtime installation guide and succeeded in installing java but when I go to a page with a java applet like(chat.intelligentmachinery.net) the applet loads up and I can even see the outline of the javachat for an instant but then firefox crashed. Not halt, nothing, firefox just vanishes. Any ideas?
I found [this thread](http://ubuntuforums.org/showthread.php?t=286069&highlight=crash+firefox+2.0)... but it wasn't useful for me:

> **distortedstar said:**
> I was sorely dissapointed when Flash caused Firefox to crash on my brand new Edgy install, but after some searching I found a solution that solved the problem for me:

In the /etc/firefox/firefoxrc file, insert this line:
```

export XLIB_SKIP_ARGB_VISUALS=1
```

I've also seen a couple more solutions that may work for you, if this doesn't:

1. Comment out the composite section in x.org
2. Change your color depth to 24 bit, if you haven't already

Hope this post helps out some other frustrated people!

Launchpad bug discussion: 
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911)

Browsing the forums I also found a thread saying that uninstalling some firefox extensions such as Mr Tech Local Install and Cute Menus everything  worked... I did so and now I have no more crashes in firefox 2.0

byebye

---

