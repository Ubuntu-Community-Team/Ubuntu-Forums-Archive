---
title: "Getting sendmail working in 7.10"
date: 2007-12-31
forum: General Help
---

### Post by diyfiesta on 2007-12-31
Hi Folks,

Bit of a newbie question really so bear with me! I want to be able to send emails from my ubuntu box (have the box as an SMTP server for use with apps and/or use mailx from the command line). On a previous Fedora box, sendmail just worked out of the box and I'd get mails from [email]me@localhost.loca[/email]ldomain, which is fine as I don't want my ubuntu box to have a specific "identify", I just want to send admin type mails out (you know, any odd in the logs, that kind of thing), so [email]me@localhost.loca[/email]ldomain would be fine.

However, after doing an "sudo apt-get install sendmail mailx", it doesn't just work out of the box and I'm at a bit of a loss!

People seem to recomend postfix here over sendmail claiming its easier to setup, but I can't find an easy / simple how too... it *all* looks really involved to setup.

So, can anyone give me any tips, links to general guides / howtos? for sendmail or postfix, and all I want to do here is send emails out, have the SMTP server setup but I don't need to have a fully registered mega-server, I just want to send admin emails out. Does that make sense?

Anyway, thanks for any tips,
Toby

---

### Post by diyfiesta on 2007-12-31
some output from mail.log if you're interested. I'm probably more interested in general tips / howtos / howto configure sendmail, but if this highlights something obvious, great :)

> Dec 30 19:40:18 localhost sm-mta[14317]: lBUJeIFE014317: to=<toby@localhost.localdomain>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent
Dec 30 19:42:20 localhost sm-mta[14315]: lBUJe1FI014310: to=<dave@gmail.com>, ctladdr=<toby@localhost.localdomain> (1000/1000), delay=00:02:19, xdelay=00:02:19, mailer=esmtp, pri=120340, relay=gsmtp183.google.com. [64.233.183.27], dsn=5.0.0, stat=Service unavailable
Dec 30 19:42:20 localhost sm-mta[14315]: lBUJe1FI014310: lBUJgKFE014315: DSN: Service unavailable
Dec 30 19:42:20 localhost sm-mta[14315]: lBUJgKFE014315: to=<toby@localhost.localdomain>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent
Dec 31 11:53:39 localhost sendmail[16030]: lBVBrdvC016030: from=toby, size=44, class=0, nrcpts=1, msgid=<200712311153.lBVBrdvC016030@localhost.localdomain>, relay=toby@localhost
Dec 31 11:53:39 localhost sm-mta[16031]: lBVBrd1d016031: from=<toby@localhost.localdomain>, size=341, class=0, nrcpts=1, msgid=<200712311153.lBVBrdvC016030@localhost.localdomain>, proto=ESMTP, daemon=MSP-v4, relay=localhost.localdomain [127.0.0.1]
Dec 31 11:53:39 localhost sendmail[16030]: lBVBrdvC016030: to=dave@gmail.com, ctladdr=toby (1000/1000), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30044, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (lBVBrd1d016031 Message accepted for delivery)
Dec 31 11:53:47 localhost sm-mta[16033]: lBVBrd1d016031: to=<dave@gmail.com>, ctladdr=<toby@localhost.localdomain> (1000/1000), delay=00:00:08, xdelay=00:00:08, mailer=esmtp, pri=120341, relay=gsmtp163.google.com. [64.233.163.27], dsn=5.0.0, stat=Service unavailable
Dec 31 11:53:47 localhost sm-mta[16033]: lBVBrd1d016031: lBVBrl1d016033: DSN: Service unavailable
Dec 31 11:53:47 localhost sm-mta[16033]: lBVBrl1d016033: to=<toby@localhost.localdomain>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent

---

### Post by Kzin on 2008-01-04
It looks to me that you are being declined forwarding because you are sending from "localhost.localdomain".  Google's servers see this and say "No thanks".

It looks like your sendmail server is actually running fine.

Try doing this

```
telnet localhost 25
ehlo domain.com
mail from:youremail@domain.com
rcpt to:dave@gmail.com
data
Subject:Testing

This is a test
.
quit

```

(Note, the empty line after subject is required.  The . on a line by itself is required. Change [email]youremail@domain.com[/email] to a real email, even [email]dave@gmail.com[/email] should work - assuming its your real email)
If you check the log, you should see Gmail accept the email =).

Now, in saying you were rc'ving emails you sent TO [email]someone@localhost.loca[/email]ldomain, do you mean you were getting them at your gmail address?  I have a tip that could help with that.  I am not too great with PostFix, but I have some sendmail tricks up my sleeve.  The more likely situation is that you were getting them on a local email account.  Can give you tips for that as well.  Let me know what you want to do with the localhost.localdomain ones.

---

### Post by diyfiesta on 2008-01-05
Hi,

Thanks for the note, thats great! I really know nothing about this stuff so it's good to talk to someone that does!

Anyway, the output of your telnet suggestion is below.

```

toby@larma:~$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 localhost.localdomain ESMTP Sendmail 8.14.1/8.14.1/Debian-8ubuntu1; Sat, 5 Jan 2008 10:25:01 GMT; (No UCE/UBE) logging access from: localhost.localdomain(OK)-localhost.localdomain [127.0.0.1]
ehlo gmail.com
250-localhost.localdomain Hello localhost.localdomain [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP
mail from:toby@gmail.com
250 2.1.0 toby@gmail.com... Sender ok
rcpt to:toby@gmail.com
250 2.1.5 toby@gmail.com... Recipient ok
data
354 Enter mail, end with "." on a line by itself
Subject:Testing

This is a test, oh yeah!
.
250 2.0.0 m05AP1Ii000430 Message accepted for delivery
quit


```

I typed it up as  literally as I could using a valid email and domain wherever I saw "domain" etc in your example. I'm not really sure about the whole domain thing. I don't have the machine setup on a domain as such, its just sort of there. Like I say this was fine when I ran Fedora and I don't really need it now (at least I think I don't!).

The tail of the mail.log show

```

Jan  5 10:24:57 localhost sm-mta[426]: m05AOgm4000426: localhost.localdomain [127.0.0.1] did not issue MAIL/EXP$
Jan  5 10:25:58 localhost sm-mta[430]: m05AP1Ii000430: from=toby@gmail.com, size=42, class=0, nrcpts=1, $
Jan  5 10:25:58 localhost sm-mta[432]: m05AP1Ii000430: to=toby@gmail.com, delay=00:00:19, xdelay=00:00:0$
Jan  5 10:25:58 localhost sm-mta[432]: m05AP1Ii000430: m05APwIi000432: DSN: Service unavailable
Jan  5 10:25:58 localhost sm-mta[432]: m05APwIi000432: to=toby@gmail.com, delay=00:00:00, xdelay=00:00:0$

```

In receiving mails, I'm not worried about my Ubuntu box getting emails, just sending out admin type ones. In my previous post, when I meant to say was that on Fedora before, when it did send out emails (to say my gmail account), it would come from "toby@localhost.localdomain", I don't think I ever tried replying to it... :)

Thanks again

---

### Post by Kzin on 2008-01-07
> **diyfiesta said:**
> Hi,
I typed it up as  literally as I could using a valid email and domain wherever I saw "domain" etc in your example. I'm not really sure about the whole domain thing. I don't have the machine setup on a domain as such, its just sort of there. Like I say this was fine when I ran Fedora and I don't really need it now (at least I think I don't!).

The domain thing is more for the sake of the receiving server.  Eliminate the possibility that it was getting rejected for spammy reasons.  Based on your output probably not I guess.  I just set up a sendmail install because I couldn't get postfix to do what I needed it to.  I did an sudo apt-get install sendmail, edited the /etc/mail/access file, ran make, rebooted sendmail and it worked, the only diff was a valid hostname.

```

Jan  5 10:24:57 localhost sm-mta[426]: m05AOgm4000426: localhost.localdomain [127.0.0.1] did not issue MAIL/EXP$

```
USUALLY this means there was an EHLO but not a MAIL FROM:
Ignoring this snippet as it is likely from a previous attempt, note date/time.

```

Jan  5 10:25:58 localhost sm-mta[430]: m05AP1Ii000430: from=toby@gmail.com, size=42, class=0, nrcpts=1, $
Jan  5 10:25:58 localhost sm-mta[432]: m05AP1Ii000430: to=toby@gmail.com, delay=00:00:19, xdelay=00:00:0$
Jan  5 10:25:58 localhost sm-mta[432]: m05AP1Ii000430: m05APwIi000432: DSN: Service unavailable
Jan  5 10:25:58 localhost sm-mta[432]: m05APwIi000432: to=toby@gmail.com, delay=00:00:00, xdelay=00:00:0$

```

Ok, going out on a limb here because I've not had to do this for some time...  Try adding ALL:127.0.0.1 to your /etc/hosts.allow. 
A DSN is generally followed up with an email to [email]postmaster@localhost.loca[/email]ldomain with more detailed error info.  You can cat /etc/mail/aliases to see where postmaster goes, usually to root, which usually goes to the first user account you created on the system.
If adding that line to the hosts.allow doesn't work, will have to get you to post your sendmail.mc and maybe track down that bounceback.

HTH :guitar:

---

### Post by BlueKnight84 on 2008-01-08
I'm having a similar problem with my Ubuntu.  I've tried .forward files and adding aliases but none of my mail works.  What is even more aggravating is that the original user does have a working .forward file, so I know Sendmail works with my system, but not with new users or with tweaks with the aliases file.  Then again, I'm a total noob.

What I'm asking is, if I posted (or emailed/IM'd) my sendmail.mc or another configuration file, would you be willing to look it over?

---

### Post by diyfiesta on 2008-01-08
Hi,

Thanks for that. I must admit I didn't understand a lot of it but cheers :D

My hosts.alllow file now looks like this

```

sendmail: localhost: allow
ALL:127.0.0.1

```

and my aliases file has the following...

```

# Added by installer for initial user
root:   toby

```

so I didn't see anything about a postmaster, however, doing a quick test and got the following in an email to toby

```

Message 1:
From MAILER-DAEMON  Tue Jan  8 08:55:53 2008
Date: Tue, 8 Jan 2008 08:55:53 GMT
From: Mail Delivery Subsystem <MAILER-DAEMON>
To: <toby@localhost.localdomain>
MIME-Version: 1.0
Content-Type: multipart/report; report-type=delivery-status;
        boundary="m088trKW016530.1199782553/localhost.localdomain"
Subject: Returned mail: see transcript for details
Auto-Submitted: auto-generated (failure)

This is a MIME-encapsulated message

--m088trKW016530.1199782553/localhost.localdomain

The original message was received at Tue, 8 Jan 2008 08:55:51 GMT
from localhost.localdomain [127.0.0.1]

   ----- The following addresses had permanent fatal errors -----
<toby@gmail.com>
    (reason: 554 Please check your SMTP server is set to smtp.orangehome.co.uk. Further help is available at http
://help.orange.co.uk/sessionBegin.do?solutionId=kb4473)

snip

--m088trKW016530.1199782553/localhost.localdomain
Content-Type: message/delivery-status

Reporting-MTA: dns; localhost.localdomain
Received-From-MTA: DNS; localhost.localdomain
Arrival-Date: Tue, 8 Jan 2008 08:55:51 GMT

Final-Recipient: RFC822; toby@gmail.com
Action: failed
Status: 5.5.0
Diagnostic-Code: SMTP; 554 Please check your SMTP server is set to smtp.orangehome.co.uk. Further help is available at http://help.orange.co.uk/sessionBegin.do?solutionId=kb4473
Last-Attempt-Date: Tue, 8 Jan 2008 08:55:52 GMT

Final-Recipient: RFC822; tweon@foo.com
Action: failed
Status: 5.5.0
Diagnostic-Code: SMTP; 554 Please check your SMTP server is set to smtp.orangehome.co.uk. Further help is available at http://help.orange.co.uk/sessionBegin.do?solutionId=kb4473
Last-Attempt-Date: Tue, 8 Jan 2008 08:55:53 GMT

--m088trKW016530.1199782553/localhost.localdomain

```

The link to orange is wrong (should be [http://help.orange.co.uk/resultDisplay.do?gotoLink=150&docType=1006&contextId=550:150.156&docPropValue=kb4473&clusterName=DefaultCluster&contentId=021a7c4f-1714-4fff-87c9-cd4832e42574&responseId=8d2e8ca9895d3ec8:100ebec:11758718228:-253b&groupId=1&answerGroup=1&score=1956&page=http://ESERVER_89815ede-42ed-4ba2-ba1c-205013980818.xhtml&result=0&excerpt=KB4473&resultType=5002#Goto150](http://help.orange.co.uk/resultDisplay.do?gotoLink=150&docType=1006&contextId=550:150.156&docPropValue=kb4473&clusterName=DefaultCluster&contentId=021a7c4f-1714-4fff-87c9-cd4832e42574&responseId=8d2e8ca9895d3ec8:100ebec:11758718228:-253b&groupId=1&answerGroup=1&score=1956&page=http://ESERVER_89815ede-42ed-4ba2-ba1c-205013980818.xhtml&result=0&excerpt=KB4473&resultType=5002#Goto150)) but it talks about setting up email POP server etc. Do I have to setup Sendmail to 'talk' with my ISP, I thought it would act like a standalone mail server?

My new log looks like this

```

Jan  8 08:55:51 localhost sendmail[16527]: m088tp63016527: from=toby, size=90, class=0, nrcpts=2, msgid=<200801080855.m088tp63016527@localhost.localdomain>, relay=toby@localhost
Jan  8 08:55:51 localhost sm-mta[16528]: m088tpKW016528: from=<toby@localhost.localdomain>, size=359, class=0, nrcpts=2, msgid=<200801080855.m088tp63016527@localhost.localdomain>, proto=ESMTP, daemon=MSP-v4, relay=localhost.localdomain [127.0.0.1]
Jan  8 08:55:51 localhost sendmail[16527]: m088tp63016527: to=tweo@foo.com,toby@gmail.com, ctladdr=toby (1000/1000), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=60090, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (m088tpKW016528 Message accepted for delivery)
Jan  8 08:55:52 localhost sm-mta[16530]: m088tpKW016528: to=<toby@gmail.com>, ctladdr=<toby@localhost.localdomain> (1000/1000), delay=00:00:01, xdelay=00:00:01, mailer=esmtp, pri=150359, relay=gsmtp183.google.com. [64.233.183.27], dsn=5.0.0, stat=Service unavailable
Jan  8 08:55:53 localhost sm-mta[16530]: m088tpKW016528: to=<tweston@foo.com>, ctladdr=<toby@localhost.localdomain> (1000/1000), delay=00:00:02, xdelay=00:00:01, mailer=esmtp, pri=150359, relay=mail2.foo.com. [66.151.244.60], dsn=5.0.0, stat=Service unavailable
Jan  8 08:55:53 localhost sm-mta[16530]: m088tpKW016528: m088trKW016530: DSN: Service unavailable
Jan  8 08:55:53 localhost procmail[16532]: Enforcing stricter permissions on "/var/mail/toby"
Jan  8 08:55:53 localhost sm-mta[16530]: m088trKW016530: to=<toby@localhost.localdomain>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent

```

Cheers again

---

### Post by Kzin on 2008-01-09
Ok that bounceback really helped.  Does your ISP block SMTP traffic?  When you had this going in Fedora, was it with the same ISP?

---

### Post by Kzin on 2008-01-09
Oh and to prevent your email address getting snatched, you should remove it from the code snippet at the bottom of your bounceback. (I notice you removed them from the top, just missed those two at the bottom)

---

### Post by diyfiesta on 2008-01-10
> **Kzin said:**
> Ok that bounceback really helped.  Does your ISP block SMTP traffic?  When you had this going in Fedora, was it with the same ISP?

A ha! I feel like we're getting to the bottom of it, when I was on Fedora I was on a different ISP! I don't know if my current one actively block stuff, I suspect they might but wouldn't know how to tell. Its Orange (free with my mobile phone) and when you phone them up, lets say, they're less than technical :)

So, would I need to setup some kind of relay, assuming they're blocking it. Setup something with the settings that the Orange support link shows?

Also, a relay doesn't mean that I'm sending mail from their mail server right? I'll still have a standalone mail/SMTP server on my box, it could be that like a firewall, their servers aren't letting traffic through?

Thanks again,
Toby

---

### Post by Kzin on 2008-01-10
This would be the next thing to try to get to the bottom of it I suppose...
```
telnet gmail-smtp-in.l.google.com 25
ehlo gmail.com
mail from:<youremail@gmail.com>
rcpt to:<youremail@gmail.com>
data
Subject:Testing

This is a test
.
quit
```
Note: you need the <>'s because google is mega RFC compliant.
So if it is firewalled that should get blocked right at the telnet level.  If it isn't blocked then we are just missing something on the sendmail configuration level.

If gmail-smtp-in.l.google.com doesn't work, do a 
```
dig MX gmail.com
```
to see what the best server is in your area.

---

### Post by diyfiesta on 2008-01-11
Hi,

I get the following, which I assume to mean it connected then kicked me off, which I assume  proves what we've been thinking?

```

toby@larma:~$ telnet alt1.gmail-smtp-in.l.google.com 25
Trying 209.85.147.27...
Connected to alt1.gmail-smtp-in.l.google.com.
Escape character is '^]'.
554 Please check your SMTP server is set to smtp.orangehome.co.uk. Further help is available at http://help.orange.co.uk/sessionBegin.do?solutionId=kb4473
Connection closed by foreign host.

```

Thanks again for your reply, top man!

---

### Post by Kzin on 2008-01-11
Indeed it does.  It would appear that your ISP is allowing the port to connect, but wastes no time in shutting it down.  We will need to attempt to use your ISP's host as a relay, if they will allow it.
[When I tried to set up PostFix to do my specialty install]("http://ubuntuforums.org/showthread.php?t=646172") I did see that there was a [way to do it in PostFix]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#relayhost"), but since we've come this far in sendmail lets keep going with it.
Lets test to see if they will let you relay at all.
Put this in your /etc/mail/sendmail.mc right above "Default Mailer Setup"
```
FEATURE(`mailertable')dnl
```

Create /etc/mail/mailertable
```
.       smtp:smtp.orangehome.co.uk
```
(The . is necessary)

In /etc/mail type
```
sudo make
```

Restart sendmail.
This will not fix localhost.localdomain, its just to test sending from your SMTP server and relaying off of theirs (see if they allow it).  Test and ping back with the results, if it works then we will set up localhost.localdomain to be delivered locally through procmail or something.

---

### Post by naghman on 2008-04-26
Hi,

I was trying to set up sendmail on ubuntu to send auto reply email to registered users.

I installed sendmail and tried the telnet exercise. Its sends an email but in the "to" field of the email it shows "undisclosed-recipients"

Is there a way to show the recipients email id as well?

Any help would be appreciated?

Thanks.

---

