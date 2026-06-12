---
title: "Evolution-EWS keeps &quot;refreshing folder inbox&quot; perpetually"
date: 2015-02-11
forum: General Help
---

### Post by timonoj on 2015-02-11
Hi guys,

I'm trying to set evolution to connect to my work account. It fetches properly the Host URL of the server (that is, I write the .com address and after checking my account it finds the real /ews/exchange.asmx address). It authenticates correctly, downloads the mailbox tree....And starts downloading. It starts somewhere from beginnings of last year up until June 2014. It stops there. It starts downloading mails for offline mode, and that percentage keeps slowly climbing to 100%, then back to start again. And again. And again...it just keeps downloading more and more offline messages. Meanwhile the app keeps also "refreshing folder 'Inbox', this one never changes the status. Screenshot of the status bar:
[ATTACH=CONFIG]259925[/ATTACH]

So, the part that it already downloaded, it's good and it's accessible, I can see the emails. However I don't get past June 2014, for some reason. I tried deleting everything and starting again, but the result is the same (it downloads always up to the exact same email/date). 

Not related, but the calendar seems to finish sync correctly, and I can see today's events properly. 

Any ideas/suggestions? I'd love to get rid of the VM that I only need because of goddamn outlook.

EDIT: Just checked the .cache/evolution/mail folder, it already weights 3.4GB, while the outlook .ost file with all the mailboxes fully downloaded only takes 2.2GB. This can mean just less compression/worse arrangement for the storage, but could be something...
Thanks!

---

### Post by timonoj on 2015-02-12
Oh...But it does sync! Since the last post a couple of days ago, I noticed that it downloaded some more emails. Each time it makes an offline files download, I saw some more emails appearing. I've seen it slowly growing at a snail pace...It already reached this week's monday, with a bit of luck it will reach today's email within the day...Mygosh, a 3 days sync. That's...something.

---

