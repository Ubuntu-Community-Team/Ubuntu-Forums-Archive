---
title: "Evolution + Spam Filtering, How?"
date: 2005-07-15
forum: General Help
---

### Post by dez on 2005-07-15
Hi all, 
    I have read some threads where people have said that spam filtering doesn't work etc. So my question is, how do I continue to use Evolution and not get heaps of spam. 

    I realise that evolution needs spamassassin  (which for some reason isn't included by default), so I installed spamassassin. I have been clicking the Junk button for 3-4 weeks now, and still the most obvious of spams are coming in. I have checked my settings and evolution is allegedly Checking Incoming Mail for Spam, and also Including Remote Tests.  So I can only assume that I need to do something to tell Evolution that SpamAssassin is here, and can do this job. 

I'm obviously missing something here, Can anyone offer advice ( besides use Thunderbird)

Thanks
Des

---

### Post by tom purl on 2005-07-15
One possibility is that the spammers have been winning for the last couple of months.  My ISP uses very good spam-blocking software, but even they have been having lots of problems lately.  The current stack of anti-spam software simply isn't good enough to stop a lot of spam currently.  Personally, i'm gettting ~10 junk messages a day when I used to get < 5 a month.  

So I guess what I'm trying to say is that it's not necessarily spamassassin's fault.  Sorry I can't help any more than that.

---

### Post by dez on 2005-07-18
Its possible that Spammers are just getting really smart, but I doubt thats the only reason. 

Is there any way to check if evolution is working correctly with Spamassassin?

---

### Post by branco on 2005-09-26
[QUOTE=tom purl]One possibility is that the spammers have been winning for the last couple of months.  My ISP uses very good spam-blocking software, but even they have been having lots of problems lately.  The current stack of anti-spam software simply isn't good enough to stop a lot of spam currently.  Personally, i'm gettting ~10 junk messages a day when I used to get < 5 a month.  

So I guess what I'm trying to say is that it's not necessarily spamassassin's fault.  Sorry I can't help any more than that.[/QUOTE]

How many SPAM msgs do I get monthly? None! :razz: 

I use the bluebottle.com mail. It's a free POP mail that has the white/black-listing built into the account. (Oh, BTW, this is NOT an advertisment or an endorsement of any sorts...)  It can put a person on your white list by sending back a verification message once the mail is on the server. If the person responds (and you can choose the manner this verification is to be carried out), the address is put on the white list. An address is also put on the white lsit automatically once you send a message to it. In some cases, waiting for a verification to occur automatically is inpractical (e.g., when you're expecting an automated message) but you can check the 'Pending' folder via webmail interface and 'Allow' the mail into the Inbox (which also white-lists the sender's address)...

The only problem with this service is that the SMTP server is unreliable. Well, it's not *too* unreliable, but you don't want to take chances... So, I use a different account to send mail, and just use the 2nd account's POP server to forward mail to bluebottle.

EDIT:

If you haven't guessed already, the link is [http://www.bluebottle.com/]("http://www.bluebottle.com/")

---

### Post by makhand on 2005-09-26
[QUOTE=dez]Its possible that Spammers are just getting really smart, but I doubt thats the only reason. 

Is there any way to check if evolution is working correctly with Spamassassin?[/QUOTE]


I have the same problem. Some of the junk really is obvoius. There's absolutely no way Evolution can be 'learning junk' as it claims to be doing. It misses the same exact messages from the same senders each time. I know when I used Thunderbird, it would learn much much better. i like that Evolution has all kinds of calendaring and tasking abilities, which is why i use it. I've also considered piping all my mail through Gmail. I dont think it needs to be this difficult. There's got to be something wrong with Evolution, or at least with my configuration. I dont think its working at all, just claiming to.

i read on a webpage that one way to incorporate spamassasin is to create a filter. in the 'If' to specify 'Pipe to Program' = 'spamassassin -e' , 'returns greater than' = '0'. For 'Then', 'Move to Folder' = 'newly_created_spam_folder'. This all seems to do nothing.

Am i doing something wrong?

---

