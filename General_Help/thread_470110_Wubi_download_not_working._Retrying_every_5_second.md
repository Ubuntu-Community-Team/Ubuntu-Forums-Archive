---
title: "Wubi download not working. Retrying every 5 seconds."
date: 2007-06-10
forum: General Help
---

### Post by Tomtomtomjacobs on 2007-06-10
I select my username and password then the next screen of the installer tries to download Ubuntu-7.01-alternative-i386.iso and keeps on just saying "retrying in 5 seconds" over and over.

Is the server down?

Can we not have the setup dependent on a server? Can we please have a standalone download of the installer?

Even that could be torrented up. As long as I can always install it!

Tom.

---

### Post by ecology2007 on 2007-06-10
Download this file and save it in the same directory as wubi.exe

[http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso)

Then run wubi.

---

### Post by Tomtomtomjacobs on 2007-06-10
Thanks!

Turns out my NSIS was just screwed up for some reason. Another NSIS installer was also failing to download anything. Don't know what fixed it but now it is fixed. Weird.

Now I'm waiting my 4 hours to complete the download.
What about a lighter version of Ubuntu, say fitting into a 10 minute download?

Tom.

---

### Post by CrazyGuy123 on 2007-06-11
Same issue here, except if you leave it trying for about 2 mins, it'll suddenly succeed.  I suspect it's going through a list of mirrors, and suddenly finds one that works when the others had failed for some mysterious reason (some kind of timeout? - it only seems to try for a fraction of a second before failing)

On a similar note todo with downloaders, I don't know which mirror it selects, but the built in downloader only gets 100kb/s on average on my connection, and it varys a lot, whereas I normally get 500kb/s when the servers aren't overloaded.

---

