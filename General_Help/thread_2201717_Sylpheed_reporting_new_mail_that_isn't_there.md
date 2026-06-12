---
title: "Sylpheed reporting new mail that isn't there"
date: 2014-01-25
forum: General Help
---

### Post by Moses_Moore on 2014-01-25
I am using Sylpheed v 3.4.0beta5, as per latest Ubuntu 13.10 repositories.  It is configured to access Google's Gmail service via IMAPS.

 Sylpheed will often report there are one or more new messages in my INBOX.  However, when I select the Gmail inbox to view the messages, there are no new messages, and the status of the INBOX folder goes from a bold "INBOX (2)" to normal weight "INBOX".  If I click on 'Get' or 'Get All' to check again, Sylpheed will notify me again there are new messages waiting.

I don't get this problem with Thunderbird, Claws(mail) nor Mutt, so I presume this is a problem with Sylpheed.  Is there some feature I've turned on only in Sylpheed that I should turn off?  Could someone tell me if Sylpheed has a debug mode so I can watch the IMAPS session to see if there's bad data coming from Gmail's servers, or if Sylpheed is making a bad request?

---

### Post by Moses_Moore on 2014-01-25
Found the log window.  Ctrl+Shift+L in Sylpheed, or "Tools > Log Window".

[FONT=courier new][17:56:30] IMAP4> 40 STATUS INBOX (MESSAGES RECENT UIDNEXT UIDVALIDITY UNSEEN)
[17:56:30] IMAP4< * STATUS "INBOX" (MESSAGES 897 RECENT 0 UIDNEXT 3907 UIDVALIDITY 2 UNSEEN 3)
[17:56:30] IMAP4< 40 OK Success
[/FONT]
There's the 'UIVALIDITY 2 UNSEEN 3' that Slypheed receives from Gmail's IMAP server.  Sylpheed notified me that 3 messages are waiting, and it shows '**INBOX (3)**' on my gmail account.  However, when I click on the INBOX, it changes instantly to '**INBOX (1)**'.

[FONT=courier new][18:00:30] IMAP4> 113 SELECT INBOX
[18:00:30] IMAP4< * FLAGS (\Answered \Flagged \Draft \Deleted \Seen $Phishing $Forwarded NonJunk $NotPhishing Junk)
[18:00:30] IMAP4< * OK [PERMANENTFLAGS (\Answered \Flagged \Draft \Deleted \Seen $Phishing $Forwarded NonJunk $NotPhishing Junk \*)] Flags permitted.
[18:00:30] IMAP4< * OK [UIDVALIDITY 2] UIDs valid.
[18:00:30] IMAP4< * 865 EXISTS
[18:00:30] IMAP4< * 0 RECENT
[18:00:30] IMAP4< * OK [UIDNEXT 3907] Predicted next UID.
[18:00:30] IMAP4< * OK [HIGHESTMODSEQ 1235779]
[18:00:30] IMAP4< 113 OK [READ-WRITE] INBOX selected. (Success)
[18:00:30] IMAP4> 114 UID FETCH 1:* (UID FLAGS)
[18:00:30] IMAP4< (retrieving FLAGS...)
[18:00:30] IMAP4< 114 OK Success
[/FONT]
I guess the bit I should be interested in is obfuscated by Sylpheed in that "[FONT=courier new](retrieving FLAGS...)[/FONT]" line.

---

