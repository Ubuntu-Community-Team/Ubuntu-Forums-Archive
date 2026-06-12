---
title: "phpmyadmin help"
date: 2007-12-19
forum: General Help
---

### Post by jeff00z28 on 2007-12-19
I have been using this for about 6 months. It randomly stopped working. I tried to install flash a few weeks ago if that caused anyhting. The phpmyadmin folder is still there in the home directory. When I try to load it it just shows me a blank white page. I need this to work. I don't have all of the data backed up. Or if there was a way to soemhow just see the records w/o the applicationt hat would work. Thanks.

---

### Post by reckless2k2 on 2007-12-19
i would uninstall and reinstall it via synaptic. it shouldn't be in your home directory anyway so i'm not sure what you are talking about. did you install via synaptic/apt-get or did you compile from the source?

---

### Post by jeff00z28 on 2007-12-19
i installed it w/ apt-get. If i reistalled it wouldnt i lose my datea?

---

### Post by reckless2k2 on 2007-12-19
your "data" is in mysql. phpmyadmin is only an interface to mysql. you can remove and reinstall phpmyadmin as you like. i certainly do. hahaha.

---

### Post by roelandp on 2008-02-19
Hi, 

I found a possible solution on FlashAPe's blog.

If you have a white page consider pasting [PHP]main.php?lang=en-utf-8&server=1[/PHP] behind the dir of your phpmyadmin.

[www.domain.tld/phpmyadmin/](www.domain.tld/phpmyadmin/) <- here!

After logging you have to do the following:

> then change your theme. I had to click on teh “Theme/Style” link, because there was only one theme in the dropdown menu, then click on the “take it” link in the popup window.
After that everything was cool like a couple of little fonzies. hope that helps.

update
looks like you need to do this for each browser you want to use phpMyAdmin with.

Check it out at [http://www.visible-form.com/blog/phpmyadmin-blank-page-bug-fix/]("http://www.visible-form.com/blog/phpmyadmin-blank-page-bug-fix/")

---

