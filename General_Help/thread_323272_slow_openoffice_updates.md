---
title: "slow openoffice updates"
date: 2006-12-21
forum: General Help
---

### Post by TheRingmaster on 2006-12-21
Did anyone have any openoffice updates recently. I have some right now and it is taking for ever. The download speed is horrible. I am sure that it is a problem with the server.

---

### Post by tenghoward on 2006-12-21
> **TheRingmaster said:**
> Did anyone have any openoffice updates recently. I have some right now and it is taking for ever. The download speed is horrible. I am sure that it is a problem with the server.

I have the same situation as yours, but for me, it looks like large package downloading. I did install every single update though. :confused:

---

### Post by dmartinsca on 2006-12-21
yeah, did those updates this morning. I think the fastest it went was 12K/sec

---

### Post by TheRingmaster on 2006-12-21
at least I am not alone in this.

---

### Post by ByeByeBill on 2006-12-21
Whew! I thought it was me....Im downloading the update at below 1k a sec.I gave up.Hope its fixed soon.

---

### Post by Cable on 2006-12-22
Check your /etc/apt/sources.list file.  If any of your repository lines have us.archive.ubuntu.com in them, simply remove the "us." (ONLY those THREE characters) portion.  I did these updates today and they were extremely slow.  I stopped the download, edited my sources.list as stated above, and the download speeds were MUCH faster.

---

### Post by viper on 2006-12-22
I did mine last night roughly 80 mg, took about 35 min which i thought was pretty good.

---

### Post by ByeByeBill on 2006-12-22
Good one,Cable.I checked,amended,and it worked,only took about 30 minutes or so,about normal for such a large file(s).Thanks for the tip.

---

### Post by talz13 on 2007-01-04
you can also change this from the settings > repositories in synaptic.  Just go there and change where the dropdown says "Server for United States" to "Main server".  I just did that tonight, and my updates / packages sped up from about 12k/sec to over 400-500k/sec.  That's the speed I remember from before!

---

