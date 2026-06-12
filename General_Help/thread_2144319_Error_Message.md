---
title: "Error Message"
date: 2013-05-11
forum: General Help
---

### Post by Chaosvoid on 2013-05-11
Hey, what's wrong with this? Please I need help. [http://i43.tinypic.com/28kuhu.png](http://i43.tinypic.com/28kuhu.png)

---

### Post by wildmanne39 on 2013-05-11
*Thread moved to **General Help**.*

---

### Post by Primefalcon on 2013-05-11
well sounds like some broken packages to me.... I could be wrong.... but if you have synaptic installed open it up and run from the command fix broken packages.... if not use the terminal and run the command ```
sudo apt-get -f install
```

reboot and see if your still getting the same messages.... also if you get any error output from the above command please post here

---

### Post by wildmanne39 on 2013-05-11
Please use thumbnails or url instead of large images.

---

### Post by lisati on 2013-05-11
For those who missed seeing the image, here it is (see the attachment).....

---

### Post by matt_symes on 2013-05-11
Hi

It looks like you may have a problems with the file

```
/usr/share/app-install/desktop/workrave:workrave.desktop
```

Press ALT + F2 at the same time. This will open the run window.

Copy and paste this into it.

```
gedit /usr/share/app-install/desktop/workrave:workrave.desktop
```

That will open the file in gedit.

Copy and paste the contents of that file into your next post so we can take a look.

EDIT:

Welcome to the forums :D

Kind regards

---

