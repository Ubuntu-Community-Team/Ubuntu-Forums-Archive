---
title: "SNAP keeps trying to install AVAHI, Bluetooth - Don't  have Bluetooth"
date: 2021-07-26
forum: General Help
---

### Post by Rick St. George on 2021-07-26
Don't have bluetooth on my Desktop, Don't want Avahi. 
Why does SNAP persist in installing these? Who started this (*&*&%&) as Ubuntu is NOT installed on Cellphones ! ! !
And yes I purged AVAHI and Bluetooth and Bluez.

What do I have to do ... Purge SNAP from v20.04 (to which I just upgraded to) ? ? ?

Any work arounds to this SNAP thing?

---

### Post by HermanAB on 2021-07-26
To my mind, Snap is an unwanted solution to a nonexistent problem.  You can safely uninstall it.  I always do.

---

### Post by monkeybrain20122 on 2021-07-26
It is easy to purge snap.

```
sudo apt purge snapd
sudo apt autoremove --purge
sudo rm -rf /var/cache/snapd
```

Then remove the snap stuffs from your $HOME as well (no sudo)


```
rm -rf ~/snap 
```


Mind you, some packages that you install with apt might actually be a script that install the snap version of the software, in that case it will install snapd and all the snap stuffs again, so read the outputs of what will be installed when you do sudo apt install x, but then the only package that I am aware of that does that is Chromium.

---

### Post by Rick St. George on 2021-07-26
Thanks, but I don't have, and will never download/install, Chromium. 
Can you check this Post as to what Snap did regarding my Video Driver?
[https://ubuntuforums.org/showthread.php?t=2465231]("https://ubuntuforums.org/showthread.php?t=2465231")

Its greyed out in Additional Drivers and can't select the right driver Nvidia 390.

I will uninstall SNAP.  Thanks!

---

### Post by Rick St. George on 2021-07-26
Thanks, but I don't have, and will never download/install, Chromium. 
Can you check this Post as to what Snap did regarding my Video Driver?
[https://ubuntuforums.org/showthread.php?t=2465231]("https://ubuntuforums.org/showthread.php?t=2465231")

Its greyed out in Additional Drivers and can't select the right driver Nvidia 390.

I will uninstall SNAP.  Thanks!

---

