---
title: "Can't get into my website - help!"
date: 2007-12-28
forum: General Help
---

### Post by stenella on 2007-12-28
Morning all,
I can't access my website to upload stuff. The server times out. My internet connection is 2Mb, allegedly. Portugal Telecom tells me its my webhosting sevice, they  tell me it's my upload speed. I don't know how to test this though. One of the speed test sites I looked at told me that it coludn't tell because of the firewall? Could this be part of the problem?

I'd be really grateful for any help as I really need to keep my website updated - it occasionally generates a bit of work.
Cheers
[http://www.frasers-art.com]("http://www.frasers-art.com")

---

### Post by LaRoza on 2007-12-28
Can you ping the site?

How are you trying to connect? What app, what port.

---

### Post by Samhain13 on 2007-12-28
Try to get in touch with your host's tech support. They might just be doing some maintenance work and have temporarily blocked FTP and/or CPanel access. This happens to me some times too. :)

edit: -- but I guess I wasn't reading.

---

### Post by stenella on 2007-12-28
How do you ping a site?

I've spoken to both my isp provider and my web hosting sevice - they point the finger at each other, butthen the ISP, Portugal Telecom admitted that it might be the pathetically slow upload speed on my connection....
I'm still trying to get through to their tech bunch but the e-mais get returned because they're 'over quota'. Brilliant, huh? Nothing like a monopoly tomake life that little bit more difficult.

---

### Post by knutschr on 2007-12-28
> How do you ping a site?

```
ping www.abcruz.com
```

In that way you will know if your machine can find the site, send something to it, and get it back.

---

### Post by Samhain13 on 2007-12-28
> **stenella said:**
> How do you ping a site?

I've spoken to both my isp provider and my web hosting sevice - they point the finger at each other, butthen the ISP, Portugal Telecom admitted that it might be the pathetically slow upload speed on my connection....
I'm still trying to get through to their tech bunch but the e-mais get returned because they're 'over quota'. Brilliant, huh? Nothing like a monopoly tomake life that little bit more difficult.

Oh man! That's not good at all.

But I can't see why your upload speed should be too much of a factor (unless you have 0) if it's only for accessing your FTP account. I will come into play once you really do transfer stuff to your host though-- and unless those files are big.

About the ping. Your site was and still is accessible. And seeing that you can post here tells me that your Internet connection is active so you should be able to reach the services of your web host-- unless they've denied access to those services for some reason.

Anyway, you can check your speed through this:
[http://www.speedtest.net/](http://www.speedtest.net/)

---

### Post by stenella on 2007-12-29
Thanks for the replies,

Tested my connection and came up with an upload speed of 102 Kbps or 0.1 Mbps (12 kB/s) and a download speed of 639 Kbps or 0.6 Mbps (78 kB/s)

Allegedly, my connection is 2Mb. I know this is compromised by us living in the middle of nowhere and the last but one connection on the line...but still. I spoke to EasySpce again and the guy I spoke to said he thought the problem was the upload speed as the time out on their server is 30 seconds, and my computer wasn't managing to log in in that time.I often get the feeling that the fact that my computer knowledge is seriously low results in me being fobbed of with tech-BS. Sapo, Portugal Telecom, is a monopoly which isn't good. I contacted them again and was referred to the small print about supply (serves you right for living in the sticks...) and told to e-mail support to see if they could raise myupload speed. the e-mail came back with the message that "The account is currently over quota" 
Joy...

Incidentally I'm using Filezilla as my FTP programme

---

### Post by Samhain13 on 2007-12-29
> Tested my connection and came up with an upload speed of 102 Kbps...

This should not be a problem. I've uploaded through FTP under much slower speeds. But from what you've just said, I think it's time for you to start looking for a new web hosting service because...

> I spoke to EasySpce again and the guy I spoke to said he thought the problem was the upload speed as the time out on their server is 30 seconds, and my computer wasn't managing to log in in that time.

...it just doesn't sound right. Hopefully, someone who has better knowledge about these things can post an opinion. I for one don't know the intricacies of such things, I just have some experience with maintaining sites. But believe you me, the upload speed you posted should be enough to maintain some sort of connection. In the past, I've been able to upload medium quality MP3's under much, much slower upload speeds (very slow dial-up connection, around 4-6 KB/s)-- it takes a very long time, but it gets there.

---

### Post by stenella on 2007-12-29
Samhain13, you've really got me thinking...I'm going to go into town on Monday and try to raise the server from the local Internet cafe - they have, I believe, faster connections. Then I'll get back on Easy Space's case....

---

