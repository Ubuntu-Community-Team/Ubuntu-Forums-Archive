---
title: "Quick script to restart network"
date: 2016-08-12
forum: General Help
---

### Post by wjbmd48 on 2016-08-12
Hi:

I frequently have to restart my network to maintain my connection.  So I open terminal, 

sudo service network-manager restart

enter my password

and everything's back to normal

What I'd like is a fast button that runs that as a script that I can put in my panel, get it done with one click.

Is there a way to do that?

Thanks,

Bill

---

### Post by 1clue on 2016-08-12
Yes, but a more appropriate question would be, why does your connection drop?

Rather than mess with sudoers file I would try to debug your real problem.

---

### Post by 1clue on 2016-08-12
```
%somegroup ALL=NOPASSWD:/usr/sbin/service network-manager restart
```

If that goes into /etc/sudoers (change somegroup to a group of your choice) then logout of your session.  When you login you should be able to run the command without a password.

Once you can do that, you can create a screen widget or script which runs it.

---

### Post by wjbmd48 on 2016-08-14
Excellent, thanks so much!

The problem isn't that I'm dropping my network, but rather that I'm running two wireless devices, my system's old B/G card and a newer B/G/N PCMCIA device, and they interfere. Is there a way to toggle only the internal device off?  The hardware on my Thinkpad X40 allows me to turn off both, but not each individually.

Thanks again!

Bill

---

### Post by 1clue on 2016-08-14
[http://askubuntu.com/questions/168032/how-to-disable-built-in-wifi-and-use-only-usb-wifi-card](http://askubuntu.com/questions/168032/how-to-disable-built-in-wifi-and-use-only-usb-wifi-card)

---

### Post by wjbmd48 on 2016-08-14
Bingo!

Thanks so much,

Bill

---

