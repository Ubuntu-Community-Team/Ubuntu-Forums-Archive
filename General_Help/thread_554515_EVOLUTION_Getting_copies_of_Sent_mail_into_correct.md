---
title: "EVOLUTION: Getting copies of Sent mail into correct accounts Sent Folders"
date: 2007-09-19
forum: General Help
---

### Post by Porpoise on 2007-09-19
I have several email accounts set up in Evolution but when I send mail, the sent copies all end up in the Master sent folder instead of the sent folder of the relevant account. It all works fine in Lookout Express on Windoze but I'm trying to migrate my W2K to Ubuntu in entirety.

The accounts are all IMAP so that they can be accessed from any machine. Obviously, this means that any Sent messages need to be in the IMAP Sent folder for the relevant account - not in the local machine's user's Sent folder.

Lookout automagically copies sent mails into the correct IMAP account's Sent folders - how come Evolution doesn't?

---

### Post by dcstar on 2007-09-19
> **Porpoise said:**
> I have several email accounts set up in Evolution but when I send mail, the sent copies all end up in the Master sent folder instead of the sent folder of the relevant account. It all works fine in Lookout Express on Windoze but I'm trying to migrate my W2K to Ubuntu in entirety.

The accounts are all IMAP so that they can be accessed from any machine. Obviously, this means that any Sent messages need to be in the IMAP Sent folder for the relevant account - not in the local machine's user's Sent folder.

Lookout automagically copies sent mails into the correct IMAP account's Sent folders - how come Evolution doesn't?

Because you haven't gone into the Preferences and changed that specific Account setting from default?

---

### Post by Porpoise on 2007-09-19
> **dcstar said:**
> Because you haven't gone into the Preferences and changed that specific Account setting from default?

Sorry, that doesn't make sense to me.

There is the default "On this Computer" set of folders (wherein lies the Outbox) where the sent mails end up in the Sent folder. Then there are the 3 accounts I have set up individually (one of which is default). There doesn't seem to be any way of not having a default address!?!

Do I have to change the default, logout, log back in and change it back again, or what.

[IMG]http://srenterprises.co.uk/Screenshot%20.png[/IMG]

Or is there something else I should have done before setting up the  3 IMAP accounts?

---

### Post by Porpoise on 2007-09-19
It's OK! Problem solved! Switched to Thunderbird. What a difference!

---

### Post by anindya_m on 2008-01-10
Hi,
    I am making this post so that people don't get the impression that the problem cannot be solved in evolution (which I use everyday and love :)). As dcstar said the settings for each account has a configurable Sent folder. Just point each account's Sent folder to the corresponding IMAP server, that's it!

However some people might argue that the default behaviour should be to move mails to the Sent folder of the server instead of the local machine. I think it's a design decision by the developers rather than a bug.

---

### Post by Michal Fapso on 2008-02-21
Hi, I had the same problem. Just go to Main menu -> Edit -> Message Filters -> Outgoing and look at the filters there. You probably just need to remove the filter which moves all outgoing messages to a particular folder. It is better to do that in the IMAP account options like anindya_m wrote.

Hope it was helpful.

---

