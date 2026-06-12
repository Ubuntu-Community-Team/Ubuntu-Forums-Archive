---
title: "Wont Stop Looping"
date: 2008-01-06
forum: General Help
---

### Post by NoobToast on 2008-01-06
I was goofing around in the Screens and Graphics menu(i have a 32inch LCD HDTV) and i set it to the reselution of the TV. Then i tested it, and i got an unsupported display box on my TV and it wouldnt go back to the log in or the desktop. Then booted it up in recovery mode and ran this code:

```
sudo dpkg-reconfigure xserver-xorg
```

when through the config and rebooted, and i got this message. And at this it kept looping. 

```

* starting defferred ececution schedulaer atd            [ok]
* starting periodic command scheduler crond             [ok]
* checking battery state                                             [ok]
* running local boot scripts                                         [ok]
```


Then it goes on to a blue screen with all these wierd symbols:

```
He display server has been shut down about 6 timees in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again on display :0.
```

HELP ME.

---

### Post by SOULRiDER on 2008-01-06
X isnt able to start, reconfigure it again.
```
sudo dpkg-reconfigure xserver-xorg
```

You might ahve messed up the video drivers.

---

### Post by NoobToast on 2008-01-06
i tried that already.

---

