---
title: "Timekpr: Disable notifications?"
date: 2015-12-17
forum: General Help
---

### Post by michigogo on 2015-12-17
Hey all, 
I was wondering if there was anyway to disable the notifications poping up at the top right corner of my screen when timekpr displays how much time I got left? 
Here is a picture:
[http://cdn.makeuseof.com/wp-content/uploads/2014/06/timekpr_timeleft.jpg?77608b](http://cdn.makeuseof.com/wp-content/uploads/2014/06/timekpr_timeleft.jpg?77608b)

Thank you!

---

### Post by XBNCPRk on 2015-12-17
You can remove the notify-osd package, but that will disable all popup notifications not just those for timekpr.

---

### Post by michigogo on 2015-12-18
And how do you do so?
Thx

---

### Post by howefield on 2015-12-18
Open up the Software Centre and search for notify-osd.

Click on the resulting "*Daemon that displays passive pop-up notifications*" and then the remove button. It can always be reinstalled by reversing this process if needs be.

or from the command line

```
sudo apt-get remove notify-osd
```

---

### Post by michigogo on 2015-12-18
Well thank you sir.

---

