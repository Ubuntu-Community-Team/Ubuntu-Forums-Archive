---
title: "Kontact Local folders: where are they stored"
date: 2008-06-25
forum: General Help
---

### Post by paul_magarey on 2008-06-25
I have started using Kontact 1.2.4 (through my Kubuntu 7.10) and really dig it. 

I have however not been able to find where my local folders are stored. I want to upgrade to Kubuntu 8.04, but only have a live CD (not alternate CD) and am not sure if I can upgrade without erasing my disk. I want to store my email folders, particularly my sent mail, but can't find where they are. I've gone through the manual without success.

Any advice would be appreciated.

rgds,

paul

---

### Post by Zorael on 2008-06-25
I think they're located in **~/.kde/share/apps/kmail/mail**, but don't quote me on that. I don't use Kontact (and by extension, kmail) myself.

**~/.kde/share/apps/** generally contains "heavier" configuration files for KDE apps. Like extra installed applets (kicker), temporarily saved torrents (ktorrent), logs (kopete, konversation), etc. So I can't imagine your mails being saved elsewhere than in kmail's own directory.

"Lighter" configuration files are similarily stored in **~/.kde/share/config/**. You can find kmailrc, kontactrc, kopeterc, kwalletrc and a whole slab of other such files there.

Hope that helps somewhat.

---

