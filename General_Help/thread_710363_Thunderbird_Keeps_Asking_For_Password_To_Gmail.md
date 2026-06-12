---
title: "Thunderbird Keeps Asking For Password To Gmail"
date: 2008-02-28
forum: General Help
---

### Post by trmentry on 2008-02-28
I keep having an interesting issue with Thunderbird 2.x in Ubuntu Gutsy.

I have 2 accounts on Gmail (google apps).  I have TB setup to IMAP to those accounts to look for mail every 10 min or so.

About 2 or 3 times a day, TB will ask me for the password for 1 of the accounts.  Even though the passwords are stored in TB's config.  I re-enter the password and chck the box to remember it and it asks me again.  And again.. and again... and again...

Eventually it will either work or it won't.  After about 5 or 6 times trying to get it to work, I shut down TB and restart it and its fine.  Until the next time it acts up.

Anyone have any ideas why this is happening?

---

### Post by jbinto on 2008-03-03
Same here. Trying to figure it out.

EDIT: All are IMAP accounts. It only happens with GMail. My one other non-Google IMAP account never asks.

---

### Post by xaerius on 2008-03-28
I've been experiencing this as well. I can confirm that it happens in Thunderbird connecting to IMAP Gmail on Ubuntu, Windows, and OS X, so this might be some issue with Gmail's servers.

---

### Post by smccandl on 2008-04-11
Ditto - same issue here on gutsy.  Workaround is to restart TB but that's annoying.

---

### Post by atosmdq on 2008-04-16
Same here, using Gmail (IMAP) + Thunderbird in 20+ WindowsXP terminals is becaming a living nightmare.

On that configuration I first got problems with the attachments ("Part1.2") which [I think] Ive solved changing the download.by.chunks values. Now this...

And was me who proposed Thunderbird against Outlook Express when we moved to Google Apps... :(


Cant find anything yet, any clues?

---

### Post by rkillcrazy on 2008-04-16
Same here...  I use Ubuntu 7.10 @ home and WinXP Pro @ work.  Both of them nag me about my password all the time.  Quite annoying!  Any fix?

04-16-08
2131 EDT

---

### Post by atosmdq on 2008-04-20
I think I finally found a clue.

[http://mail.google.com/support/bin/answer.py?answer=78754&topic=12922](http://mail.google.com/support/bin/answer.py?answer=78754&topic=12922)

Beyond the usual recomendations there (double check he passord, append @gmail.com to username, remember is case sentisitive, etc) I found this specially interesting:

>     * Make sure your mail client isn't set to check for new mail too often. If your mail client checks for new messages more than once every 10 minutes, your client might repeatedly request your username and password. 

Now please follow the steps below to resolve the problem:

    * If you're receiving 'Username and password not accepted' errors or are constantly prompted to enter your username and password on your POP or IMAP client, try clearing the CAPTCHA.

I'll be implementing the change [remove the "check for new messages every 10 minutes"] tomorrow, and let you know the results asap.

---

### Post by rkillcrazy on 2008-04-21
I stopped using IMAP and switched over to POP.  I know this isn't a fix but it's my work-around.  It's not like I use it much anyway; it's more of an account for testing things.  I have T-Bird on my Ubuntu machine @ home and my XP Pro machine @ work set the same and the leave a copy of the message on the server for a week.  They also check for new mail every 10 minutes.  It seems to work fine and I've not been bothered by the password thing since I did it.

04-21-08
0938 EDT

---

### Post by atosmdq on 2008-04-23
Well the thing is that it stop happening the last days.

I just made the changes on half the terminals to see if it changes something, but the issue stop happening an all of them. Not really related with the changes though, as they are not physically on the same place, nor in the same domain (two different google apps accounts), so apparently some modification on google side, or just a temporal truce?

---

### Post by atosmdq on 2008-06-09
A temporal truce. Its happening again.

---

### Post by ickey on 2008-06-16
this is happening to me as well.  didn't happen to me at all until very recently, and i've been using imap on gmail via thunderbird since they introduced it.

while closing and restarting the client does fix it, this shouldn't be necessary.  this is a huge annoyance--especially when you have to enter your pass many times to dismiss the dialog

---

### Post by nisarg on 2008-06-17
I am experiencing this issue too.
I dont use TB too heavily, but its annoying that it keeps prompting me for password randomly, especially when I send or receive emails.

---

### Post by HandyAndy on 2008-06-17
[http://mail.google.com/support/bin/answer.py?hl=en&answer=78754](http://mail.google.com/support/bin/answer.py?hl=en&answer=78754)

This works, but the problem comes back intermittently. Gmail is a work in progress and I expect it will get fixed eventually.
It is annoying though, especially because Gmail+IMAP+Thunderbird has been a nice, problem-free solution until this started happening.

---

### Post by soulinafishbowl on 2008-06-21
From the Google page mentioned above:
> Make sure your mail client isn't set to check for new mail too often. If your mail client checks for new messages more than once every 10 minutes, your client might repeatedly request your username and password.

Has anyone tried increasing the Check for new messages every XX minutes from 10 to perhaps create an error margin beyond the 10 minute window Gmail asks for?  I'll give it a try and post any results.

---

### Post by jbinto on 2008-06-22
After a few weeks of working fine, it's back to asking me over and over again.

I wonder if Gmail's IMAP server has a throttle that is not per account? For instance, I'm checking three Gmail accounts every 10 minutes. Perhaps I should increase the timeout to 30 minutes (i.e. average one IMAP connection per ten mins)?

Has anyone gone as far as to analyze what it's doing? I don't know anything about the IMAP protocol, but perhaps it's giving the equivalent of an FTP 421 "Service not available/Too busy/Stop hammering me" and not a FTP 530 "Login incorrect", and Thunderbird says "doy, I can't connect, it must be the wrong password".

*shrug*

---

### Post by soulinafishbowl on 2008-06-23
Well, its been only a little more than a day, but since my last post, no password prompts have appeared.  I adjusted my setting for check every 10 minutes to 12 minutes on each of my five Gmail addresses on one Thunderbird profile.  

When it did occur, I am almost sure that it was prompting me for a password on only two particular addresses of the five, if that is a relevant clue.

I've also tried forcing a check for all inboxes repeatedly, and even opening and closing Thunderbird repeatedly, and can't reproduce the password glitch, so I'm thinking that it is not related to the check frequency after all.

---

### Post by ccrs8 on 2008-06-23
There's not much more I can add to the thread that already hasn't been discussed.  I use Thunderbird 2.0 for my gmail account via IMAP on both Ubuntu 8.04 and Windows XP Pro (at separate times).  I only have one gmail account, so I can't test it with multiple gmail account setups, but I do have one non-gmail IMAP account that never requires re-authorization.

Until reading this thread just now, I had both machines checking every 5 minutes.  I changed it to 10 minutes, but per the reply above, that may not really be the problem.  Also, until about 10 minutes ago when I was asked repeatedly for my credentials, Thunderbird had gone two days without asking, even though I was set to check every 5 minutes and I was also using Thunderbird a lot and refreshing my inbox much more frequently than every five minutes.  Very strange.  It just seems so random, and if it wasn't for this issue I'd say that my "Thunderbird/IMAP/Gmail/Lightning/Google Calendar/Provider for Google Calendar" setup is the dream setup for complete anywhere access.

---

### Post by soulinafishbowl on 2008-06-23
Happened again just a bit ago.

Not quite a gem, but I found this from Google Groups:
[http://tinyurl.com/6px4re](http://tinyurl.com/6px4re)

> Hey folks,

We're aware that some of you may need to unlock the CAPTCHA
repeatedly, and we're working to resolve this issue. In the meantime,
make sure that no other computers or devices are downloading your
mail. Also, if you're using POP, make sure that your email client only
checks for new messages every ten minutes. While we recognize that
many of you access your mail from different devices (and think that
this is perfectly reasonable), frequently accessing your mail from
multiple devices can look "suspicious" to us when combined with other
factors, so limiting your connections is a good place to start
troubleshooting.

Just a Daisy, I see that you're only using one computer, and it sounds
like you're not checking your mail too frequently, so I would suggest
changing your password.

Best,

Sarah
Gmail Guide Yellow

On Mar 26, 7:15 pm, Just a Daisy wrote:

- Hide quoted text -
- Show quoted text -
> Ok, I have had to do this every second or third time I get my mail!
> What's going on?!  I just started having this problem three days ago
> and it works for about two or three times but then I get locked out
> again!  I only check this address on this computer and then only about
> four times a day, but this is getting frustrating!! 

So the guide suggests it is a problem with checking frequency from multiple devices, but then provides a specific example of how this is incorrect!

After scanning through a few of the Google Groups pages and looking at one page in particular, ( [http://tinyurl.com/5uc72k](http://tinyurl.com/5uc72k) ) I'm surprised at Google.  The CAPTCHA method seems to work for only a small percentage of people, and still we don't even know what the CAPTCHA thing is.  It isn't Bob's Software Company run from Bob's basement, it's Google!  

I hope a fix arrives soon, but I won't hold my breath.

---

### Post by ccrs8 on 2008-06-25
After changing the check time to 10 minutes, the same thing is still happening.  I cleared my CAPTCHA (whatever that means) but that didn't fix anything.  I'm beginning to think that simply sticking with the web gmail is better.  Besides this issue, I'm also finding that spam that I delete in Thunderbird is still in the spam box (just marked as read) when I log in to the web.  Also, drafts of email I send sometimes go in to the Trash once I send them and sometimes stay in drafts, making me have to go back and verify that I actually sent the message.  If it wasn't for the fact that PulseAudio messes up my audio by not allowing non-web sound to play once I've played a web sound (either flash advertisement with sound or Youtube or whatever) until I close the browser, I think I'd just leave the web version of gmail up all the time like I used to do with Thunderbird until this issue started.

Anyway, I guess I don't have anything constructive to add - it's just frustrating so I'm venting.

---

### Post by soulinafishbowl on 2008-07-17
It's getting worse.  It's more frequent and happening to all of my Gmail accounts, and still not a clue.  :mad:

---

### Post by ddixonr on 2008-07-17
Anybody try setting a master password from the preferences menu? I just enabled one and I am waiting for it to happen again.

---

### Post by soulinafishbowl on 2008-07-23
I thought I would give ddixonr's idea a try, and after about 4 days, I have not had to retype my password.  However, I'm almost sure this not a solid workaround.  This morning, I get the following message from Thunderbird in an alert dialog for one of my gmail addresses.  

> Mail server imap.gmail.com is not an IMAP4 mail server.

I am assuming this alert is from the same problem that's causing Thunderbird to repeatedly prompt for passwords.  I still think the problem is with Google, but at least I don't have to retype my password every time.  Thanks!

---

