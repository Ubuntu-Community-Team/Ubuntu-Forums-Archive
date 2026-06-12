---
title: "[SOLVED] Evolution + Gmail SMTP = can't send email"
date: 2008-05-13
forum: General Help
---

### Post by jcwmoore on 2008-05-13
I have tried this post [http://ubuntuforums.org/showthread.php?t=342779&highlight=Evolution+Gmail+smtp]("http://ubuntuforums.org/showthread.php?t=342779&highlight=Evolution+Gmail+smtp") but it didn't work for me.  So I can receive my mail from Gmail but and can't send any out going messages.  I have posted the sending messages tab from evolution, any suggestions?

---

### Post by Patrick793 on 2008-05-13
What about Thunderbird? They already have pre-configured settings for Gmail. Just enter your gmail address and it works like a charm.

---

### Post by jcwmoore on 2008-05-13
I have used thunderbird, but I like evolution better, I really like the integration with gnome.

---

### Post by jcwmoore on 2008-05-14
[http://groups.google.com/group/Gmail-Help-POP-and-IMAP-en/browse_thread/thread/3ab9c0b38a81af18/151bb6ea966650e5?lnk=gst&q=evolution#151bb6ea966650e5]("http://groups.google.com/group/Gmail-Help-POP-and-IMAP-en/browse_thread/thread/3ab9c0b38a81af18/151bb6ea966650e5?lnk=gst&q=evolution#151bb6ea966650e5")

I found someone with a similar issue on the google support group, but I still can't send emails after following that advice.  Any one out there had success with evolution and gmail SMTP?

---

### Post by Monicker on 2008-05-14
> **jcwmoore said:**
> [http://groups.google.com/group/Gmail-Help-POP-and-IMAP-en/browse_thread/thread/3ab9c0b38a81af18/151bb6ea966650e5?lnk=gst&q=evolution#151bb6ea966650e5]("http://groups.google.com/group/Gmail-Help-POP-and-IMAP-en/browse_thread/thread/3ab9c0b38a81af18/151bb6ea966650e5?lnk=gst&q=evolution#151bb6ea966650e5")

I found someone with a similar issue on the google support group, but I still can't send emails after following that advice.  Any one out there had success with evolution and gmail SMTP?

Works fine for me.  I just did a couple of test sends to verify.

---

### Post by dje on 2008-05-14
My setup just has:
```
smtp.gmail.com
```
and not:
```
smtp.gmail.com:465
```
I think that will solve your problem (if you remove the :465)

hope that helps you,
dje

---

### Post by jcwmoore on 2008-05-14
smtp.gmail.com
SSL encryption
Plain authentication

Remember, if you have the incorrect settings and then correct them, they DO NOT apply to messages sitting in the outbox, that's what got me

---

### Post by mindepinde on 2008-06-02
> **jcwmoore said:**
> 
smtp.gmail.com
SSL encryption
Plain authentication


The above didn't work for me. I had similar problem - can send plain emails via smtp.gmail.com (with above configuration), yet can't send emails with attachments.

What worked for me:
- TLS encryption (instead of SSL)

I don't know why google gives misleading instructions, but this one works. Yet, in all other cases when I used Evolution (earlier installs) I used SSL and everything was fine. Mystery.

---

### Post by woodnymph on 2009-11-29
What worked for me:
- TLS encryption (instead of SSL)


this worked for me too.  thanks

---

### Post by thync on 2010-02-03
> **woodnymph said:**
> What worked for me:
- TLS encryption (instead of SSL)


this worked for me too.  thanks

Hmm, opposite holds true for me. Must be because I'm in the Southern Hemisphere.

---

### Post by AndyWhite87 on 2010-02-20
I've found a way to send e-mails using Google's correct settings:

smtp.gmail.com
SSL
Plain

I was wondering for about half an hour why I couldn't send messages, follow these steps they work:

1. Close anything that has your gmail account (Web browser, home mail client, Mobile).
2. Visit [https://www.google.com/accounts/DisplayUnlockCaptcha](https://www.google.com/accounts/DisplayUnlockCaptcha).
3. Enter your e-mail address, password and the distorted words.
4. Open Evolution and try to send an e-mail

Hope it solves your issues too.

---

### Post by Diabolis on 2010-04-19
Yeah, I was trying to send a email through Evolution, but I also had open gmail in Firefox. I closed the gmail tab, and the mail was sent by Evolution...

---

### Post by Groucho Marxist on 2010-05-01
I was having trouble myself with this issue until I came across [this website]("http://boolix.net/2010/04/22/configure-evolution-to-use-goggle-mail-with-imap-and-ssltls/"). It's instructions were straightforward and I can now send and receive my mail without problems :)

---

### Post by theronb on 2010-08-21
I just tried it and found I had to use SSL and Plain - no apparent consistency.

---

### Post by Ehrman on 2011-07-24
I don't understand why, but AndyWhite's steps above worked perfectly.  Thank you.

---

### Post by barnabasbarty on 2012-02-02
If you've ensured that all receive and send settings are correct...I've found that you have to make sure the User Name is the same in the Evolution email account and the Username for the Gmail account.  After I had issues sending, this turned out to be the issue for me.

---

