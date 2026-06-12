---
title: "How to enable networking in recovery mode?"
date: 2016-09-10
forum: General Help
---

### Post by CantankRus on 2016-09-10
In 14.04 the enable networking option in recovery mode didn't work but
was able to use the "drop to root shell" option and
mount / as rw with...
```
mount -o remount,rw /
```
and enable networking with ...
```
dhclient eth0
```

ifconfig tells me my interface is now enp3s0 but
```
dhclient enp3s0
```
does not enable networking.

Additionally when I'm in the root shell it seems to timeout and appears to be rebooting where I have to [**_reisub_**]("https://en.wikipedia.org/wiki/Magic_SysRq_key#Uses") to get out.
Is it possible to enable networking in recovery mode or is it just a complete waste of time?

---

### Post by ajgreeny on 2016-09-11
I know you have now seen [https://ubuntuforums.org/showthread.php?t=2336758&p=13543030#post13543030](https://ubuntuforums.org/showthread.php?t=2336758&p=13543030#post13543030) and posted in it so it looks as if this is now sorted for you, and hopefully others as well.

I posted here so other forum users searching for answers may find this and the link above.

If you are now happy that this really is solvedplease mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

### Post by CantankRus on 2016-09-11
May be for others but I've tried the methods stated and they don't work for me.
Something seems to be amiss.
If I just let the recovery screen sit there it becomes corrupt within a couple of minutes.
Same happens after a while if I have dropped to root shell.
[ATTACH=CONFIG]271071[/ATTACH]

Doesn't matter though. I was only looking for a solution for the OP of that thread.

---

