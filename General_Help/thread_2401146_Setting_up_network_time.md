---
title: "Setting up network time"
date: 2018-09-14
forum: General Help
---

### Post by webmiester on 2018-09-14
Hi everyone

How do I get my computers to get their date and time from a computer or server within my network?

I would prefer command line inputs if possible.

Thank you.

---

### Post by TheFu on 2018-09-14
I use NTP.  It is best to have 3 NTP servers fed from stratum 1 sources or 3 different GPS devices, then all the clients would use those 3 ntp servers.

NTP is supports by all network clients that I know.  I originally setup my NTP server at home because Windows couldn't keep time and was constantly losing 15+ minutes a day. The exact same hardware running Linux didn't have any time issues. Using internet sources for time too often is considered rude and can lead to your clients being blocked. Anyways, I've forced Windows systems to update their time more and more often hoping to address the issue. Every 4 hrs wasn't often enough.  Every 2 hrs wasn't either when all my other systems were basically 0.01 sec accurate, just Windows was 5+ minutes off.  Eventually, I settled on Windows time being updated 15 minutes.  That finally solved it and has been working about 8 yrs.  The initial Windows problem happened around 1997.  Not all Windows systems can't keep time.

NTP is extremely easy to setup in a non-secure way.  There are newer time servers which address security issues, but I've never used them.  Having accurate time is extremely critical to security and encryption for client/server connections.

[https://help.ubuntu.com/lts/serverguide/NTP.html.en](https://help.ubuntu.com/lts/serverguide/NTP.html.en) - google "ubuntu ntp server" to find it and other guides.

Some virtualization solutions include time services, so using NTP on those wouldn't be the best answer.

---

### Post by webmiester on 2018-09-15
Thank you so much.  I'll go read on your link

---

### Post by jbcohen on 2018-09-15
Related question: how do I change the clock from 24hr to 12hr?

---

### Post by #&amp;thj^% on 2018-09-15
> **jbcohen said:**
> Related question: how do I change the clock from 24hr to 12hr?

Not really related but:
12-hour:
```


gsettings set com.canonical.indicator.datetime time-format 12-hour
```

24-hour:
```
gsettings set com.canonical.indicator.datetime time-format 24-hour
```



options are:

locale-default
12-hour
24-hour
custom

---

### Post by webmiester on 2018-09-15
> **TheFu said:**
> I use NTP.  It is best to have 3 NTP servers fed from stratum 1 sources or 3 different GPS devices, then all the clients would use those 3 ntp servers.

NTP is supports by all network clients that I know.  I originally setup my NTP server at home because Windows couldn't keep time and was constantly losing 15+ minutes a day. The exact same hardware running Linux didn't have any time issues. Using internet sources for time too often is considered rude and can lead to your clients being blocked. Anyways, I've forced Windows systems to update their time more and more often hoping to address the issue. Every 4 hrs wasn't often enough.  Every 2 hrs wasn't either when all my other systems were basically 0.01 sec accurate, just Windows was 5+ minutes off.  Eventually, I settled on Windows time being updated 15 minutes.  That finally solved it and has been working about 8 yrs.  The initial Windows problem happened around 1997.  Not all Windows systems can't keep time.

NTP is extremely easy to setup in a non-secure way.  There are newer time servers which address security issues, but I've never used them.  Having accurate time is extremely critical to security and encryption for client/server connections.

[https://help.ubuntu.com/lts/serverguide/NTP.html.en](https://help.ubuntu.com/lts/serverguide/NTP.html.en) - google "ubuntu ntp server" to find it and other guides.

Some virtualization solutions include time services, so using NTP on those wouldn't be the best answer.

I read the guide, but it doesn't seem to answer my question.  I'll think my question could be made clearer...  I'll make it clearer.  Here goes:

1 of my computers (let's name it 123.123.123.1) has a CMOS battery on and it takes notes of time quite well.  I want all the Linux computers in my network to get their time from this computer (123.123.123.1) and not from some internet computer. How do I do this?  The guide I read seems to show how to shncronize my computer's time with time servers on the internet.  What I would like to do is to synchronize the time with a specific computer on my local network.  Thank you

---

