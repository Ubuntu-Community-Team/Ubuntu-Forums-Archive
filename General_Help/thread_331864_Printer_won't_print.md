---
title: "Printer won't print?"
date: 2007-01-05
forum: General Help
---

### Post by yezzer on 2007-01-05
Hey board,

i've managed to install my Canon LBP-1120 printer using the guide [here]("http://www.ubuntuforums.org/showthread.php?t=81454") (with a few changes, i had to use:
chmod a+rw /dev/usblp0 )

Anyway - i've got the printer installed - but it wont print. it's connected correctly, the printer itself works ok on my windows machine, but when i print something, it gets added to the printer queue, hangs around for a few seconds, then disappears! This is the same with a test page or printing from gedit.

Any ideas anyone? Are there any log files i can look at anywhere?

Cheers

---

### Post by gwpritch on 2007-01-05
The most likely problem is that the wrong driver is loaded. I would go back and double check which one you are using. I had a similar problem recently which was resolved by installing a generic driver. Sorry, I don't have a Canon so I can't advise you on which is most appropriate

---

### Post by yezzer on 2007-01-05
i've been playing around with this for ages now!

through googling, i found that this log might be of use:
/var/log/cups/error_log

and this error is repeated hundreds of time in the log:

E [05/Jan/2007:13:29:31 +0000] cupsdAuthorize: Local authentication certificate not found!

so i've googled this, and i cant find any way of getting this working.. bear in mind my knowledge of *nix is minimal, i'm a windows guy that's trying to convert :)

I kinda feel a bit let down by this actually - printing is a reasonably basic thing to ask for, and it's a shame it doesnt work straight off like most things in ubuntu do! 
Never mind, ubuntu *is* great, and it'll only get better... :D

---

### Post by gwpritch on 2007-01-05
I've just had a look at the instructions you were following and see that they were for a system running Breezy. If you are not using Breezy, rather Dapper or Edgy I would not be suprised if this is not the appropriate driver for you.
Did you try just installing the default as detected? If you haven't received any other advise by the time I get back to my ubuntu box I will have a closer look for you. Good Luck.

---

### Post by Sigma on 2007-02-26
> **yezzer said:**
> i've been playing around with this for ages now!

through googling, i found that this log might be of use:
/var/log/cups/error_log

and this error is repeated hundreds of time in the log:

E [05/Jan/2007:13:29:31 +0000] cupsdAuthorize: Local authentication certificate not found!

so i've googled this, and i cant find any way of getting this working.. bear in mind my knowledge of *nix is minimal, i'm a windows guy that's trying to convert :)

I kinda feel a bit let down by this actually - printing is a reasonably basic thing to ask for, and it's a shame it doesnt work straight off like most things in ubuntu do! 
Never mind, ubuntu *is* great, and it'll only get better... :D

Yezzer, I had the same problem as you (printer hanging, same error message repeated hundreds of times in the error_log, etc.) and I finally realized that I was adding the printer under parallel port #1 instead of LPT #1.

Granted, I'm using a different printer (Canon BJC-240ex), but you might want to try killing any of your print processes, removing your existing printer configuration, and re-adding it it with the suggested driver under LPT #1 (if you aren't doing that already).

---

### Post by scbonney on 2007-02-26
I;m a noob but I had similar printer problems appear suddenly and found that an update I installed had left me with some essential cups files or packages missing,  I made the problem go away by using snaptic to install 2 or 3 cups packages that wern't installed.

This is not a fix, it's a possible something to try or give you ideas of what to do.:guitar:

---

