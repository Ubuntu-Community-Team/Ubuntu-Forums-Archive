---
title: "Apparently, gutenprint is not being installed with CUPS."
date: 2021-08-04
forum: General Help
---

### Post by Acharn on 2021-08-04
After I installed Ubuntu20.04, the system detected my Canon G2010 printer but it would not print. I had  the  same problem with installations of 20.10 and 21.04. After more than a year of searching I finally stumbled on the solution at AskUbuntu yesterday. It was simple. All I had to do was enter the command ```
sudo apt install printer-driver-gutenprint
``` The correct printer driver was immediately  installed and the printer started working. It seems to me this program should be automatically installed as a part of CUPS. It is in Fedora, in which I never had a printer problem. I would like to pass this information on to the developers, but don't know how.  It doesn't seem like something I can submit a bug report on, but maybe I'm wrong about that. would appreciate some advice.This really should be corrected. The G2010 is a very popular printer here in Thailand

---

