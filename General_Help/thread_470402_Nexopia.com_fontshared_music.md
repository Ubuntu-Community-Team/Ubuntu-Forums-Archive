---
title: "Nexopia.com font/shared music"
date: 2007-06-10
forum: General Help
---

### Post by Grazfather on 2007-06-10
Hey guys, only my faisty distro I noticed (after installing the firefox widgets) most sites look nice, however, nexopia.com doesn't.  It's just the font, it's not the same as it is on windows. I'm just wondering how to find this font, and install it.  Also, are there some recommended font packs to install or something similar? thanks.

[http://www.nexopia.com](http://www.nexopia.com)

Second question.  This computer is used by a couple people, what i want to do is have a shared folder where everyone can throw music, and allow read and write permissions (for editing id3 tags, adding album covers, and obviously saving files) I made a directory /usr/share/music and chmod 777'd it, but the problem is its new music files default to RW for the user only, any way I can do it/How do you guys set up shared music? What do you think is best?

Thanks a lot.

---

### Post by disposable on 2007-06-11
For sharing music, create a group, say 'music', and add the users to that group. Then create your shared folder, say 'tunes', and then 'chgrp music tunes'. Finally, 'chmod 775 tunes' (don't want world-writable). Can't help w/ nexopia.

---

### Post by Grazfather on 2007-06-12
okay cool. What about files downloaded to that folder by a personal user say from ktorrent... do they default to group writeable? 'chmod -R'-ing every time i get music isn't convenient.

---

### Post by disposable on 2007-06-12
You're correct -- the files default to the owners primary group. So either chgrp the files or change the primary GID for the users in /etc/passwd.

---

