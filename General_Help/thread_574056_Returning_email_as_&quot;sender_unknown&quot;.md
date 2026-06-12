---
title: "Returning email as &quot;sender unknown&quot;"
date: 2007-10-12
forum: General Help
---

### Post by BobLand on 2007-10-12
After 5 years of being invisible, I'm being flooded with spam.  I have filters to delete them but once on a list, forever on all lists.

How can I automatically resend an unwanted email back to the sender to appear as if there is no such address?

Thanks,
bobland

---

### Post by kyphi on 2007-10-12
There is a programme called Mailwasher that will do that for you.

Although a Linux version was being developed, this was ceased just recently and is no longer available.

Presently, the only option is to buy the Windows version and run it via Crossover.  There has been some success to run it via Wine.

I run this unique and essential (to me) programme via Crossover 6.2.

Mailwasher is made by Firetrust and Crossover is made by Codeweavers.

---

### Post by BobLand on 2007-10-12
kyphi,
I downloaded and installed via wine.  It came up and seems to be working.  I wont know until I get mail.  I disable my junk filters and let the garbage in and see what happens.

This seems to be what I was looking for.

Thanks,
bobland

---

### Post by milosz.galazka on 2007-10-12
> **BobLand said:**
> After 5 years of being invisible, I'm being flooded with spam.  I have filters to delete them but once on a list, forever on all lists.

How can I automatically resend an unwanted email back to the sender to appear as if there is no such address?

Thanks,
bobland

As I understand you want to resend spam to "spammer" (bogus return address)?
Don't do that, you will only confirm your email address or send it to innocent people.

---

### Post by kyphi on 2007-10-12
True, milosz, unless you bounce it from the server without downloading it to your machine.

---

### Post by cssutto on 2007-10-12
My understanding is that spammers pay no attention at all to mail that is returned.

Therefore, you waste your time with mailwasher and similar stuff.

I use bogofilter.  I have it set up to dump the spam in a spam mailbox and every 10 minutes cron zaps the file.

As I use mutt, I never see what is in the spam mail box.

Run bogo.  Do not set up cron to zap the mailbox until you have watched it for a couple of weeks to be sure you have it set up correctly.

Bogo tells you how to map your keys so that Shift-x puts anything that gets past it into the spam mailbox the next time it is received.  Saving mail will tell bogo it is 100% clean.

I once was getting hundreds of spams a day.  Now I might see three a week at the most.

Every now and then someone will come up with a totally new and unheard of name and address and that one will get through.  Give it the Shift-x treatment and you will never see it again.

I am using mutt, fetchmail and procmail.

Procmailrc is a little tricky to set up, but it works like a charm.

The point is, just dump the spam and care not that they keep sending it because you never see it anyway.

Bouncing it is a total waste of time.

---

### Post by cssutto on 2007-10-13
One more thing.

Forwarding spam, if picked up by one of the picky IPS's can get you or your ISP banned by the "wounded" ISP.

Some ISP's have installed anti-spam systems.  I do not like that because they are not nearly as  able to decide what spam is than you are, so the result is that they will ban mail they should not.

For instance, suppose you have something like SpamCop (I suppose they still exist) and you report someone by mistake, that person's email is then banned by the ISP that receives your complaint.

Then it becomes a hassel to get it corrected and you have damaged that person, not legal damage, but damaged just the same.

So bouncing, forwarding or reporting has its dangers.  If you just zap it, no harm done and it is a lot more effective and controllable..

---

### Post by posterboy on 2007-10-13
There's still another consideration, when bouncing this stuff, read on the web about "backscatter", a really popular spammer trick.

---

### Post by cssutto on 2007-10-13
The guts of it.

[http://www.dontbouncespam.org/](http://www.dontbouncespam.org/)

---

### Post by BobLand on 2007-10-13
This is not quite spam.  When I buy something from a site I always check the "don't bother me button," but it does no good, neither does the unsubscribe process.  Hence, I'd like to inform the vendor that I no longer exist.

All of my "spam" comes from in-place internet vendors.

---

### Post by cssutto on 2007-10-13
If you always initiate the purchase, then spam is spam is spam and you will not miss anything by treating their mail as spam.

Because you always initiate the purchase.

---

### Post by posterboy on 2007-10-13
Way too many of these places have a line somewhere that reads like this: "Your email address may be shared with certain affiliated business partners", blah,blah. What this means is that the email list is for sale to anyone with a checkbook. They become "an affiliated business partner", and away we go.

---

