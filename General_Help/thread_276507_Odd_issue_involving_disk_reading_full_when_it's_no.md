---
title: "Odd issue involving disk reading full when it's not..."
date: 2006-10-13
forum: General Help
---

### Post by Zaskoda on 2006-10-13
I was letting some torrents run in the background via ktorrent while I was browsing the web. Firefox crashed and wouldn't restart. I tried launching firefox from the prompted and got a segmentation fault. I looked around and found that my disk was reported full...

I though, "oh, those silly torrents"... but the way I understood it was that when I started the torrent download - it allocated the disk space it needed.. and I was sure I had around 10 gigs free.

So, I deleted a few big items I had on the server.. dumped the trash... and still no space..

I rebooted... it wouldn't let me log in. After I give my credentials and login, it fails to load and boots me back out to the login screen.

So I rebooted in recovery mode and got to a command prompt. When I type DF, it reports that /dev/sda1 is 100% used.

So, from the prompt.. using rm... still no space... I deleted gigs of stuff, but no space???

I didn't know how to run that utility that checks the file system so I kept rebooting until a check was forced.. no errors.

I did an apt-get dist-upgrade just in case. Some apache stuff was out of date... hrm... that was all..

I did notice that it downloaded those apache updates with no problem at all.. if the disk is full, where did it put them? Something is screwy...

Then I installed links to try to google for some answers. It installed fine but hitting "back" made it crash.. It also complained about not being able to write a config file or some nosense.

So here I am.. can't log in... deleting things does no good... I'm kind of at a loss here..

Suggestions?

---

### Post by Zaskoda on 2006-10-13
Ok.. problem solved.. I guess... Even when I had several gigs freed up, DF was reporting 100% (bad math?)... I deleted a few more gigs of crap (I've got an 80 gig drive) and eventually it let me log in.

I kept deleting things until I had over 10 gigs free. The weird thing is, df still lies!!!
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             72508184  61619156   7205728  90% /

```

Last time I checked on the calculator, that's about 85% used, not 90%. WTF?

---

