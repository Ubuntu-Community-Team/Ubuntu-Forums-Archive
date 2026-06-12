---
title: "[SOLVED] Request for opinions - full disk encryption on Gutsy"
date: 2007-12-13
forum: General Help
---

### Post by Barnable on 2007-12-13
Can someone give me their experiences of using the full disk encryption from the Gutsy alternate install CD, please.

I have read the articles on these forums and have looked at the screenshots on an article on softpedia but am confused as to how it would work with a laptop (which is what it's aimed at, presumably) - there aren't exactly any testimonials, or comparisons of performance with or without the encryption.

When you boot up, your box has to decrypt the whole filesystem - doesn't that impact on battery life and bootup time?

Also, what happens if your box shuts down because the battery runs low? There won't be enough power to run the encryption, will there, so your data remains clear.

I would really appreciate some comments on this, thanks.

---

### Post by tighem on 2007-12-13
I use full disk encryption on my system and to answer your questions:

1) It's really easy to do off the alternate CD, as long as you follow the defaults.
2) One would imagine there is some minimal hit to performance and battery life, but again, that should be minimal
3) Running low on battery wouldn't be an issue. The system asks you for a pass-phrase when you log in that unencrypts the keys and those are used to decrypt the drive. The drive itself is encrypted period so as long as an attacker does not have access to an active session they get nothing but junk.

The basic idea here is not theft prevention - it's data protection. Thief steals your laptop, sees there's nothing usable on the drive and wipes it and loads something else on it.

---

### Post by Barnable on 2007-12-14
Does that mean that the system decrypts files "on the fly", as you use them? Surely that makes a big hit on performance and battery life?

Can I ask, are you using full disk encryption on a laptop or desktop?

Sorry to pester!

---

### Post by Barnable on 2007-12-20
Just wanted to say, bit the bullet and reinstalled from the alternate installer CD and put the full disk encryption in place.

It did mean the install took longer than usual, but it doesn't lengthen my boot-up time, nor does it seem to adversely affect battery life (at least, not noticably).

Thanks for your help.

---

