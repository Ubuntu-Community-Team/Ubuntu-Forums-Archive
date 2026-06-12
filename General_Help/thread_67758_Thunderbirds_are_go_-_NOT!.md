---
title: "Thunderbirds are go - NOT!"
date: 2005-09-21
forum: General Help
---

### Post by ngms27 on 2005-09-21
Hi,

I have a dual boot machine with XP using Outlook (not express) as my email client.

I'm trying to shift everying over to Ubuntu and the last major issue is getting over my emails.

I like Thunderbird but it cannot import a pst file.

So the question is how do I export emails from Outlook on XP to Thunderbird on Ubuntu. I've tried googling to no avail.

Thanks

JonnyT

---

### Post by Borusa on 2005-09-21
Hmm.

Thunderbird can't read PST files, as they're proprietary. (I'll have another go at spelling that later).

Suggestion : 

Try installing windows thunderbird on XP.  (Suggest take backup of pst file first!)
Windows thunderbird can do an online transfer from outlook (you run both apps at the same time). 
Then move the files from Windows thunderbird to linux thunderbird.

Never had to do it, know there might be issues with the transfer (hence backup suggestion), but would be entertaining to try!

---

### Post by ngms27 on 2005-09-21
I tried that earlier (great minds think alike) and it stalled on the importation.

However it does look like it probably worked.

Now I need to work out what files Thunderbird uses to store the mail etc!

JonnyT

---

### Post by jimcooncat on 2005-09-21
Not positive, but I would install an IMAP server (like Dovecot), connect to it from Outlook, and copy email over to it. Then fire up Thunderbird and connect to the IMAP server. 

After that, you could copy the email into Thunderbird's default storage, but I wouldn't bother -- leaving it on the IMAP server is better IMHO. 

I have lost all my old email twice using the Windows version of Thunderbird, and won't trust it anymore for storage. But I continue to use it with IMAP.

That only addresses the mail itself, I'm not sure about address books and account settings.

---

