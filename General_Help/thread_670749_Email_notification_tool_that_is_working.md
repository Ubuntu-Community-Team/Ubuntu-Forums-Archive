---
title: "Email notification tool that is working"
date: 2008-01-17
forum: General Help
---

### Post by s0larian on 2008-01-17
I just wanted to install a little email notifier to check my IMAP mail with SSL/TLS. I thought this is an easy task, but it is not. Therefore I want to share my little experience.

First I found **mail-notification**. I installed it with apt-get from the repros. It worked really good except SSL support. I found a way around to repackage it with SSL enabled. It seemed to work really well until the next reboot. Since it takes a while for my laptop to connect wireless to the router, mail-notification already wanted to check the email before my laptop was online. An this lead to 100% CPU consumption. This was also always the case when I was periodically offline. No internet connection -> cooking CPU. The reason seemes to be  the enabled SSL support. But I don't want to check my email with blank password transmitted.

The next tool I tried was **cgmail** (download from website). It looked promising, not so many features as mail-notification, but quite ok. After installation I checked of course what happens when the internet connection was droped. And guess what: not 100% CPU power, but just no checking of email anymore. When it tries to check for email and there is no connection it just gets stucked and is doing nothing anymore. Until restarting the service, after that everything is working again.

So I went on to install the third tool: **gnubiff** (with apt-get). At first it looks not very good because of the pinguin picture with some text above (almost unreadable). But you can deactivate/change the picture and change the text you want to see shown in the gnome panel (i.e. "no mail" and "3 new mails"). The configuration tool is somehow strange compared to the others. The notification and mail preview popups also look not so good compared to the other two. And if you want to add more than one account to check it shows sometimes the add button, sometimes just a copy button for whatever reason. But this tool is acually working and if you go offline the CPU is not going to 100% and if you go online again the tool is detecting new emails without restarting the service.

So all together: gnubiff was the only tool actually working for me in a online/offline environment and with SSL support. I would have liked the other two as well, especially the hotmail support in mail-notification 5.0, but they cannot handle offline session together with SSL. If for someone plain text password transmission is ok, then I would suggest to go with mail-notification since it has more features. I didn't check anymore if cgmail handles better online/offline situations when not using SSL.

---

### Post by LeDechaine on 2008-02-12
Thanks for the info, i'm now using cGmail.

Looks like I have no mail *now* according to cGmail, which can't be true, but anyway, i'll keep it and verify if it really *works* after a reboot.

Mail-notification didn't even worked for me, always doing nothing, and I couldn't even set the "verify e-mails every (X) mins", it was locked to 5mins, not grabbing any info.

Haven't tried gnubiff yet, but if cGmail doesn't works, i'll try it. :)

---

### Post by apetresc on 2008-02-12
You may also want to check out the very spiffy app [Specto](http://specto.sourceforge.net/), which was concieved of on these very forums, and led by forum member kiddo.

It's neat, give it a try. It can notify you of a lot more than just e-mails, too.

---

### Post by LeDechaine on 2008-02-12
Thank, I may try this too. :)

Note: lmao @ «you are more than welcome to help us make Specto the most useful desktop app out there after PizzaParty ;)» :D

---

