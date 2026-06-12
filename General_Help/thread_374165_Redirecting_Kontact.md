---
title: "Redirecting Kontact"
date: 2007-03-02
forum: General Help
---

### Post by bob-aptllc on 2007-03-02
I just started using Kontact and want to change the location of where the personal data (messages, appointments, etc.) is saved. I know that it is stored in ~/.kde/share/apps... by default, but if I move those files how can I redirect Kontact to look in the new locations? 

Thank you!

---

### Post by bob-aptllc on 2007-03-02
From "The KMail Handbook" ([http://docs.kde.org/stable/en/kdepim/kmail/index.html](http://docs.kde.org/stable/en/kdepim/kmail/index.html)) : 

14. Can I con&#64257;gure the location of my mail folder?
    Exit KMail, make a backup of /.kde/share/config/kmailrc, then open
    it with an editor and add e.g. folders=/home/username/.mail to the
    ‘[General]’ section. Then move all your existing folders (including the
    hidden index &#64257;les) to the new location. The next time you start KMail
    will use /home/username/.mail instead of /home/username/.kde/share-
    /apps/kmail. Note that KMail will lose its &#64257;lters if you change the mail
    folder’s location but forget to move your existing folders.

---

