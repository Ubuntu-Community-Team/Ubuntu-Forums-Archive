---
title: "Thumbnails in nautilus?"
date: 2007-01-03
forum: General Help
---

### Post by rioghal on 2007-01-03
Whenever I view graphics in nautilus, I see that a ~/.thumbnails directory is created. How can I stop that directory from being created? Is there a setting in gconf-editor or nautilus or something? I have the following settings in nautilus (see attahcment)

---

### Post by kerry_s on 2007-01-03
That's a feature in most browsers to speed up browsing. You can just delete it from time to time or if your browsing alot of pics. It will always be created again. But if you really don't mind you can do this->
Delete the .thumbnails folder & open terminal there, put this for the command-> ln -s /dev/null /home/"user"/.thumbnails

Replace "user" with the account name. Remember you will no longer get thumbnail pics at all & there could be some problems. You do at your own risk.

---

### Post by kinematic on 2007-01-03
> **kerry_s said:**
> That's a feature in most browsers to speed up browsing. You can just delete it from time to time or if your browsing alot of pics. It will always be created again. But if you really don't mind you can do this->
Delete the .thumbnails folder & open terminal there, put this for the command-> ln -s /dev/null /home/"user"/.thumbnails
.

shouldn't that be ln -s /home/username/.thumbnails /dev/null so that the thumbnail folder is linked to /dev/null instead of /dev/null being linked to .thumbnails....

---

### Post by kerry_s on 2007-01-03
> **kinematic said:**
> shouldn't that be ln -s /home/username/.thumbnails /dev/null so that the thumbnail folder is linked to /dev/null instead of /dev/null being linked to .thumbnails....

No, it goes= location-> link name

---

### Post by kinematic on 2007-01-03
you're absolutely right....my mistake ](*,)

---

### Post by kerry_s on 2007-01-03
> **kinematic said:**
> you're absolutely right....my mistake ](*,)

Just remember the order, that kind of mistake as root can toast your system. Luckily in this instance it would be harmless, you would just get a error.

---

### Post by rioghal on 2007-01-04
> **kerry_s said:**
> That's a feature in most browsers to speed up browsing. You can just delete it from time to time or if your browsing alot of pics. It will always be created again. But if you really don't mind you can do this->
Delete the .thumbnails folder & open terminal there, put this for the command-> ln -s /dev/null /home/"user"/.thumbnails

Replace "user" with the account name. Remember you will no longer get thumbnail pics at all & there could be some problems. You do at your own risk.
Hmm.. it's nice to know that this can be done and thank you for the tip. However, you mentioned "could be some problems", so I think I'll just leave it as is and add a "rm -r ~/.thumbnails" daily cronjob. That should take care of it for me.. I was just worried about wasting disk space but that isn't such a big deal on a 200Gb drive.

---

### Post by reclusivemonkey on 2007-01-05
You can also turn off the creation of thumbnails in the Nautilus preferences.

---

### Post by rioghal on 2007-01-05
> **reclusivemonkey said:**
> You can also turn off the creation of thumbnails in the Nautilus preferences.
How can I do that? As seen by the thumbnail I posted with the original question, I thought I had done that but it didn't stop nautilus from creating the ~/.thumbnails dir.

---

### Post by rioghal on 2007-01-09
Bump

---

### Post by emarkay on 2007-01-28
> **rioghal said:**
> How can I do that? As seen by the thumbnail I posted with the original question, I thought I had done that but it didn't stop nautilus from creating the ~/.thumbnails dir.

Anyone know how to do this?  I see no option to disable CREATING thumbnails.

---

### Post by emarkay on 2007-01-28
I'll add a new topic on this one.

---

