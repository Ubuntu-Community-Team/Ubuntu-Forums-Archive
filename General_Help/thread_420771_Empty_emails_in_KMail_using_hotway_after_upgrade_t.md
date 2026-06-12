---
title: "Empty emails in KMail using hotway after upgrade to Feisty"
date: 2007-04-23
forum: General Help
---

### Post by msak007 on 2007-04-23
Here's the problem. I just upgraded to Feisty today and had a few hiccups, but overall everything was working fine until I checked my email. In Edgy, I had KMail set up to send and receive emails from Hotmail using hotway / hotsmtp. It worked great until my upgrade. Now most emails received to Hotmail through KMail show "No Subject" for the subject, no sender, the body is empty, and a date of "12/31/69". I've lost numerous emails because I have it set to delete the emails off the server. I've tried purging and reinstalling inetutils-inetd, hotway, hotsmtp, purging all the config files, and reinstalling everything but no change. I tried sending emails to myself from various email accounts and from my Hotmail account to myself, and they all came back with the same symptoms. The weird thing is I receive some emails, but not others. This is also affecting Yahoo (same symptoms), which I also had set up through KMail using freepops.

Can anyone who is using the same setup in Feisty see if they're having the same problems? I know you can use the same setup with Evolution (and possibly Thunderbird), so I want to see if it's a bug in the versions of the helper apps (hotway, hotsmtp, freepops, inetutils-inetd, etc.) in Feisty, or if it's KMail specific. Google, forum, and Launchpad searches came up empty so I would appreciate any help in trying to duplicate this issue.

---

### Post by msak007 on 2007-04-25
Nobody else is using hotway to retreive Hotmail emails through KMail, Evolution, or Thunderbird? I'm still having the problem and it's driving me nuts. In case anyone can help, here's what I've figured out.

I noticed some emails were coming through and some weren't. After a couple of days what I started noticing was that the emails that DID make it through intact were ones that I had filters applied to. Those ones went straight into their respective folders based on a filter. Everything else either ended up in the main Hotmail "Inbox" folder or the "Junk" folder. Those emails exhibit the "Unknown" subject / sender and weird date. I did the following:

1. I created a new folder called "Test", and sent myself emails with nothing but "test" as the subject. I created filters for these emails and when they were filtered came right through intact to the "Test" folder. Putting them back in my Hotmail inbox and marking them as unread, then fetching the mail again without the filter yielded the same "Unknown" result when they were put in the local Hotmail Inbox folder. This confirms my suspicion that filtered emails make it through OK.

2. Suspecting it was my "Inbox" folder, I created a new one and directed all emails to it. No luck, got the same result.

3. Created a new account and fetched email pointing it to both the new and old Inbox, same result.

So it seems at this point any emails that come into my plain old inbox or Junk email folder have this problem, while filtered emails that go into other folders don't. I suspect at this point it's a problem with KMail since the emails *seem* to come through intact, but KMail butchers them somehow. If anybody is using hotway (preferably with KMail), please confirm whether or not you're having the same problem in Feisty. I want to narrow this down as a problem with KMail or hotway.

---

### Post by msak007 on 2007-04-29
Still having the problem, but it's now happening to my GMail account as well which is natively using POP, so it's not a hotway problem after all. It's something with KMail. I've tried deleting all the indexes from my kmail folder and restarting Kontact, but I'm still having the problem. Unless an email is filtered through a POP filter into another folder, the email gets lost.

---

### Post by msak007 on 2007-04-30
One last post in case anybody ever runs into this problem, I resolved it. I tried setting up one of my accounts on another machine and couldn't duplicate the issue. So I deleted all the kmail related config files in ~/.kde/share/config/ (kmailrc, kmail.eventsrc, kmailcvtrc) and restarted Kontact / KMail. That problem is gone, but of course in the course of deleting the config file I had to recreate all my accounts and POP filters that I lost (all custom filters + spam filters). Oh well, at least it works now.

---

