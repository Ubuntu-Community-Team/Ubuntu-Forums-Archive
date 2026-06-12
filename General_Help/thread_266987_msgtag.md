---
title: "msgtag"
date: 2006-09-28
forum: General Help
---

### Post by pandanuma on 2006-09-28
How can I stop msgtag's in my emails?

I just received an email with a message at the bottom that reads:

MSGTAG has notified the sender that this message has been received.

I have evolution 2.6, set to 'never send message receipts', yet this embedded code automatically sends a receipt.

I checked out the msgtag.com site and thats how it is supposed to work but I would like to know when I am sending info.

also, could this be a security issue?

---

### Post by Jussi Kukkonen on 2006-09-28
> yet this embedded code automatically sends a receipt.
No, it **says** it automatically sends a receipt. There's a difference.

They use html mail features. The method may work if your mail client runs javascript or loads external images. Otherwise it's bollocks. Personally I suggest turning html email off altogether, it's an evil invention.

It's a security issue in the sense that e.g. spammers can use it to find out if you've read the spam.

---

### Post by pandanuma on 2006-09-28
I knew I should have said "yet this embedded code sends a receipt *without my consent*."

If I turn off my html email, will that stop this type of intrusion?

I will try disabling javascript and external images.

As for spam and security, I wonder what happens if you forward an email with the msgtag code in it??

---

### Post by Jussi Kukkonen on 2006-09-28
> If I turn off my html email, will that stop this type of intrusion?
Yes. So should disabling javascript and loading external images.

> As for spam and security, I wonder what happens if you forward an email with the msgtag code in it??
The receiver will have the same privacy problems -- although the system might mis-identify the recipient, i.e. think that you are reading the mail again...

---

### Post by jvaudrey on 2007-02-24
Hello

I have used MSGTag in the past and this is how it works.

You type an email and click send, its process by the MSGTag program on your pc which inserts an image tag on the end of the email (converting it from a Text document to HTML if required)

When the recipient opens the email the image is loaded from the MSGTag servers and an email is sent to say the recipient has opened it.  If you forward it on to someone else they do not send another email to the original sender to say it has been read.

To be honest I've not told you anything you could not find out by checking their website.

---

