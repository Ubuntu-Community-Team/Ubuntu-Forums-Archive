---
title: "Is there an Ubuntu equivalent of Softpedia Advanced Identity Protector"
date: 2021-06-13
forum: General Help
---

### Post by cigtoxdoc on 2021-06-13
One of IMAP email accounts stopped working on Evolution.  I have the same email account under Outlook on a Windows 10 PC.  It had also stopped working.  When I called the email vendor, the tech found that my email account had been hacked and was being directed to an offshore PC.  He had me download and run Softpedia Advanced Identify Protector and it found "unsafe" files.  Is there a similar tool I can use for my Ubuntu PCs?

John

---

### Post by TheFu on 2021-06-13
> **cigtoxdoc said:**
> One of IMAP email accounts stopped working on Evolution.  I have the same email account under Outlook on a Windows 10 PC.  It had also stopped working.  When I called the email vendor, the tech found that my email account had been hacked and was being directed to an offshore PC.  He had me download and run Softpedia Advanced Identify Protector and it found "unsafe" files.  Is there a similar tool I can use for my Ubuntu PCs?

John

Did you try alternativeTo.net?  I've never heard of Softpedia anything, except as a download site to get Windows software that didn't come directly from the people who made it. I'd always considered it a little shifty, though I don't have any proof.  I wouldn't download software from C-Net either.  

BTW, "Softpedia" is nothing more than a download site for this software too. They didn't create it. 
[https://www.microsoft.com/en-us/p/advanced-identity-protector/9nk4lhnbblkb](https://www.microsoft.com/en-us/p/advanced-identity-protector/9nk4lhnbblkb)
Get it from Microsoft, not Softpedia.
That type of software feels like an overnight TV commercial.  Your browser and email client should handle the things they list, if you have reasonable, secure, settings.  For example, SMTP is required to be 7-bit ASCII.  Any thing included in an email that isn't 7-bit ASCII is an attachment.  That means HTML email is optional, because HTML requires 8-bits or more.  Don't allow HTML email. Don't ever display images inside email and definitely not from locations that are not either on your computer or the IMAP server with the message being read.   You'll not be tricked by phishing again and tracking will be much harder when you do this.

**Unrelated, but related ... **

Hopefully, you've already created a few new email addresses and split up which organizations each gets used at, to limit liability.
For example, social network email addresses should never be used for online purchases or banks or brokerage accounts of any sort. Same for work email addresses. Those should never be tied to anything personal.
I couldn't tell you my different bank email addresses or online accounts.  I don't know them. They are long, complex and random.  For online retail stuff, I have a different email alias for each vendor that isn't completely random, but ends in a random string. I don't know those either ... just that [email]amzXXXXXXXXXXXX@domain.com[/email] is for amazon.

As for browser security, my rules are pretty simple.
block ads - all of them, especially if they come from different domains.
block javascript - all of it, until I've vetted a website sufficiently to decide it can be and should be trusted.  Most work fine without any javascript enabled.
disable all 3rd party cookies by default.
remove all local object stores. These can be from Flash media or HTML5. I do this nightly in an automatic script.
limit the number of addons in your browser.  I have 4 - ad-blocker, noscript, a tab organizer, and a tool that saves pages to read later to my own server.  That's it. No media players. No download managers, nothing else.  If I'm going out of the country, I'll load up an SSL cert tracker, so I'll be notified about certs that are different from home when on the road. I was surprised how many countries MiTM certs and DNS in my travels.  Better to be aware than to make a mistake.
never use the browser password manager. Never add a password manager to your browser. Keep those separate - sorta "program-gapped".

If you are really privacy focused, there is much more to be done to block the trackers. You can use DNS filters or /etc/hosts entries or both. Each has good and bad things about them. This is blocking at the network layer.  People on my network can't get to facebook or twitter or about 200 google tracking websites.  Rather than be tracked, I'd rather NOT have any access to google/FB/Tweeter at all. I do not agree to their terms.

Software cannot replace a smart end-user.  That's really the lesson here.  If it could, there's be a 2 checkboxes on all our systems
a) "Security (y/N)"
b) "Privacy (y/N)"
There isn't.

---

