---
title: "[SOLVED] Evolution not able to read IMAP folders"
date: 2008-07-08
forum: General Help
---

### Post by The Foz on 2008-07-08
I have been trying to set up Evolution to work with IMAP.

I am doing this because I need to be able to access my stored emails from all my PCs at home, from the office, and when I am on the road.

The IMAP server is my own server (running courier-imap). I know that the IMAP server is working fine, as it works perfectly with Mozilla Thunderbird. It also works fine with Evolution when I first configure Evolution as an IMAP client for an account.

The problem is that, as soon as I create any new IMAP folders with another client (Thunderbird or another instance of Evolution on another machine), Evolution can no longer read any of the IMAP folders. The only exception to this is if Evolution is connected (online) to the IMAP server when the folders are added. Evolution cannot even query a list of available folders to which to subscribe.

I have tried all sorts of configuration changes to get around this problem (synchronisation settings, security settings, etc.). I have even removed all the IMAP folders and started again, but once a particular IMAP account is messed up for that instance of Evolution, no amount of cleaning and reconfiguration will fix it (I currently have 3 such accounts that I can no longer access with Evolution). If I configure a clean instance of Evolution to connect to the IMAP account, everything is fine until I create folders with any other client, at which point it becomes unusable. 

It seems that Evolution is locally caching the folder list, and is unable to reconcile its cached list with that from the server.

I have found no help in the Evolution Help & FAQs, nor anywhere else on the Evolution web-page.

Does anyone have any ideas?

---

### Post by The Foz on 2008-07-15
Problem solved!

In case any of you have the same problem (which you probably will if you use Evolution with an IMAP server, and use more than one client to access the IMAP server), here is the answer.

If/when you get errors in Evolution from trying to access the IMAP folders (which seems to occur when another email client has added/deleted/renamed an IMAP folder):
[LIST=1]
[*]Close the Evolution email client
[*]Open the folder .evolution/mail/imap, and delete the folder corresponding to the problem IMAP account
[*]Reopen Evolution
[/LIST]

Please not that this approach does not seem to work the Windows version of Evolution (one of the most buggy pieces of software it has ever been my misfortune to install), but for the Linux version it does.

---

