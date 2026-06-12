---
title: "Thunderbird mail question"
date: 2023-11-01
forum: General Help
---

### Post by paulshaffer4 on 2023-11-01
On this new install, it has a newer version of Thunderbird mail.
Does anyone know where to click to tell it to delete emails off the server once they're retrieved - since I have 2 computers it's retrieving emails I already read on one of the computers.

Ubuntu 22 lts user here

---

### Post by ajgreeny on 2023-11-01
I think that is a setting in the server's own control that you will have to change using the email provider's own setup system; I don't think you can do it from thunderbird though it may depend on the email provider used.

I assume you're using IMAP not POP3 but it may help to give us all the information you can in detail.

---

### Post by paulshaffer4 on 2023-11-01
> **ajgreeny said:**
> I think that is a setting in the server's own control that you will have to change using the email provider's own setup system; I don't think you can do it from thunderbird though it may depend on the email provider used.

I assume you're using IMAP not POP3 but it may help to give us all the information you can in detail.


I'm not sure if I'm using IMAP or POP3 - how do I tell?

I know that in previous versions of Thunderbird Mail I could choose to not leave mail on the remote server......

Addendum:  On my laptop, in the server settings, I get the below option.  On my desktop, a newer version of Thunderbird seems to be installed and that option isn't there
See in screenshot below how I don't have the box checked to leave messages on server
Also, on the laptop it is POP3; howeverr, I'm not so sure on the Desktop.

---

### Post by TheFu on 2023-11-01
POP3 removes the messages from the server.
IMAP leaves them.  

Both are features. Personally, I like having the exact same view across all my email clients that IMAP provides. It even shows the status (read, junk, unread) across all the different clients, if they sync or are actively connected.  Sometimes the easiest way to send information to my wifi-only tablet/phone is via email from a desktop.  Those emails will be sync'd every few minutes, if I'm not in airplane mode, and the information is there.

But we all have different expectations.

If you are using IMAP, then just delete the message from the server. After all, you can read it directly off the server anyway and Thunderbird has an offline mode for mail, calendar, addressbooks.  My calendars and addressbooks are also maintained on the same server as IMAP email.  Again, every client has the same information, always. Very convenient.

To see which protocol is being used by Thunderbird, you need to understand that SENDING email always used SMTP.  Server-to-Server is on port 25/tcp and authenticated user-to-server is on either 465/tcp or 587/tcp.  All SMTP.

To READ email, Thunderbird uses either POP3 or IMAP. These have nothing at all to do with sending email.  In your mail folder view, right-click on the different account, and look at the "Settings".   At the top, there is "Server Settings" and the first line says which type POP3 or IMAP, messages are delivered to Thunderbird using.

At the very bottom of the Settings page, there's an "Outgoing Server (SMTP)", which is where the SENDING controls go.

---

### Post by paulshaffer4 on 2023-11-02
> **TheFu said:**
> POP3 removes the messages from the server.
IMAP leaves them.  

Both are features. Personally, I like having the exact same view across all my email clients that IMAP provides. It even shows the status (read, junk, unread) across all the different clients, if they sync or are actively connected.  Sometimes the easiest way to send information to my wifi-only tablet/phone is via email from a desktop.  Those emails will be sync'd every few minutes, if I'm not in airplane mode, and the information is there.

But we all have different expectations.

If you are using IMAP, then just delete the message from the server. After all, you can read it directly off the server anyway and Thunderbird has an offline mode for mail, calendar, addressbooks.  My calendars and addressbooks are also maintained on the same server as IMAP email.  Again, every client has the same information, always. Very convenient.

To see which protocol is being used by Thunderbird, you need to understand that SENDING email always used SMTP.  Server-to-Server is on port 25/tcp and authenticated user-to-server is on either 465/tcp or 587/tcp.  All SMTP.

To READ email, Thunderbird uses either POP3 or IMAP. These have nothing at all to do with sending email.  In your mail folder view, right-click on the different account, and look at the "Settings".   At the top, there is "Server Settings" and the first line says which type POP3 or IMAP, messages are delivered to Thunderbird using.

At the very bottom of the Settings page, there's an "Outgoing Server (SMTP)", which is where the SENDING controls go.

ok, this explains a lot.

From your tips, I have determined my laptop is using POP3 and my new desktop is using IMAP.

So my laptop is automatically NOT leaving mail on the server, but when I choose delete a mail message on my desktop- it is deleting the mail from the server (as well as my desktop).

I can live with this, now that I think I know how it works.

---

### Post by TheFu on 2023-11-02
If it were me, I'd set both the IMAP and learn to love it. It is amazing.  And your phone/tablet can also use imap.

So, when you read, delete, or move to a new IMAP folder any where, that will be reflected every where.  My mail server automatically tags messages with certain contents and files the messages by project/topic for me where it remains unread until I get there.  Firefox has a "Show Unread" option, to prevent the hundreds of folders from being too much.  Every year, I archive old projects into a folder by YYYY/ as part of my data retention rules.  After 7 yrs, I delete the old yearly archived mail with 1 "delete",   Easy.  Part of my normal organization. 

For paper (bills, taxes, etc.), I do the same with 7 boxes.  Sadly, shredding paper documents for a full year takes longer because my cheapo cross-cut shredder handles light-duty needs only.

---

### Post by coffeecat on 2023-11-05
The OP has left the building. Thanks to all who offered help. Thread closed.

---

