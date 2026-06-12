---
title: "rc-local.service query"
date: 2017-08-20
forum: General Help
---

### Post by pat4 on 2017-08-20
I run two computers both with 16.04 installed. One a desktop the other a laptop.

I am still trying to learn a bit more about Ubuntu and have been looking at boot times etc. I used the command "systemd-analyze blame" on the laptop.  I was surprised to see that the "rc-local.service" was taking around forty seconds to load. The rest of the listed services were all in milli-second time range.

Now, the laptop appears to boot in around fifteen seconds and I have experienced no difficulty in using the machine straight after boot so this has prompted a couple of queries.

What exactly does the rc-local.service do?   I have tried a web search but I can't find an explanation beyond that it starts scripts executed at boot.  Is this correct?

Any idea why it should take so long to load?  Especially with no apparent adverse effects.

If it is considered necessary, that is if it would make any improvement to the operation of the laptop, is there any way to speed up loading?

I do not have the same issue on the desktop machine which also boots in around the fifteen second mark.

I stress that I don't have an issue with the laptop - I'm simply trying to improve my knowledge of Ubuntu. Any explanations - in laymans terms - would be appreciated.

Thanks.

---

### Post by Morbius1 on 2017-08-20
I don't rightly know why rc.local would take that long to process.

Is there anything in it:
```
cat /etc/rc.local
```
And what is it's current status:
```
systemctl status rc.local.service
```

---

### Post by pat4 on 2017-08-20
Thanks for your response...

Yes - here is something in it:

#Run &#8220;fstrim&#8221; at boot
LOG=/var/log/trim.log
fstrim -v / >>$LOG
echo &#8220;Time: $(date)&#8221; >>$LOG
exit 0

And its current status is Active (exited).

Obviously this is the command to run fstrim (I'm running on an SSD).  Still don't know why it should take so long to load though.

As I stated, it doesn't seem to degrade system performance and the computer boots to a usable status in around fifteen seconds.  this doesn't happen on my desktop machine also running on an SSD and using the same version of Ubuntu.

Many thanks.

---

### Post by Yellow Pasque on 2017-08-21
Did you put the fstrim there yourself? fstrim is going to take a little while to run, and Ubuntu already runs it weekly as a cron job.

---

### Post by pat4 on 2017-08-21
Yes.. When I installed Ubuntu on the laptop (from new) I read at the time that trim needed to be set up to run and followed the instructions in a web article.

I'm aware that trim is run as a cron job, but wasn't aware that it was already setup to run without intervention.  I was given to believe that I needed to set it up.  

I have learned something...
I assume then that the entry in the rc.local file is not required?  If so, can I simply delete the data?

Thanks...

---

### Post by Yellow Pasque on 2017-08-21
Yes, if you manually added it, you can delete it.

---

### Post by pat4 on 2017-08-21
> **Temüjin said:**
> Yes, if you manually added it, you can delete it.


Thank you very much for your help..  I appreciate it.

I shall mark the thread as solved.

Kind regards,

---

