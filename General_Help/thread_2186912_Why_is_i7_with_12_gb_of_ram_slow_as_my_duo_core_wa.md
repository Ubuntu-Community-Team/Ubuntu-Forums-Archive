---
title: "Why is i7 with 12 gb of ram slow as my duo core was when online uploading/downloading"
date: 2013-11-09
forum: General Help
---

### Post by Bushcraft Bill on 2013-11-09
OK I got what I think is a pretty scookum puter but when I am online and uploading or downloading it grinds things down to a crawl I am no better off than my duo core that I had before?
why does being on the internet suck the thing dry so everything else I try  and do on the puter is slow as molasses man it seems like I am on an 8088 puter is this just the way things are when on the internet and it dont matter what puter your using or is their something I can do so that I can accually do something else while I am uploading or downloading stuff off the internet HELP ME PLEASE!

---

### Post by tgalati4 on 2013-11-09
Slow is a relative term.  Open a terminal and install *htop* and see what is going on:

```
sudo apt-get install htop
htop
```

What processes are taking up the most CPU time?

---

### Post by Bushcraft Bill on 2013-11-09
Thanks I installed it and will test things out and get back!

---

### Post by leclerc65 on 2013-11-09
Also check your Internet line with speedtest.net or something. 
You might get throttled by your ISP.

---

