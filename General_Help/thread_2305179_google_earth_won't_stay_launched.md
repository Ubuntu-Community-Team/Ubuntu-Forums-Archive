---
title: "google earth won't stay launched"
date: 2015-12-03
forum: General Help
---

### Post by wbmpe2 on 2015-12-03
after opening, it immediately closes. Any ideas?

Tnx, wbmpe

---

### Post by wbmpe2 on 2015-12-03
When I click on it to open it, it opens and then immediately closes without input from me. 
I would like to remove the google earth files completely and reinstall it, but don't know how to do this.
Could some one please give me a tutorial on how to do this or possibly suggestions on how to fix my problem.

Regards, wbmpe

---

### Post by tgalati4 on 2015-12-03
Try running it in a terminal.  Open a terminal:

```
googleearth --debug
```

How you fix it depends on how you installed it.  In 14.04 there is a package:

> tgalati4@Mint17 ~/Desktop $ apt-cache search google earth
google-earth-stable - Explore, search and discover the planet
googleearth-package - utility to automatically build a Debian package of Google Earth


To find out where it resides:

```
locate earth
```

---

### Post by Ricardo_Velasco on 2015-12-03
Greeting:

In my past I have also this problem with Google Earth and I recommend that you follow these steps to install it again ..

After the tutorial or if you remeber the first steps off the box to always show the Home appears ..


If it works not installed :

> sudo apt-get install lsb-core

For 64-bit operating systems

And for 32-bit operating systems :
> 
sudo apt-get install ia32-libs

If you are in the operating system Ubuntu LTS 14 then try to run this command:

> mv ~/.googleearth ~/old_googleearth 





Then if you follow these instructions you must be able to open the Google Earth but there is a serious average error on a black screen at the beginning ..

I wish I could spend the instructions but on this page you can install Google Earth smoothly ..

I also had these 2 disadvantages that would not open to me and separate me a black screen appeared ..

But follow my instructions and the instructions on the page that 'll give you and you can have without problems Google Earth
> [http://ubuntuhandbook.org/index.php/2014/10/install-google-earth-ubuntu-14-10/](http://ubuntuhandbook.org/index.php/2014/10/install-google-earth-ubuntu-14-10/)

But first check if your graphics card supports 3D functions to run:
> 
/usr/lib/nux/unity_support_test -p  

---

### Post by sandyd on 2015-12-03
Threads Merged.

Please start one thread per topic as not to dilute community effort.

Thanks!

---

