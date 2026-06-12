---
title: "Evolution error"
date: 2006-11-10
forum: General Help
---

### Post by pennyminstrel on 2006-11-10
Every time I try to send an e mail in evolution I'm getting the following error message:

Welcome response error: Transaction failed

I've tried unintalling and reinstalling it and searched all tht#rough the forums but the only thread which is similar hasn't been replied to so I'm womdering if nobody has the answer to this one.  But I'd be grateful if anyone has cos I really like evolution and at the moment I'm having to use webmail, which I don't.

Thanks guys

penny

---

### Post by dcstar on 2006-11-10
> **pennyminstrel said:**
> Every time I try to send an e mail in evolution I'm getting the following error message:

Welcome response error: Transaction failed

I've tried unintalling and reinstalling it and searched all tht#rough the forums but the only thread which is similar hasn't been replied to so I'm womdering if nobody has the answer to this one.  But I'd be grateful if anyone has cos I really like evolution and at the moment I'm having to use webmail, which I don't.

Thanks guys

penny

That may be due to incorrect settings for that e-mail account, you should double-check your SMTP (Sending) settings.

---

### Post by encmonkey on 2007-02-22
Hey there Pennyminstrel

I'm recently seeing the same thing, and that's after having the settings work continuously for a long period of time.  I then went through and have systematically tried almost every combination of encryption/non-encryption on sending.  Receiving IMAP email works fine, though.  

I'm opening at ticket with Speakeasy (the folks providing the smtp server) to see if they changed anything on their end.

Good luck-

---

### Post by encmonkey on 2007-02-28
I found a post from someone else that fixed it for me - it seems that Evolution was not passing along a FQDN to the provider, and that was hamming things up.  I fixed it by changing my /etc/host file to have the full domain name (me.domain.com) rather that just the host name (me).

Hope this helps.

---

