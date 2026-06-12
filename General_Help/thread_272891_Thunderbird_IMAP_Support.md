---
title: "Thunderbird IMAP Support"
date: 2006-10-07
forum: General Help
---

### Post by wizzkid on 2006-10-07
Hi Guys,

Im not sure if this is the right selction to post my question. but here you go. I am using Thunderbird as my email client, and I am using IMAP account on my email. however, I feel that thunderbird is a bit slower on getting mails. and Also I want my folder to automatically sync when I open my thunderbird, it seems only inbox sync with my IMAP account. Is there a way to enable folders to sync on server? im just hosting on hostony.

Also, can you guys recommend me what is a good IMAP client software? :)

Hope to received geedback! :)

Thanks

---

### Post by wizzkid on 2006-10-08
any suggestions ? :)

---

### Post by Cronjob on 2006-10-09
New messages should still go through your inbox (and then your message filters will act on them, but unless a filter is set to mark a message as "read", it will appear as unread in the mailbox it eventually arrives in).

However, if you're doing filtering on server side (scripts, SIEVE, etc) then the count will only be updated when you actually click on the folder. For example, I have a 'SPAM' folder on the server which directly receives messages based on some spamassassin and procmail recipes - that way I don't have to download them and process them through my client-side filters.

If you want other folders to be updated just like your inbox is, I believe right-clicking on a desired folder and selecting the 'check this folder for new messages' bod at the bottom of the "General Information" tab in the "Folder Properties" dialogue box that will open.

If you want entire messages (not just headers) to be synchronized, you'll need to go to the 'offline' tab in the same dialogue box and check 'select this folder for offline use'.

Whether this actually behaves properly for you, I can't predict. I only have the inbox updated. I find that Thunderbird occasionally behaves oddly in linux, however (I've seen the 'mark as junk' button not move junk to the junk folder even though the 'move when marked' option is selected and so on).

As for "speed" -- that will largely depend on the complexity of your client-side filters, the number of messages in a given folder and the complexity of your folder/subfolder layout.

Also, depending on what kind of IMAP server you are dealing with, there can be other issues at hand which will cause performance issues - such as if the server doesn't handle listing shared IMAP folders in a sensible way. I've seen IMAP servers with shared folders enabled where it would bring the server itself to its knees. That probably isn't the case in your situation, though.

---

### Post by wizzkid on 2006-10-11
Thanks! solved it :)

---

