---
title: "Evolution. Gmail."
date: 2008-03-04
forum: General Help
---

### Post by Roasted on 2008-03-04
SMTP works.
POP does not.
POP is enabled in my Gmail account.
I'm using pop.gmail.com + smtp.gmail.com, just as the directions said in the how-to guide I had.

When I do a send/receive, SMTP says completed. POP sits there and times out.

I'm so worn out right now that I'm sure I'm overlooking something stupid, but I wanted to post anyway. What else can I look for?

---

### Post by YldGuy on 2008-03-04
IMAP for Gmail. Look for the settings in the Gmail itself.

---

### Post by Roasted on 2008-03-04
So receive = imap.gmail.com + send = smtp.gmail.com?

imap still hangs... and yes it's enabled in my gmail settings...

---

### Post by YldGuy on 2008-03-04
Yes. and the ports.. incoming is 993. outgoing is 587 both over SSL or TLS. i forgot if its SSL or TLS. Have to get back home and check mine.

I didnt see any slowness in Gmail although my Exchange mail is bit slow.

---

### Post by Roasted on 2008-03-04
where do I set the ports? In evolution? I didn't see any place to... perhaps I should look at this tomorrow when I'm not seeing doubles from lack of sleep...

---

### Post by YldGuy on 2008-03-04
Sorry. I thought I had set those ports.. i must be daydreaming. :confused:

check this link: [http://www.linuxloop.com/gmailevolution/index.shtml](http://www.linuxloop.com/gmailevolution/index.shtml). this may help.

---

### Post by Roasted on 2008-03-04
My settings were identical, except SSL encryption. So I added it. It prompts me for a pop password now. Which password? It won't accept any of mine.

---

### Post by YldGuy on 2008-03-04
it doesn't? i had given my gmail account password. It went fine...

---

### Post by Slingshot on 2008-03-04
Try setting the port by using 

```
pop.gmail.com:995
```

 I think Gmail POP uses SSL and SMTP uses TSL but play around with these settings.

---

### Post by Roasted on 2008-03-08
Everything works now, except when I hit send/receive, it asks for an SMTP password.

I tried using my gmail login password but it rejects it. I never set any other passwords, I think. What password is it asking for? Where can I adjust it?

---

### Post by vishzilla on 2008-03-08
Why don't you try Thunderbird for a change? I love thunderbird and have no problems with Gmail/IMAP!

---

### Post by Roasted on 2008-03-08
I just installed Thunderbird. I only selected the main package from synaptic, so I assume that's all I needed. In five minutes I had both gmail accounts up and running and fully functional. VERY nice, very smooth, and the gui is great. Thanks for the advice!

---

