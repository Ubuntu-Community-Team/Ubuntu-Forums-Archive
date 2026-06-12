---
title: "How to troubleshoot an external website timeout problem"
date: 2012-12-26
forum: General Help
---

### Post by eadwacer on 2012-12-26
What tools can I use to watch what my system is doing when it times out while waiting to log on to a website?

My Ubuntu machines are having trouble logging in to a number of external websites. Happens with both Firefox and Opera. I'll get a blank page and then a server timeout. This just started a couple of weeks ago. Before that, for a good six months, everything worked fine, and there have been no config changes other than standard patches.  

Modem logs show a few dropped packets, and once a 204 error, but nothing directly associated. 

CenturyLink has checked the lines and the DSL and they are fine.

Happens on two different flavors of Ubuntu (10 and 12) and two different browsers (Firefox, Opera). Doesn't happen on all websites. WordPress don't work. gMail works.

---

### Post by fdrake on 2012-12-26
> **eadwacer said:**
> What tools can I use to watch what my system is doing when it times out while waiting to log on to a website?

My Ubuntu machines are having trouble logging in to a number of external websites. Happens with both Firefox and Opera. I'll get a blank page and then a server timeout. This just started a couple of weeks ago. Before that, for a good six months, everything worked fine, and there have been no config changes other than standard patches.  

Modem logs show a few dropped packets, and once a 204 error, but nothing directly associated. 

CenturyLink has checked the lines and the DSL and they are fine.

Happens on two different flavors of Ubuntu (10 and 12) and two different browsers (Firefox, Opera). Doesn't happen on all websites. WordPress don't work. gMail works.
wireshark , netstat
```

sudo apt-get install wireshark
#also a good update doesn't hurt
sudo apt-get update

```

---

### Post by eadwacer on 2012-12-29
> **fdrake said:**
> wireshark , netstat
```

sudo apt-get install wireshark
#also a good update doesn't hurt
sudo apt-get update

```

Thanks. I got wireshark, learned a lot of stuff, and managed to capture a couple examples of fails -- we could see the packets being dropped. The telco techs worked pretty hard on their side. One spent half a day in the house trying to figure it out. Unfortunately they couldn't come up with an answer other than that it's an 'ethernet port configuration problem'.

It only impacts sites with passwords, and not all of them and not all the time. It also doesn't seem to impact my Win7 machine. For example, I am typing this on the Win7 box, because I tried three times to answer this thread on my Linux box and failed each time.

In any event, your suggestions helped. I learned a lot. Now I have to go learn more stuff, about ports.

---

