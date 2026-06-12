---
title: "[SOLVED] Flash player in Firefox not working with Certain Websites; Gutsy"
date: 2007-10-29
forum: General Help
---

### Post by tak1150 on 2007-10-29
I can play youtube and various other flash sites, but not certain other sites, such as this one:

[http://hitslot.com/?p=126](http://hitslot.com/?p=126)

I see the picture (motion picture that is not moving), but when I hit the play button, nothing happens. I have also installed flashplugin-nonfree. Does anybody have wisdom on this? Thank you!

---

### Post by Crafty Kisses on 2007-10-29
> **tak1150 said:**
> I can play youtube and various other flash sites, but not certain other sites, such as this one:

[http://hitslot.com/?p=126](http://hitslot.com/?p=126)

I see the picture (motion picture that is not moving), but when I hit the play button, nothing happens. I have also installed flashplugin-nonfree. Does anybody have wisdom on this? Thank you!

You should check your resources, see what's going on at the time:
```
top
```

---

### Post by tak1150 on 2007-10-29
Thank you for replying.

I see

firefox-bin
scsi-eth_0
hald-addon-stor
init
xorg
kthreadd
migration/0
ksoftirqd/0
watchdog/0
events/0
.....

What would you look for?

---

### Post by tak1150 on 2007-10-31
Somebody, help!

---

### Post by Maestro23 on 2007-10-31
> **tak1150 said:**
> Somebody, help!

Try disabling Watchdog or changing some settings in it and go to that site.  I just went there and it played fine for me.

---

### Post by tak1150 on 2007-10-31
Thanks for replying.
I feel a bit embarrassed about bumping the thread because I just figured it out.
What I did was I uninstalled flashplugin-nonfree and also deleted the following:
```
/home/ME/.mozilla/plugins/libflashplayer.so
```
Then I installed flashplugin-nonfree and it works!
I'll give it a day or so to make sure I'm not dreaming and mark this thread solved. Thank you guys.

Tak

---

### Post by Maestro23 on 2007-10-31
> **tak1150 said:**
> Thanks for replying.
I feel a bit embarrassed about bumping the thread because I just figured it out.
What I did was I uninstalled flashplugin-nonfree and also deleted the following:
```
/home/ME/.mozilla/plugins/libflashplayer.so
```
Then I installed flashplugin-nonfree and it works!
I'll give it a day or so to make sure I'm not dreaming and mark this thread solved. Thank you guys.

Tak

That was going to be my next suggestion. :)

Hope it works man.

---

### Post by tak1150 on 2007-11-01
> **Maestro23 said:**
> That was going to be my next suggestion. :)

Hope it works man.

It does still!
Thanks!

-marked as "SOLVED"

---

