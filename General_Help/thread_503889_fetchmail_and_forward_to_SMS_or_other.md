---
title: "fetchmail and forward to SMS or other"
date: 2007-07-18
forum: General Help
---

### Post by professor_chaos on 2007-07-18
Ok, if anyone can suggest a better way to do this, I would be grateful.

My goal is to retrieve mail from a few different accounts using fetchmail, and then to parse a few fields (ie the original sender, the subject, and the message) and squeeze this down to my 140character limit so I can forward this to my cell phone as a text message. 

Fetchmail works fine, but I'm using a "diff" statement on '/var/mail/user' to get only the newly fetched mail since the last check. This can work, but because I'm using grep to find fields like "From " and "Subject ", my false alarm rate turns out to be greater than zero, because forwarded mail can contain those terms. 
What would help, is some how to automagically retrieve new mail and accurately split the messages, and then accurately pull only info from the "From " "Subject " and the message body. 
After that, I am using the command "head" to get the first so many characters and "mailx" to forward this to my phone. I just am not happy about the "diff" technique and parsing the mail file the way I am.

I would be grateful for any tips here. I think I'm making it more work than it needs to be.
Thx much
prof

---

### Post by schilcha on 2007-07-18
Try having a look at nail -- a command-line mail-program. 
```

nail -H -f /var/mail/yourusername

```
will display a summary (from, date, subject) of your inbox without modifying the mail-spool. 

Use this output in your diff-technique instead of the whole spool file.

Nail can do like 1000 more things, which might let you do what you want.

Good Luck!

---

