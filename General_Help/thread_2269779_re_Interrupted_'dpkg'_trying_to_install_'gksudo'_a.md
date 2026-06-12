---
title: "re: Interrupted 'dpkg' trying to install 'gksudo' and 'leaf'"
date: 2015-03-18
forum: General Help
---

### Post by fallsoff on 2015-03-18
Hi all,
My error message is: 

"dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem". 

However  'sudo dpkg --configure -a' only yields the following:

"dpkg: error: parsing file '/var/lib/dpkg/updates/0003' near line 0: newline in field name `#padding''

Opening '/var/lib/dpkg/updates/0003' shows well over 100 '#padding' lines, and I cannot delete a one without changing permissions, and even at that <which> '#padding' line (?)  becomes an issue. I just want to get along with my adventure. I was half asleep and didn't realize 'dpkg' was still running when I closed the terminal.

I did search the forum but did not find anything relevant. The nearest topic  involved an Edgy installation issue. Please forgive me if I am in the wrong forum or somehow missed my topic in searching.

Any good ideas would be appreciated.
Thanks in advance,
Fallsoff (off 'motorcycle', actually)
Linux user number  37677

---

### Post by jimmyh1972 on 2015-03-18
delete the lines as root so you dont need to escalate permissions

---

