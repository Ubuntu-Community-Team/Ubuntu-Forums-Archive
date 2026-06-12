---
title: "Cron Mailing"
date: 2007-12-09
forum: General Help
---

### Post by agentfubu on 2007-12-09
If there any way to disable cron from emailing you when tasks complete? It started spontaneously, and I've searched around a bit and couldn't find a sure answer. Having to delete 900 emails is not fun.

Thanks.

---

### Post by dcstar on 2007-12-09
> **agentfubu said:**
> If there any way to disable cron from emailing you when tasks complete? It started spontaneously, and I've searched around a bit and couldn't find a sure answer. Having to delete 900 emails is not fun.

Thanks.

Install the logcheck package recently?

---

### Post by agentfubu on 2007-12-09
No, not to my knowledge. I looked and I have no logcheck/logwatch insatalled.

I think why it just started was because I installed a new mail server, and I added a new mail account that it is now sending the emails too. So maybe it was always doing this, but failing to send the email before.

So any other ideas?

Thanks.

---

### Post by Snakob808 on 2007-12-09
Have you tried 

> sudo crontab -e

This will allow you to either create or edit your crontab.

The format is

> m h dom mon dow command 

---

### Post by Subban on 2007-12-09
You could try this, edit your crontab to have the following at the start:

```
MAILTO=""
```

It should be on a line by itself at the head of the cron jobs.

Hope that works for you.

---

