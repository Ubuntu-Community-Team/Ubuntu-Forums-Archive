---
title: "Spamassassin and Thunderbird"
date: 2006-08-02
forum: General Help
---

### Post by cssutto on 2006-08-02
Iam trying Thunderbird and I can not tell if spamassassin is working.

How do I find out?

There has to be a .log but I can't find it.

CSSJR

---

### Post by MacMan on 2006-08-03
> **cssutto said:**
> Iam trying Thunderbird and I can not tell if spamassassin is working.

There is a test email message that you can use to test if your spam filter is working correctly.

You can find the message here:
[http://spamassassin.apache.org/gtube/gtube.txt](http://spamassassin.apache.org/gtube/gtube.txt)

Try to send it to your email account and see if it is detected as spam when downloaded with Thunderbird.

I hope this helps.

Ciao.
-- 
MacMan

---

### Post by cssutto on 2006-08-04
Thanks.

It did not work.

I have spamassassin working in EVO, but I can't get it to work in Thunderbird.

Any suggestions?  Obviously I have the selection made in the junk mail tool box.

Sapmassassin is installed as per the instructions at [http://www.yrex.com/spam/spamconfig.php](http://www.yrex.com/spam/spamconfig.php)

TB filters are working very well and others have posted that spamassassin is too quick on the trigger, so maybe I should leave well enough alone.

But I would like to try and compare.

CSSJR

---

### Post by mannheim on 2006-08-04
If I understand it right, spamassassin works with the mail **server** which delivers mail to your inbox on the server. It doesn't work with the mail **client** (such as Thunderbird) directly. So there are two questions to check on:

[LIST]
[*]Is spamassassin filtering the mail?
[*]Is Thunderbird then dealing with it correctly?
[/LIST]

When spamassassin filters email, it adds headers to the email. If it thinks the mail is spam, there is a header
```
X-Spam-Satus: Yes
```
(as well as other stuff). If it is not spam, then spamassassin puts in a header like
```
X-Spam-Satus: No
```

For the first point, you can check whether your email is being filtered by spamassassin by looking for those headers: in Thunderbird, from the menu, do "View-->Headers-->All" and then look at the headers of any message (click the "+"). There's no log (I think) by default, because spamassassin reports its activity in the mail headers.

If spamassassin is filtering your mail correctly, and if it is configured to deliver the mail whatever is spam status, then you can get Thunderbird to deal with it by opening Thunderbird's "Tools-->Junk Mail Controls" and checking "Trust Junk Mail Controls" from "SpamAssassin". You should be able to check whether that is working by sending yourself some junk mail: there is a special 68-character mail text on spamassassin's web site, designed to trigger spamassassin, see [http://spamassassin.apache.org/gtube/]("http://spamassassin.apache.org/gtube/"). Just paste the sting from that web page into a mail, and send it to yourself.

---

### Post by cssutto on 2006-08-04
I have done all of that including making certain my address is not in any of the address books, sending from EVO from another ISP, etc.

Rand sudo spamd and it loads but has no effect.

Does not work.

CSSJR

---

### Post by mannheim on 2006-08-04
> Rand sudo spamd and it loads but has no effect.

If you are using Thunderbird, you need to run spamd on the machine that is your mail server, not the machine where Thunderbird is. It needs to be set up to work with procmail etc. etc. Unless you are running your own mail server, running spamd will do nothing.

---

### Post by cssutto on 2006-08-04
OK, but where do I find out how to do that?

It seems to me that it is something less than cridible to put a little box in Thunderbird that says"check here for spamassassin" when apparently in reality one has to spend hours tracking down the various steps to make it work.

I probably will go back to EVO.  It works there and was as close to 100% as you will ever get.

CSSJR

CSSJR

---

### Post by tschaboo on 2007-08-13
> **mannheim said:**
> 
If spamassassin is filtering your mail correctly, and if it is configured to deliver the mail whatever is spam status, then you can get Thunderbird to deal with it by opening Thunderbird's "Tools-->Junk Mail Controls" and checking "Trust Junk Mail Controls" from "SpamAssassin". You should be able to check whether that is working by sending yourself some junk mail: there is a special 68-character mail text on spamassassin's web site, designed to trigger spamassassin, see [http://spamassassin.apache.org/gtube/]("http://spamassassin.apache.org/gtube/"). Just paste the sting from that web page into a mail, and send it to yourself.

My mailserver runs spamassassin and does a good job marking spam, but thunderbird does not mark those messages as junk and does not move them to the Junk-folder but just leaves them in my inbox. "Trust junk mail headers set by: SpamAssassin" is marked. Any ideas?

---

