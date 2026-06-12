---
title: "Desktop effects could not be enabled"
date: 2008-06-03
forum: General Help
---

### Post by scottptn on 2008-06-03
Hello,
I recently installed Ubuntu 8.04 LTS . Now , when i try to enable desktop effects by going to :

System->Preferences->Appearance->Visual Effects->Extra, i get a message saying ```
 "desktop effects could not be enabled". 
```

I went through some posts on this topic in the forum, and also installed xserver-xgl package.

Now, even after installing xserver-xgl, when i try to run compiz through the terminal, i get the following output

```

Checking for Xgl:Not present
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

My video card is Via Chrome9 HC IGP, just in case you need this info.

Please help.

Thanks.

---

### Post by Forlong on 2008-06-04
You need to install the proprietary driver directly from via.
You should find it on their homepage.

But **do not** mess with /usr/bin/compiz to get the driver on Ubuntu's whitelist.
Run this instead after you have installed the driver: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)
It will help you then (in case you are actually able to run Compiz).

---

