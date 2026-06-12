---
title: "system restore"
date: 2007-10-14
forum: General Help
---

### Post by hilfer on 2007-10-14
I have ubuntu on a virtaulBox.

Is there any simmilar operation like in windows called "system restore " for ubuntu ??

I mean I think I've installed something that is causing some crashes.

Can I restore my ubuntu for e previous time or date ??

---

### Post by r-mo on 2007-10-14
not afaik, in virtualbox you can create snapshots of the disk image and restore to that.  You have to create them manually though, so it's not much good to you now.

What are the symptoms of the crashes? any idea what you might have installed that's causing them?

---

### Post by hilfer on 2007-10-14
I think (almost sure ) that is deluge that's causing the crashes !!! I dont know why.
But everytime I start it it fails to start and crashes virtualbox.

How can I uninstall deluge on UBUNTU ??

---

### Post by r-mo on 2007-10-14
at the boot menu choose Ubuntu (recovery mode) that should bring you to a terminal where you're logged in as root

type
```
aptitude remove deluge-torrent
```
answer y when it asks if you're sure you want to remove it

type
```
shutdown -r now
```

deluge-torrent will now be removed and hopefully things will be working again

---

### Post by hilfer on 2007-10-14
sorry but where do I choose the ubuntu recovery mode ??

I dont see any option to do that ??

orry completely new to this.

---

### Post by r-mo on 2007-10-14
It should be there as soon as you boot, before you get the ubuntu loading screen.  You might need to press esc to get into the menu.

As an alternative if you can boot as far as the login screen press ctrl+alt+F2 when you get there.  Login to the terminal as yourself and do

```
sudo aptitude remove deluge-torrent
```

Then ctrl+alt+F7 and try logging in

---

### Post by hilfer on 2007-10-14
Ok I did it.

Tks.

---

