---
title: "Firefox 1.5.0.10 upgrade breaks https"
date: 2007-03-06
forum: General Help
---

### Post by rushcamera on 2007-03-06
Upgrading Firefox to 1.5.0.10 produces this when trying to connect with the "https" protocol:

Firefox doesn't know how to communicate with this server.
* Please make sure that the Personal Security Manager is installed on your system.

This appears to be a known bug:
[https://launchpad.net/ubuntu/+source/firefox/+bug/89023](https://launchpad.net/ubuntu/+source/firefox/+bug/89023)

I fixed the immediate problem by using aptitude to downgrade Firefox from
1.5.0.10-0ubuntu0.6.06.2 to 1.5.0.5-0ubuntu6.06.1

My question is: how will I know when it's safe to upgrade Firefox (on my 6.06 machine)?

---

### Post by sorceror on 2007-03-06
> **rushcamera said:**
> I fixed the immediate problem by using aptitude to downgrade Firefox from
1.5.0.10-0ubuntu0.6.06.2 to 1.5.0.5-0ubuntu6.06.1

 How do I do that? This is irritating my wife very much...

---

### Post by rushcamera on 2007-03-06
Try this to revert your version of Firefox:

open a Terminal window
type "sudo aptitude"
press the "/" key to open the Search window
type "firefox" and press OK to search
the "firefox" line should be highlighted
press the Enter key to see details
go to the very bottom line, it should show the latest version, prefaced with an "i"
while on the bottom line, press the "-" (minus) key, the line is now prefaced with "d" and highlighted in purple
press the "g" key
OK the warning about downgrading firefox from 1.5.0.10 to 1.5.0.5

Hopefully, it will fix the problem accessing secure sites via https.

However: I just updated a second machine's Firefox from 1.5.0.5 to 1.5.0.10, and Firefox did NOT break - https works fine.

Note, the machine whose "https" was broken by Firefox 1.5.0.10 has a "noapic, nolapic" boot parameter. Might that be any help to anyone who might know why this is happening?

---

### Post by rushcamera on 2007-03-07
I re-updated my Dapper box's Firefox to 10.5.0.10 today and yesterday's problem -- accessing email, https -- seems to have gone away. However, Firefox opens pages very very Slowly. Google's home page takes 75 to 90 seconds. So, the problem is Not Fixed.

---

### Post by rushcamera on 2007-03-07
OK, I downgraded Thunderbird, Firefox, and libnss3. Firefox and Thunderbird worked, fast. Then I upgraded libnss3 (and verified that libnspr4 was at latest version).

Then I upgraded Thunderbird to the latest version. Everything worked, fast. Finally, I re-upgraded Firefox to the latest version, expecting it to break again.

Wrong. Everything worked, fast. The upgrade that failed a couple of hours ago, works fine now.

If anyone has an explanation, no matter how crazy, I'd love to hear it.

---

