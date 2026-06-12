---
title: "Is Kmail WITHOUT KDE Wallet possible? HELP!"
date: 2007-05-16
forum: General Help
---

### Post by thayerw on 2007-05-16
I'm going *out of my mind* with this and would appreciate any help at all at this point.  Yesterday, I migrated to KMail (Kontact actually) after being a diehard Mozilla Thunderbird user for years.  

I thought everything went peachy keen, until I realized that KDE Wallet had stored the POP account passwords, requiring me to enter my wallet password every time I open Kontact.  Naturally, I removed the entries from KDE Wallet and told Kontact to store the passwords locally instead.  This works great--until I close and re-open Kontact...then none of the accounts can authenticate and I am presented with this error:

**Error - KMail**

*Could not login to mail.mydomain..ca. The password may be wrong.  The server said: "Login failed."*

-- or sometimes it shows this instead --

*The server said: "[AUTH] Username and password not accepted."*

Yet, when I enter the password again and click "Store password" it works for the rest of the session until I close KMail (or Kontact, I've tried both) and then the errors occur again the next time I start it.  I haven't found ANY solutions to this, but there seems to be a lot of unanswered threads pertaining to it.

ANY help would be greatly appreciated at this point. Thanks in advance!

So far I've tried the suggestions in these threads and nothing has worked:

**Re: Kopete/KDE Wallet/Passwords**
[http://ubuntuforums.org/showpost.php?p=563665&postcount=2](http://ubuntuforums.org/showpost.php?p=563665&postcount=2)
[B]
kde wallet/kmail problem[/B]
[http://ubuntuforums.org/showthread.php?t=285282](http://ubuntuforums.org/showthread.php?t=285282)

**Forcing KMail to stop trying to use KDE Wallet?**
[http://ubuntuforums.org/showthread.php?t=1838100](http://ubuntuforums.org/showthread.php?t=1838100)

**kmail password annoyance**
[http://ubuntuforums.org/showthread.php?t=236972](http://ubuntuforums.org/showthread.php?t=236972)

---

### Post by strabes on 2007-05-17
Have you removed the password from the specific wallet that kontact is using? That's what I did with knetworkmanager so that it just connects automatically to my wifi networks.

---

### Post by thayerw on 2007-05-17
Yes, shortly after I posted here I gave up and just stripped the password from Kwallet.  I think it's sad though that that's the only real solution to this problem.  I'm uncomfortable with the idea of having my passwords available in plain text.  Of course, it wouldn't be so bad if you could create a separate wallet just for KMail, but I tried that as well and KMail still prompts to access the "default" wallet even if the passwords are already stored in a secondary wallet.

I store my really sensitive information in PwManager, but Kwallet does have it's uses for network passwords... well, DID have it uses.  I won't save SSH info in a password-free wallet.

I guess the real question is whether I made a mistake in choosing KMail/Kontact as a PIM.  Thunderbird/Lightning isn't a realistic solution for calendaring, and Evolution seems to be even more abandoned than Kontact.  I hope the KDE developers are just focusing on KDE4 at the moment and aren't all together giving up on Kontact--even their website info is stale.

I hate the idea of running MS Outlook under GNU/Linux just to have a working PIM.

---

### Post by seamless on 2007-05-17
[QUOTE="thayerw"]Evolution seems to be even more abandoned than Kontact.[/QUOTE]
The latest release of Evolution was made 8 days ago... The release before that was less than a month ago. Svn was last updated 5 hours ago... Evolution is far from abandoned and is being actively worked on. Maintained as well as enhanced.

---

### Post by thayerw on 2007-05-17
My mistake then regarding Evolution.  I had tested it when I was running Ubuntu and when it came to finding solutions, the majority of posts and articles I found spoke of how stale the feature set was becoming due to the fact that not many were working on it these days.  To make matters worse, the Evolution website seems to avoid timestamps of any kind--versions, news, etc.  The last changelog is dated Oct 2004.

---

