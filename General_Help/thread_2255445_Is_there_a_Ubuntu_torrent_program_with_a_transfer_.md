---
title: "Is there a Ubuntu torrent program with a transfer cap?"
date: 2014-12-05
forum: General Help
---

### Post by ultragamer2 on 2014-12-05
In the utorrent program on windows there is a setting for a transfer cap.

Do any of the Ubuntu torrent programs have a similar setting?

---

### Post by Lars Noodén on 2014-12-05
transmission has by default the ability to stop seeding once a certain ratio is met.  That means a little bit of calculation but you can use it to stop after a certain amount of GB.  It also can limit by time of day.

---

### Post by sudodus on 2014-12-05
I use Transmission. Do you mean maximum speed by cap? It can be set in a menu of Transmission. There can be two levels, or for the time of day, when you want to give other things priority, and another (typically higher level) or no limit at all.

---

### Post by ultragamer2 on 2014-12-05
Thanks.

No I mean is there a way to get it to stop downloading or uploading when it has transfered a total amount of say 10gb for example.
So you don't go over your ISP monthly limit and then you have slow internet for the rest of the month.

---

### Post by sudodus on 2014-12-05
Then I think the tip by *Lars Noodén* in the previous post is the best alternative. Tick the box and select a suitable (low) level of 'Stop seeding at ratio' according to the attached screenshot.

Maybe you should also look at some other torrent clients available for linux. The following link recommends ***Deluge***

[http://codecondo.com/top-linux-bittorrent-clients/](http://codecondo.com/top-linux-bittorrent-clients/)

(I have not tried it, but I think it is worth trying for you.)

---

### Post by nerdtron on 2014-12-05
Yup. Transmission is quite basic but it gets the job done most of the time.
If you need more options, you may want to try Deluge. If you are using KDE, kTorrent is also good.

---

