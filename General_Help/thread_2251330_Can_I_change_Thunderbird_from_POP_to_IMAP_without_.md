---
title: "Can I change Thunderbird from POP to IMAP without altering accounts?"
date: 2014-11-03
forum: General Help
---

### Post by Mike_Walsh on 2014-11-03
Evening, everybody.

Just a general query about Thunderbird, really. 

When I originally configured T-Bird in each of my distros, I set it up for POP (keep mail on the computer). I would now like to change it to IMAP (remote folders); can this be done without affecting my accounts, or will I have to delete the accounts, and set them up again?

Regards,

Mike.

---

### Post by TheFu on 2014-11-03
I think so ... but the server on the other side of the country has to support IMAP.  Some ISPs do, but many choose NOT to do so because they don't want email left on their email server storage.

Oh - and clearly you will need to change the settings for each account - so that IS a modification.

---

### Post by Mike_Walsh on 2014-11-03
@ TheFu:-

Thanks for that. I just installed the newest version of Puppy Linux to a flash drive the other day. 'Tahrpup' is based on Trusty; and it now uses the same repos as Trusty, albeit modified to its own peculiar .pet or .sfs files. So I've installed T-Bird, which I use in all my distros.....except that THIS time, since it's running from a 4 GB SanDisk Cruzer Blade, there's not a lot of space for storing loads and loads of POP e-mails; so I set it up for IMAP. My two e-mail accounts DO both support IMAP, so clearly, that isn't going to be an issue. 

And that got me wondering as to how easy it would be to change the other T-Bird installs over. It's simple enough, I suppose, to just delete each account in turn, and then re-create it with IMAP instead of POP; but I wondered if there was a specific setting I could change, instead.

Regards,

Mike.

---

### Post by TheFu on 2014-11-03
It is in the server settings for each account. No need to delete/recreate accounts.  <--- this is wrong.

Edit --> Account Settings --> Server Settings

Well - crap - just looked on mine. Perhaps it cannot be done that way?  The POP/IMAP seems to be unchangeable.
Sorry - I've been running email servers since the mid-1990s and have only used IMAP since around 1997.

Google found this as a method:  [https://support.mozilla.org/en-US/kb/switch-pop-imap-account](https://support.mozilla.org/en-US/kb/switch-pop-imap-account) as the way.  It does require manual transfer of all messages.  Looks like it will work.

---

### Post by ajgreeny on 2014-11-03
There is no real problem doing what you want if the servers of your email supplier support IMAP.  You have to set up another account, but it will have the same email address and password etc etc, and your emails and configuration for those imap emails will be in another sub-folder of the hidden .thunderbird folder in your home.

TB keeps all your pop mail in the hidden folder ~/.thunderbird/*alphanum*.default/Mail/pop.*mail.com/* where the **alphanum** is a random string and **pop.*mail.com/*** is named according to your mail server, eg in my case pop.gmail.com.

If you later set up an IMAP account for the same email address, all those pop emails will remain where they were and you will get another folder called ~/.thunderbird/*alphanum*.default/ImapMail/ with all the imap mail folders (or tags/labels, whatever they're called) in there.

---

### Post by Mike_Walsh on 2014-11-03
Thanks for the replies, guys.

I've discovered that it's quickest simply to delete the POP account, and create a new IMAP account in its place; takes around 90 seconds or so...

AJ, is it possible to delete the POP mail folders in the .thunderbird config files? I assume so; I'll mark this as 'Solved', but would just like clarification on that one point.

Cheers!

Regards,

Mike.

---

### Post by ajgreeny on 2014-11-04
Yes, if you wish to you can delete the files in ~/.thunderbird/*alphanum*.default/Mail/pop.*mail.com/* or delete the whole folder.  It is your choice.

However, if you delete them from there, you will not have any emails from your pop days, unless of course, you have not deleted them all from the server, in which case you will be able to find them in the imap all-mail folder.  Whether or not you will be able to see them when off-line will depend on your setup of imap.

---

