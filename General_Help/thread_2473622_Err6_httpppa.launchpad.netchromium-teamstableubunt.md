---
title: "Err:6 http://ppa.launchpad.net/chromium-team/stable/ubuntu impish Release 404 Not"
date: 2022-04-08
forum: General Help
---

### Post by WacoJohn on 2022-04-08
Error 404 not found.  See shot on the LEFT first.  Not particularly proficient.  Clear instruction on fixing is appreciated in advance.

---

### Post by ActionParsnip on 2022-04-08
[http://ppa.launchpad.net/chromium-team/stable/ubuntu/dists/](http://ppa.launchpad.net/chromium-team/stable/ubuntu/dists/)

PPA doesn't support Impish and should be removed. Not all PPAs support all releases of Ubuntu

---

### Post by oldos2er on 2022-04-08
Remove that PPA since it hasn't been updated to work with your version (impish).

---

### Post by ActionParsnip on 2022-04-08
Chromium is in the default repos. Why are you adding a PPA at all??

Also if you look at the PPA page it clearly says "deprecated"

[https://launchpad.net/~chromium-team/+archive/ubuntu/stable](https://launchpad.net/~chromium-team/+archive/ubuntu/stable)

#shrug

---

### Post by grahammechanical on 2022-04-08
The Ubuntu app store has the snap version of Chromium. May be the OP has some kind of dislike for Snap packaged apps.

Regards

---

### Post by WacoJohn on 2022-04-08
> **ActionParsnip said:**
> [http://ppa.launchpad.net/chromium-team/stable/ubuntu/dists/](http://ppa.launchpad.net/chromium-team/stable/ubuntu/dists/)

PPA doesn't support Impish and should be removed. Not all PPAs support all releases of Ubuntu

Thank you for the quick reply.  Could you possibly detail what I need to do??  Thank you again.

---

### Post by oldos2er on 2022-04-08
```
sudo add-apt-repository -r ppa:chromium-team/stable
```

---

### Post by WacoJohn on 2022-04-08
> **oldos2er said:**
> ```
sudo add-apt-repository -r ppa:chromium-team/stable
```

Thank you Very much.

Seeing other replies ... I am on a Raspberry Pi 400 running their Ubuntu.  Having a terrible time with browsers .. mostly failing to respond.  Went through FF er(?) .... a Snap release then got help to dump that for FF nonsnap and it 'ran better' but still not satisfactory.  Went to Chromium ... and not sure why but I have to run it from Terminal rather than from the 'desktop' or it runs 'busy' constantly.  My goal is to try Chromium NONSnap but this time without the help and I am failing miserably.  That brings me to this post.

After trying to do that I have to admit its over my head and I would love it if someone would help me do that.  I have another thread going on just that, but no one seems to want to help.

Thank you all for the help you have granted.  I will be back to mark as SOLVED after I fix this Repository issue.

---

### Post by WacoJohn on 2022-04-08
> [COLOR=#000000]Why are you adding a PPA at all??[/COLOR]



I don't even know what a PPA is.

---

### Post by yancek on 2022-04-09
>  I don't even know what a PPA is. 		

A web search for terms like this will often give an answer, see the site below.

[https://help.ubuntu.com/stable/ubuntu-help/addremove-ppa.html.en](https://help.ubuntu.com/stable/ubuntu-help/addremove-ppa.html.en)

---

### Post by WacoJohn on 2022-04-09
> **oldos2er said:**
> ```
sudo add-apt-repository -r ppa:chromium-team/stable
```


This has apparently solved the problem/topic of this thread.  THANK YOU!

---

### Post by oldos2er on 2022-04-09
> **WacoJohn said:**
> I am on a Raspberry Pi 400 running their Ubuntu.

It would've been helpful to know this up front. Anyway, I'm glad your problem is solved.

---

### Post by WacoJohn on 2022-04-09
Yeah.  I have not figured out how to roll back time.  Thanks ... for everything.

---

