---
title: "Where's frostwire"
date: 2006-12-08
forum: General Help
---

### Post by Russty of Oz on 2006-12-08
I want to install frostwire, but it is not showing up in Automatix, does anyone have any idea where it is, or is there something else that is preferable?

Russty

---

### Post by ciscosurfer on 2006-12-08
> **Russty of Oz said:**
> I want to install frostwire, but it is not showing up in Automatix, does anyone have any idea where it is, or is there something else that is preferable?

RusstyI like it.  You can always download it from here if Automatix is giving you trouble: [http://www.peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb](http://www.peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb)

But, here's the order I would do it in:[LIST=1]
[*]Make sure Java is installed first >>```
sudo aptitude install sun-java5-jre sun-java5-bin sun-java5-plugin
```
[*]Then link that sucker up in the alternatives```
sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
```
[*]Download the Frostwire .deb file from here: [http://www.peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb](http://www.peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb) and then install it```
sudo dpkg -i frostwire-4.13.1.i586.deb
```
[*]Run the following two commands in a terminal as well to get Frostwire working correctly:```
sudo sed -i -e's/^#!\/bin\/sh/#!\/bin\/bash/' /usr/lib/frostwire/runFrost.sh
sudo sed -i -e's/^sh runFrost\.sh/bash runFrost\.sh/' /usr/bin/frostwire
```This is done, btw, so you don't have to reconfigure Edgy's default shell, Dash.  If you would rather reconfigure the default shell from Dash back to Bash, you can follow do the following and select "No" when prompted to install Dash.  Additionally, you can ignore the code in Step 4 if you issue the following:```
sudo dpkg-reconfigure dash
```
[*]You're all set![/LIST]

---

### Post by Russty of Oz on 2006-12-08
OK, but why is it not available in Automatix anymore?

---

### Post by Russty of Oz on 2006-12-08
I just installed Automatix2 and there was frostwire, so all is fixed!:D

---

### Post by ciscosurfer on 2006-12-08
> **Russty of Oz said:**
> I just installed Automatix2 and there was frostwire, so all is fixed!:DI was going to ask if you were using Automatix or Automatix2...glad you got it all straightened out.

My post above can serve as a reference if things ever get borked with it though. 

--And/or as a way of installing it for other users who don't want to use Automatix2.

:D

---

