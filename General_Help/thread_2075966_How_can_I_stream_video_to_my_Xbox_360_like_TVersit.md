---
title: "How can I stream video to my Xbox 360 like TVersity for WIndows?"
date: 2012-10-25
forum: General Help
---

### Post by kenmore on 2012-10-25
So, for years I've been using TVersity on Windows and it allows me to stream my videos on my desktop to my Xbox 360; how can I do this on Linux?

Thanks.

---

### Post by evilsoup on 2012-10-25
The best & easiest software I've found for this is ps3mediaserver (don't worry, despite the name it works fine on the xbox). Unfortunately, it isn't in the repositories (for 12.04 at least), so you need to add the PPA.

In a terminal (ctrl+alt+T), type

```
sudo add-apt-repository ppa:happy-neko/ps3mediaserver && sudo apt-get update
```

You'll need to put in your password. To install it,

```
sudo apt-get install ps3mediaserver
```

Or you can go through the software centre - you can also add the PPA in the software too, but I can't remember exactly how.

The software itself is pretty easy to use. You have to go to the 'navigation/share settings' tab to add folders to the media server, and don't forget to click 'save' after any changes or it will forget what you've done after quitting. Oh, and you'll have to click 'restart server' after adding folders for it to take effect.

When ps3mediaserver is active, if your Xbox is on the same wireless network, it should show up by magic.

---

### Post by Psychobudgie on 2012-10-25
> **evilsoup said:**
> The best & easiest software I've found for this is ps3mediaserver (don't worry, despite the name it works fine on the xbox). Unfortunately, it isn't in the repositories (for 12.04 at least), so you need to add the PPA.

In a terminal (ctrl+alt+T), type

```
sudo add-apt-repository ppa:happy-neko/ps3mediaserver && sudo apt-get update
```

You'll need to put in your password. To install it,

```
sudo apt-get install ps3mediaserver
```

Or you can go through the software centre - you can also add the PPA in the software too, but I can't remember exactly how.

The software itself is pretty easy to use. You have to go to the 'navigation/share settings' tab to add folders to the media server, and don't forget to click 'save' after any changes or it will forget what you've done after quitting. Oh, and you'll have to click 'restart server' after adding folders for it to take effect.

When ps3mediaserver is active, if your Xbox is on the same wireless network, it should show up by magic.

I don't think a repo for 12.10 has been added yet, however you can grab a inclusive deb file for the latest build from the ps3mediaserver forums linux section under Ubuntu Friendly I seem to recall.

---

