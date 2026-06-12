---
title: "to IMAP or POP..."
date: 2015-05-07
forum: General Help
---

### Post by maclenin on 2015-05-07
...that's, essentially, the question.

I have a fairly strong opinion the other way - as I have been using (only) the other way (quite blissfully) for many, many (many) years now and it ain't broke....

However, I ask the question, because there's a mighty and growing swell imploring the use of one and pooh-poohing, the other....

Thanks for any thoughts.

---

### Post by timgood on 2015-05-07
IMAP is useful if you are accessing mail on multiple devices, as your folders will always be the same. So send or delete a mail from your desktop, and the result will show in phone, tablet, laptop etc. I use IMAP simply because of this functionality. On the downside, your service provider will probably not provide as much space as you will have on your home computer, but properly managed email should not be a problem.

---

### Post by buzzingrobot on 2015-05-07
With IMAP, mail is retained on the server until the user specifically deletes it.  Folders for your account on the server and on your local devices mirror each other (if configured correctly by a user, and I suspect they often are not).  Changes to mail can be synchronized in both places. 

All that is handy for folks who need or want to get at their email from different devices and make sure it's in the same "state" on all of them. (Or obsess about checking mail on the phone every 30 seconds.)

POP is much simpler. Before you can read your mail, you download it from the server.  The POP protocol allows mail to be deleted on a server as soon as its downloaded.  Some providers, like Gmail, allow users to delay that deletion.

IMAP is the common default these days. 

Most of the time I could live with POP but IMAP comes in handy when I travel.

---

### Post by SeijiSensei on 2015-05-07
As someone who has provided mail services, the worst arrangement is POP3 with "don't delete messages on server" enabled. Many mail clients will no longer identify the stale messages as residing on the server, so the user never bothers to delete them.  

POP only makes sense if you read your mail from one device.  For any other situation, IMAP is by far the better choice.

---

### Post by buzzingrobot on 2015-05-07
> **SeijiSensei said:**
> As someone who has provided mail services, the worst arrangement is POP3 with "don't delete messages on server" enabled. Many mail clients will no longer identify the stale messages as residing on the server, so the user never bothers to delete them.  

POP only makes sense if you read your mail from one device.  For any other situation, IMAP is by far the better choice.

Gmail and others discourage deletion. People have been trained to expect mail to be there forever.

I think many IMAP clients assume too much expertise on the part of the user. Most users won't know how IMAP works, folder structure, syncing, etc., yet setting up clients beyond the defaults typically requires that knowledge.

---

### Post by Habitual on 2015-05-07
IMAP has a smaller footprint on the local drive.
IMAP for uniformity across all client software.

---

### Post by maclenin on 2015-05-08
All!

Thanks for the thoughtful replies!

I am an ardent POP user - and love its ease of deployment / configuration. I have an email provider who offers a very simple web mail interface - and I, yes - pay - about eight quarters a month to retain an address I've used since the latter part of the last century. I enjoy 200 ***MB*** of email "server" space - and have the settings on my desktop email "client" set to "keep mail on the server" for 5 days after they are downloaded to the client (only the desktop client download kicks-off the 5-day clock). I have it set this way, so that I can both manage email server bloat and leave reasonable time to download INCOMING email to all of my devices. I archive / backup emails I wish to keep, as I would archive / backup any other data (and with 100 godzillabytes of storage media costing next to nothing, I am not worried about running into over-capacity issues - locally).

The desktop is the central repository - fed by the email server - and I can maintain as many different views / folders of email as I wish from device to device. If I "accidentally" delete an email from one of my devices - I will not worry that the accidentally deleted email will be removed from ALL DEVICES EVERYWHERE - as the devices "sync" - which I understand can be a risk with IMAP. What happens if my child gets hold of one of my devices and - oops - wipes clean / deletes email and an account - accidentally - making sure she syncs, of course (because she's thorough), before removing the account from my device. Though I do not have extensive experience with IMAP (so, please correct me should I misrepresent), it does seem TOO mapped TOO integrated TOO entangled - not allowing the flexibility / modularity for me to organize, integrate, map and manage things in a way I prefer to organize them - hmm - one of the many reasons I chose to take the leap to linux!

As for OUTGOING mail - from an automation standpoint - I can, perhaps, see the appeal of IMAP - however - even here - it's not critical (for me) that I have every single mail I send from every device on all of them. Should I need something I've sent - on a different device - I can easily forward it to myself - and then I'll have it everywhere.... Assuming I've sent something from a portable device - while on the fly, I will have that portable device with me when I am next at the desktop - so, I can open the device, which is sitting in my pocket or on my desk - to access its sent email. Should I send something from web mail - web mail is accessible wherever I can reach the web - which is most everywhere nowadays.... If I've sent it from my desktop - well, then, perhaps, I am SOL - unless someone has replied to the sent email - in which case I'd have it in my INCOMING mail - on all devices....

If it ain't broke?

---

### Post by buzzingrobot on 2015-05-08
If you read mail over breakfast at home and then want to respond at the office, by the book POP can't do that.  The mail won't be on the POP server when you get to the office. If the mail files are retained on the server for X amount of time, so you can see them again at the office, then that's dependent on the particular ad hoc setup of that provider.

It's that kind of versatility that makes IMAP dominate. Works in reverse, too:  Start a message here, finish it there, send it from over there.

When I travel, I forward to myself anything I want to have access to on the trip. I've created a specific folder for the stuff server and set up filters to route messages there.  I could do *that* in POP, but that those message would only be available on whatever device I happened to use to read them initially.

---

### Post by sgage on 2015-05-08
The main problem with IMAP as I see it is that different ISP's/services implement it differently. E.g., Google is set up so that you can use POP, but if your use their SMTP to send from any machine, it will be in your sent folder, available through the web interface or IMAP. And if you read your mail on the web interface or IMAP, it will still be picked up by POP the next time you check. 

My ISP used the Google 'partner program' to outsource email, and it was good - I could mix and match POP and IMAP as I saw fit. Of course, being Google, they discontinued the 'partner program' last summer. My ISP's current solution handles IMAP very differently. If you pick up mail with POP, it vanishes from the IMAP server. If you send mail from outside of IMAP, it does not show up in 'sent' of IMAP. It took me a while to figure out what was going on.

I have a gmail account, and I may have to just switch over to that. I really don't want to change my email address of 20+ years, though...

---

### Post by maclenin on 2015-05-08
> **buzzingrobot said:**
> If you read mail over breakfast at home and then want to respond at the office, by the book POP can't do that.  The mail won't be on the POP server when you get to the office. If the mail files are retained on the server for X amount of time, so you can see them again at the office, then that's dependent on the particular ad hoc setup of that provider.

I have my email client (Thunderbird) set up to "Leave messages on the server" for 5 days - so, after my morning coffee at the desktop, my other devices will find the same email on the POP server, when I am out and about. Thus, INCOMING on the desktop (with coffee) and devices (while out and about) will be identical.... Moreover, what I do to change what's on either (desktop or device) will not change what's on the other should I decide to delete mails from one and not the other, for example.... I use the desktop as a repository - so - if I decide to delete an email from my device - I don't want it vanishing from my desktop....

> **buzzingrobot said:**
> It's that kind of versatility that makes IMAP dominate. Works in reverse, too:  Start a message here, finish it there, send it from over there.

I hack this with POP - I draft an email with my coffee - and fwd the draft to myself - then cut and paste to complete it while out and about on the device.... A few more (3 second) key strokes to "finish it there," and "send it from over there" - with full control over what gets deleted and how I organize things - everywhere....


> **buzzingrobot said:**
> When I travel, I forward to myself anything I want to have access to on the trip. I've created a specific folder for the stuff server and set up filters to route messages there.  I could do *that* in POP, but that those message would only be available on whatever device I happened to use to read them initially.

So - the forwarding force is strong with you, as well....

---

### Post by raptir on 2015-05-08
It sounds like you're pretty well set on using POP3. I personally think IMAP is much better for the multi-device world we have today, but if POP3 is working for you then there's no reason to switch.

---

### Post by buzzingrobot on 2015-05-08
Both are actually antiquated, I think.  Few users are aware the protocols exist, and they shouldn't be expected to be aware. Frankly, mail should never be deleted without the owner's consent, and HTTP-based clients are more than capable.

---

