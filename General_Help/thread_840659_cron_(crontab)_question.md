---
title: "cron (crontab) question"
date: 2008-06-25
forum: General Help
---

### Post by Krupski on 2008-06-25
Hi,

I'm running Ubuntu 8.04 Server (64 bit) in a home built Network Attached Storage box.

I have an entry in 'crontab' to reboot the server every day at 0400 (4:00 AM) and I also wish to log the reboot.

So, here are the entries I have:

```

# reboot server every day at 0400
  00    04      *       *       *       root    /bin/echo -n 'Reboot at: ' >> /var/log/reboot.log
  00    04      *       *       *       root    /bin/date >> /var/log/reboot.log
  00    04      *       *       *       root    /sbin/shutdown -r 5

```

Notice the first entry that puts the string "Reboot at: " into the file, then the second entry that puts the date immediately after on the same line.

My question is this: Are 'crontab' entries executed in the order that they appear, or is there the chance of them getting mixed up so that instead of getting THIS:

Reboot at: Wed Jun 25 04:00:00 EDT 2008

...I might get THIS instead...:

Wed Jun 25 04:00:00 EDT 2008
Reboot at:


I know that I could avoid this by setting the first line to happen at 0359 and the next at 0400, but I would rather have it "clean" and do all at 0400.... but I need to know if the entries are executed SEQUENTIALLY.

Thanks in advance for any help!

-- Roger

---

### Post by HalPomeranz on 2008-06-25
There's no guarantee that they'll be executed in the order they're listed in the file.  Do this instead:

```

# reboot server every day at 0400
00    04      *       *       *       /bin/echo -n 'Reboot at: ' >> /var/log/reboot.log; /bin/date >> /var/log/reboot.log; /bin/shutdown -r 5

```

That'll run the three commands in the order you want at 4am (notice the semicolons separating the commands).

A more interesting question is why you're rebooting the machine every day.  You shouldn't need to do that in general.

---

### Post by Krupski on 2008-06-25
> **HalPomeranz said:**
> There's no guarantee that they'll be executed in the order they're listed in the file.  Do this instead:

```

# reboot server every day at 0400
00    04      *       *       *       /bin/echo -n 'Reboot at: ' >> /var/log/reboot.log; /bin/date >> /var/log/reboot.log; /bin/shutdown -r 5

```

That'll run the three commands in the order you want at 4am (notice the semicolons separating the commands).

A more interesting question is why you're rebooting the machine every day.  You shouldn't need to do that in general.

Awesome! Thanks! I didn't know commands could be placed on one line separated by a semicolon! Yeah.... I'm a newbie!

Thanks again!

---

### Post by cariboo on 2008-06-25
You're going to screw up your uptime numbers if you reboot every day:)

Jim

---

### Post by Krupski on 2008-06-25
> **cariboo907 said:**
> You're going to screw up your uptime numbers if you reboot every day:)

Jim

Is there any reason other than bragging rights that I should care about uptime? (serious question... not sarcasm).

Maybe I should reboot less... or maybe not at all. I'm migrating from a Windoze environment where daily rebooting was in everyone's best interest!  :D

Seriously... I also planned to put APT-GET update and dist-upgrade into the CRONTAB file and let the server update itself periodically (like maybe once a week). Of course, with those "deferred" packages, a reboot is (I think) necessary.

Am I way off base here? Remember, I'm a Linux newbie. 

Thanks for your input!

-- Roger

---

### Post by Krupski on 2008-06-25
> **HalPomeranz said:**
> A more interesting question is why you're rebooting the machine every day.  You shouldn't need to do that in general.

I'm used to Windoze... 'nuf said huh?  :D

---

### Post by HalPomeranz on 2008-06-25
> **Krupski said:**
> Is there any reason other than bragging rights that I should care about uptime? (serious question... not sarcasm).

I think it's mostly a "if it ain't broke, don't fix it" attitude.  Obviously if the machine has some important business function then you want to reboot it as little as possible, but for a personal machine at home, this is probably less important.

I suppose you could make the argument that rebooting the machine puts more stress on the hardware and probably consumes a bit more power than just leaving the box running, but I think it's probably insignificant.

But, yeah, bragging about an uptime of several hundred days is pretty darn cool...  :-)

> **Krupski said:**
> 
Seriously... I also planned to put APT-GET update and dist-upgrade into the CRONTAB file and let the server update itself periodically (like maybe once a week). Of course, with those "deferred" packages, a reboot is (I think) necessary.


You might be interested in this thread:

[http://ubuntuforums.org/showthread.php?t=840548](http://ubuntuforums.org/showthread.php?t=840548)

---

### Post by Krupski on 2008-06-26
> **HalPomeranz said:**
> You might be interested in this thread:

[http://ubuntuforums.org/showthread.php?t=840548](http://ubuntuforums.org/showthread.php?t=840548)

Ah yes... that's what I wanted to do. Thanks!

-- Roger

---

