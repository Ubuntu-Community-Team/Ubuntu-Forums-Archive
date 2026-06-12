---
title: "Migrate from Outlook to Thunderbird"
date: 2015-07-22
forum: General Help
---

### Post by ryu kun on 2015-07-22
I know that this is a question asked and answered for many times, I have read many of them, but I have to ask it again, because, Thunderbird does not support importing Outlook e-mails as its current version 38.1.0. Please see "Known Issues" section [here]("https://www.mozilla.org/en-US/thunderbird/38.1.0/releasenotes/"). 

Another reason for me to ask this question again is: I have set up a Gmail account to transfer all my e-mails from Outlook to Gmail IMAP server, and then from there to Thunderbird, however Gmail could not take all my e-mails, because some e-mails were too large and for some other reasons which I have not beed notified about.

So my question: How can I import my Outlook e-mail archive (in .pst files) to Thunderbird (to use on Ubuntu 14.04)?

---

### Post by sudodus on 2015-07-22
With an IMAP server you need not import the emails. Keep them at the server (Google allocates plenty of space for each gmail account, several GB), and connect to the server via IMAP. After a while you get more used to Thunderbird, and can select to make local copies of you mails (if you wish).

If gmail cannot import your emails, because there are too big and/or too many attached files, you can either delete mails with big attachements, or save those big files locally and after that delete those mails. It is possible to sort the mails according to size and that way find the huge ones.

I have no problems to store several years of mails at gmail (but I do some 'housecleaning' once per year).

---

### Post by amanchesterman on 2015-07-22
This tutorial 
[http://kb.mozillazine.org/Import_.pst_files](http://kb.mozillazine.org/Import_.pst_files)
lists a number of Linux utilities that are designed to convert .pst files to .mbox format for importing into Thunderbird. At least one of them is available in the Software Center. I'm wondering if you have tried them? Apparently different versions of Outlook configure the .pst files differently, so the utilities may not all work, but I would have thought it would be worth experimenting.

---

### Post by ryu kun on 2015-07-23
readpst is in Ubuntu repositories. It is a command line utility. I have tried it. Unfortunately it cannot convert all e-mails. It reports that it skips some of them. I cannot tolerate even one e-mail loss, as this is a business e-mail account, therefore it was not a solution for me.

Copying to Gmail IMAP from Outlook took a lot of my time and it always failed at some point with a vague error message. I could not get information about which e-mails were skipped or how many e-mails were copied. This is a tedious process when you have thousands of e-mails. I have just gave up for now.

I tried demo version of PST Converter a commercial software. It successfully converted 25 e-mails (demo limit) in PST mailbox to eml format. Unfortunately this software is pricey, 49 USD.

I will try to find another way... For now I guess I will just use Outlook when I need to search my e-mails in pst archives. :(

---

### Post by ElRick on 2015-07-24
Hi

Try Outlook Open Converter. Some time ago it worked for me, and I could convert my 2007 PST into MBOX. You can find It here

[http://sourceforge.net/projects/ooconverter/](http://sourceforge.net/projects/ooconverter/)

---

### Post by ryu kun on 2015-07-26
Thank you ElRick, great tool. I have not seen it anywhere despite all my long searches. 

It converted many of my e-mails in 2010 PST file however it reported that it skipped a few. Unfortunately there was not any detail about skipped ones. Nonetheless I have the majority of my e-mails in open format now.

---

### Post by ElRick on 2015-07-26
> **ryu kun said:**
> Thank you ElRick, great tool. I have not seen it anywhere despite all my long searches. 

It converted many of my e-mails in 2010 PST file however it reported that it skipped a few. Unfortunately there was not any detail about skipped ones. Nonetheless I have the majority of my e-mails in open format now.

Your Welcome

I'm glad to help you, and yes, it needs some improvements. It might be a good idea to suggest those "missing" options at the project's page

---

