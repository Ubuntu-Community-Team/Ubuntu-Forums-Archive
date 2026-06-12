---
title: "Which files should be included in backup?"
date: 2006-07-19
forum: General Help
---

### Post by thebasti on 2006-07-19
Hello,

A month ago our whole company switched over to Ubuntu and we have been experimenting with various ways to do backups. Finally we have settled on simple rdiff-backup as it fulfills most of our needs (one being to save files  simply as files, i.e. not using some custom format, so we can access them easily).

Anyway, my question is what are important system files/dirs that should be included in our backups?

Obviously, we'll backup /home and few other dirs that we use, but what else should be backed up? I presume that /etc should be included too, since it contains all config files. Is there anything else we need to successfully recover in case of hard failure?

---

### Post by wahman143 on 2006-07-19
I think /home and /etc about cover it - however, if you have any custom boot parameters, you may want to backup /boot as well - most of the other dirs (AFAIK) are common and would be regenerated upon reinstall if your system failed...oh, if you have any web pages/web apps, I'd include /var/www

HTH,
W.

---

### Post by thebasti on 2006-07-19
> **wahman143 said:**
> oh, if you have any web pages/web apps, I'd include /var/www

Thanks for that. We do have a lot of web apps on our computers, but we've moved web server files inside home dir.

---

### Post by wahman143 on 2006-07-19
Sweet - well that makes things easy, eh?

Good luck to you - when I backup my server, that's essentially what I include.  Unless you've remapped anything to weird locations, you should be good.

Cheers,
W.

---

