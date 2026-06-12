---
title: "true type fonts wont install"
date: 2007-03-05
forum: General Help
---

### Post by stchman on 2007-03-05
hello I have some fonts that are true type fonts that wont install.

I made a folder in /usr/share/fonts/myfonts

I then copied the fonts to that folder using sudo of course.  All were of .ttf extension.

I then ran the following command

fc-cache -f -v and most of the fonts in that folder were installed but not all of them.

Any suggestions?

Thanks.

---

### Post by yabbadabbadont on 2007-03-05
Try:

cd /usr/share/fonts/myfonts
sudo mkfontscale
sudo mkfontdir
sudo fc-cache -f -v

By the way, you can put user fonts into ~/.fonts and they should then show up.  You may need to restart X windows before they do though.

---

### Post by stchman on 2007-03-05
> **yabbadabbadont said:**
> Try:

cd /usr/share/fonts/myfonts
sudo mkfontscale
sudo mkfontdir
sudo fc-cache -f -v

By the way, you can put user fonts into ~/.fonts and they should then show up.  You may need to restart X windows before they do though.

I will give that a try when I get home.

I put the fonts in the /usr/share/fonts/myfonts folder as they would be there systemwide not just for my profile.  I made my girlfriend a profile on my laptop (very limited of course) so she can use it.  She actually likes it and thinks it is very Windows XP like in its ease of use.

---

