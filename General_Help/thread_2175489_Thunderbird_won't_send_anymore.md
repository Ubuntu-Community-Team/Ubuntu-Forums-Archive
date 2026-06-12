---
title: "Thunderbird won't send anymore"
date: 2013-09-19
forum: General Help
---

### Post by Windoze Refugee on 2013-09-19
Hi Folks.
I've been using Thunderbird as my email client for over a year with no major probs. 
Today, for no apparent reason, it has just suddenly stopped sending emails. No error message just click the 'send' button and...nothing. 
No repsone of any kind. 
I've restarted Thunderbird and rebooted Ubuntu twice, to no avail.
Anyone got any ideas?
Cheers
WR

---

### Post by Kirboosy on 2013-09-19
What email service are you using? If its a private email server you might want to reach out to the provider and see if they recently made any changes to the mail server. 

I would check with them first.

---

### Post by Windoze Refugee on 2013-09-19
Thanks for your reply caboose885. 
I really dont think that can be the problem, because in that case I would expect at least an attempt to send the emai, followed by an error message. 
What is happening is the email does not leave the screen. You click send, and NOTHING  happens. 
Im suspecting a bug, or (god forbid) virus or hacking activity?

---

### Post by Kirboosy on 2013-09-19
I would say its a bug. I don't think its a virus or hacking activity. 

Have you recently updated thunderbird? Also is there a bunch of messages building up in your outbox folder?

---

### Post by Windoze Refugee on 2013-09-19
No, no recent update. And no outbox buildup - like I said, It wont even begin to send emails. I did add a new email account yesterday though...

---

### Post by whitesmith on 2013-09-19
Is the cache full? Try emptying it. [edit]You didn't happen to change the password yourself, did you?

---

### Post by Kirboosy on 2013-09-19
You could try setting up a new profile and see if that one works. If it does then you have a bad profile and should just delete the old profile.


[Profile Manager]("http://kb.mozillazine.org/Profile_manager#Linux")[URL="http://askubuntu.com/questions/128036/how-to-run-firefox-profilemanager-with-unity"]
[/URL]
```
thunderbird -profilemanager
```

that should do the trick

---

### Post by Windoze Refugee on 2013-09-19
I've tried running t-bird in safe mode with the add-ons disabled, and that seems to ave done the trick. Clearly something recently added is messing around with it. Now if I can only find out what.....

---

### Post by whitesmith on 2013-09-19
Now you're halfway home. Enable add-ons one by one, until you discover which causes the problem.

---

### Post by Windoze Refugee on 2013-09-19
EDS contact integration 0.6 was the guilty element. Now disabled and all running smoothly. Ta :)

---

### Post by John_A._Mason on 2013-09-27
I was having the EXACT same behavior after an out-of-sight update on the 13th of this month. Haven't been able to get it to work since. Finally saw this post, bingo. Disabled the EDS contact integration add-on and it now sends every time.

It was hard to research this one because there was no error, no movement, no lost mail, nothing.... it just ignored the "send" command altogether.

---

