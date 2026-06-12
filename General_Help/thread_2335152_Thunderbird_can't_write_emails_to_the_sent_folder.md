---
title: "Thunderbird can't write emails to the sent folder"
date: 2016-08-25
forum: General Help
---

### Post by pedro_rodriguez2 on 2016-08-25
I have only just got Thunderbird working. I can send and receive emails. After sending, Thunderbird wants to write the email to the sent folder. It cannot. I get a little window which says 'copying email to sent' but this never completes.

 If I click 'cancel', Thunderbird tells me the email has not been sent. This is not true, I have confirmed that the email has been sent and received.

How can get Thunderbird to write the mail to 'sent'??

I use qqmail, which is Tencent, a Chinese company. I just assume that Thunderbird does not have permission to copy the email to sent.

It is not sooo important but it is nice to have emails in sent, just in case you want to check what you wrote when.

---

### Post by Skaperen on 2016-08-25
what protocol is being used to access the mail server? POP3? IMAP4?

---

### Post by pedro_rodriguez2 on 2016-08-25
incoming:
imap.qq.com port 993

Connection security ssl/tls 

normal password

outgoing:

smtp.qq.com port 465

---

### Post by Bucky Ball on 2016-08-26
Just to confirm: I have the same issue on three machines and have had for two or three months. Have written it off as annoying and been too busy to bother with (more pressing and ongoing issues with 16.04) but will watch this thread and see if a solution can be discovered.

My guess is that this is yet another issue with 16.04 (I, at least, have had a heap of issues with it) or this release of Thunderbird - or a combination of 16.04 and this release of Thunderbird (45.2.0) - rather than related to protocol being used. But who knows and will see what clues emerge ...

* You might have a look in the Thunderbird preferences or account settings and see if you can find where the 'sent' mail is being stored, or supposed to be. Change to a path you know to exist. I figured that is probably the issue but never got round to looking ...

And apologies @Skaperen, because I think I misunderstood.

> **Skaperen said:**
> what protocol is being used to access the mail server? POP3? IMAP4?

Yes, when it comes to saving on the computer and/or just server, this does have something to do with it from memory. One saves on computer, one doesn't?

---

### Post by pedro_rodriguez2 on 2016-08-26
Thanks.

I was rather hoping that the sent email would be put in the  sent folder on the mail server, not here on this laptop. Otherwise, I  couldn't get at them from another location. 

I'll keep using the old fashioned internet email for a while! I thought Thunderbird would be an improvement!

---

### Post by Bucky Ball on 2016-08-26
Think you can set it to keep mail on server only. The mail should always be on the server though unless you specifically and manually delete it.

* Just out of curiousity, if you send an email, get the error, close Thunderbird and reboot, open TBird and check the sent folder, is the email you sent actually there? This happened to me on one of the other machines which just got things weirder. :-k

* Just another thought: Are you fully up to date? Try updating your machine if not, reboot and see if that makes a difference. I'm presuming you have your email set up with your ISP ok and you can send email ok apart from them not being stored to the sent folder? Can you also receive them? Can you send yourself an email from another account and check (or from the same account)?

And apologies @Skaperen, because I think I misunderstood.

> **Skaperen said:**
> what protocol is being used to access the mail server? POP3? IMAP4?

Yes, when it comes to saving on the computer and/or just server, this does have something to do with it from memory. One saves on computer, one doesn't?

---

### Post by pedro_rodriguez2 on 2016-08-26
Ok, I can tell Thunderbird to save sent email to its own sent folder on this local machine, or to the email server at qq.com

I sent 1 email to my email at 163.com with Tbird set to save to my laptop sent folder. Email arrived, email was saved in sent.
Then I set Tbird to save to my email server sent folder at qq.com After 5 minutes, it was still 'saving', I cancelled, it told me the mail was not sent and would I like  to save it to Drafts.

Both mails arrived at 163.com

I update almost daily, so no worries there.

Tbird does not work, at least not with qq. Maybe this is a China thing.

---

### Post by ajgreeny on 2016-08-26
I use gmail and using that you have to use the settings of gmail itself, not T'Bird, in order to save sent mail to the server.

Perhaps your email with qqmail must be configured in then same way, assuming it can be.

---

### Post by SeijiSensei on 2016-08-26
Do you have other mail folders on the server that you can write into?  Can you create new folders?  If not, and you can't solve the problem using ajgreeny's method above, your provider may not let you have anything more than an inbox on the server.  

As you've discovered, you can use your local disk to store sent mail, but that limits your ability to retrieve it anywhere.  You can tell TBird to send a copy of each outgoing email to another address via Cc or Bcc.  Use Edit > Account Settings > Copies and Folders.

---

### Post by pedro_rodriguez2 on 2016-08-26
OK, a new morning, I'm a morning person. Fixed it!

Please see the screenshot: Tbird>Preferences>Account Settings>Copies&Folders>It says 'When sending messages automatically place a copy in' Then there are 2 radio buttons, the first one is 'Sent folder on' [EMAIL="xxxx@foxmail.com"]xxxx@foxmail.com[/EMAIL], the second is 'Other: sent messages on [EMAIL="xxxx@foxmail.com"]xxxx@foxmail.com[/EMAIL]'

Tbird was set to button 1.
I clicked button 2 and now it works! Oh wonder! Emails that I send from my laptop turn up in my sent folder at qq!

Since the setting is the same, I can't figure that out, but it works, so who am I to complain?

The folder is definitely called Sent and not Sent Messages, I just checked to be sure.

---

### Post by pedro_rodriguez2 on 2016-08-26
Forgot the screenshot:

---

### Post by Bucky Ball on 2016-08-26
Good news and thanks for marking as solved.

---

