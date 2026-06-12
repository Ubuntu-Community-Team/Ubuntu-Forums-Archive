---
title: "Evolution is incredibly slow"
date: 2006-12-14
forum: General Help
---

### Post by rpkehoe on 2006-12-14
I have tried using Evolution becuase I want to use the calendar in it, but I find it to be obnoxiously slow to download email.  It is set up to hit 3 pop servers, but I know the servers are not the problem, becuase I have switched to Thunderbird instead, and it has no issues.  The vast majority of the time when I try to use Evolution, the server times out, does anyone else have this problem?  Could spam filters be the problem?

Thanks

---

### Post by dcstar on 2006-12-14
> **rpkehoe said:**
> I have tried using Evolution becuase I want to use the calendar in it, but I find it to be obnoxiously slow to download email.  It is set up to hit 3 pop servers, but I know the servers are not the problem, becuase I have switched to Thunderbird instead, and it has no issues.  The vast majority of the time when I try to use Evolution, the server times out, does anyone else have this problem?  Could spam filters be the problem?

Thanks

I have multiple POP servers with my Evolution setup, and I have no timeout issues but my Spamassassin is fairly slow.

---

### Post by chifeatures on 2008-05-11
I had also been experiencing very slow POP message downloading; I was receiving mail at about 1 or 2 messages per second. After some fiddling I found it to be Spamassasin and while I've found it to be superb, it was the culprit of slow receives.

To remedy the speed issue I turned off the Junk filter:
Edit > Preferences > Mail Preferences > Junk. Turn off "Check incoming messages for junk".

My situation is that I had 4500 emails to receive and couldn't wait the 2 or 3 hours to receive my email, well actually, my internet cut out a few times so had to start receiving from scratch twice so would have been all day!

---

### Post by cpikel on 2008-05-12
I was following this thread because I've been having the same issue after upgrade.  Actions in Evolution seemed to hang the whole system while it was trying to communicate with the gmail imap servers (only account I have hooked up in Evolution).

I had been using Thunderbird on the windows side of this system and decided to try switching over.  I'm running it with the contacts sidebar and lightning plugins and so far it has been excellent, and quick.  Folder refresh even seems to be faster than evolution pre-8.04 upgrade.

---

### Post by rpkehoe on 2008-05-12
My fix for this has been to turn off spam filtering in evolution and run everything through gmail.  I have found there filtering to be pretty good, so I just set up all my mail to forward there, then I download it pop3 from gmail.

---

