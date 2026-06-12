---
title: "thunderbird doesn't work after upgrade"
date: 2005-04-18
forum: General Help
---

### Post by hedu on 2005-04-18
I upgraded to hoary without any problems. Then I started Thunderbird and everything worked fine. After a reboot of my computer I started Thunderbird again. I don't see anything. The program starts but my folders don't appear (see screenshot).

I found in a different [Thread](http://www.ubuntuforums.org/showthread.php?t=24556&highlight=thunderbird) that I should rename the *.msf files. I tried this but it didn't help at all.

A strange thing I noticed is this: When I go with mouse where the folders should be and I drag and drop (even though I don't see anything) the mouse look changes. It looks like the folders are there but I just cannot see them

Thanks for the help

HEDU

---

### Post by Leif on 2005-04-18
This may not be the solution you're looking for, but have you tried re-installing ? And if your mail is IMAP, you might consider deleting .mozilla-thunderbird/ as well (complete removal option under synaptic).

---

### Post by hedu on 2005-04-19
Yes I tried reinstalling. But I save the .mozilla-thunderbird directory because I also use pop3 accounts and I don't want to loose my mails in my local folders either. After reinstalling it works again. But closing TB and reopening it will lead to the same problem again. I don't want to reinstall TB everytime I want to use it. 

So no, this is not a solution to my problem.

---

### Post by hedu on 2005-04-19
Ok it looks like it's a problem of TB 1.0.2
I upgraded to TB 1.0.3 like this:

sudo wget [http://mirror.aarnet.edu.au/debian/pool/main/m/mozilla-thunderbird/mozilla-thunderbird_1.0-3_i386.deb](http://mirror.aarnet.edu.au/debian/pool/main/m/mozilla-thunderbird/mozilla-thunderbird_1.0-3_i386.deb)

sudo dpkg -i mozilla-thunderbird_1.0-3_i386.deb

Now it works without any problems

---

