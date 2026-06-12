---
title: "[SOLVED] Ubuntu downloads slow"
date: 2007-11-05
forum: General Help
---

### Post by MikeBenza on 2007-11-05
Has anyone else noticed that downloading from us.archive.ubuntu.com recently is really slow?  It's basically been slow since Gutsy came out.  I think by now people have stopped pounding Canonical's servers so much that they slow.  I'm on a major research university connection and we're not capped, yet I'm still getting only 80kbps down from us.archive.ubuntu.com, whereas a few weeks ago I could get 5 times that.

- Mike Benza

---

### Post by kshane on 2007-11-05
> **MikeBenza said:**
> Has anyone else noticed that downloading from us.archive.ubuntu.com recently is really slow?  It's basically been slow since Gutsy came out.  I think by now people have stopped pounding Canonical's servers so much that they slow.  I'm on a major research university connection and we're not capped, yet I'm still getting only 80kbps down from us.archive.ubuntu.com, whereas a few weeks ago I could get 5 times that.

- Mike Benza

You need to change the download source.  I believe if you go to System>Administration>Software Sources and got to Download From and choose Other, there's an option to Select Best Server.  It will test the connect speeds for you with different servers and allow you to get some better speeds.

Kevin

---

### Post by MikeBenza on 2007-11-05
> **kshane said:**
> You need to change the download source.  I believe if you go to System>Administration>Software Sources and got to Download From and choose Other, there's an option to Select Best Server.  It will test the connect speeds for you with different servers and allow you to get some better speeds.

Kevin


That's an amazing tenfold increase.  Thanks.

---

### Post by kshane on 2007-11-05
> **MikeBenza said:**
> That's an amazing tenfold increase.  Thanks.

Any time!

Kevin

---

### Post by daengbo on 2007-11-06
You can also choose the default server, which appears to round-robin the download, and you'll get a different server every time.

---

### Post by BrianElliott0218 on 2007-12-24
I haven't found this one to resolve the issue for me.  I got slightly faster downloads for a brief period of time, but the DL's are still only around 30 to 50kpbs.  That doesn't seem right for a machine that is on cable.

So now I have tweaked Firefox (no more IPV6), selected "find best server" for source servers, and I have deselected and reselected my network card to reset it.

Nothing seems to make the average speed of downloads come close to the speeds I get on my WinXP box (not a dual boot system, I have multiple machines).

Any help would be greatly welcome!  I really don't want to stop using Linux due to an issue that I heard Linux beats the pants off of Windoze.
~BE:confused:

---

