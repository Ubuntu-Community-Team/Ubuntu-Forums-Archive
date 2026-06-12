---
title: "completely purge firefox"
date: 2016-08-09
forum: General Help
---

### Post by courtney2 on 2016-08-09
I want to run firefox nightly on my ubuntu 16.04 install, but whenever I try to run Mozilla's firefox binary from source (not the ppa) it still runs firefox that is packaged with ubuntu!

I did an apt-get purge firefox to remove it and looked for anything resembling firefox, but it still runs Firefox 47 instead of nightly 51. How can I completely nuke firefox from my install so it only recognizes the nightly binary when I try to run it?

---

### Post by &amp;KyT$0P# on 2016-08-09
It really should be gone after [FONT=Courier New]sudo apt-get purge firefox*[/FONT] ...

How are you running Firefox?
Did you download the Mozilla binary .tar.bz2 from mozilla.org (or download-installer.cdn.mozilla.net) or somewhere else?

---

### Post by howefield on 2016-08-10
Testing a purge here for Firefox leaves the ~/.mozilla folder intact. Try removing (or possibly better, rename ) that folder if it did not get removed, to force a new profile to be created.

---

