---
title: "A Few Issues"
date: 2005-06-27
forum: General Help
---

### Post by gdboling on 2005-06-27
I just installed Ubuntu and everything seems to be running just fine.  However, I am having a few issues with software udpates.  I've noticed that things seem a bit out of date.  For example, I can only apt-get firefox 1.2 and when I installed the desktop-calendar application it only has months through April.  So it would seem that my respository is a couple of months behind.  I've done an apt-get update and have also added a few sites to my sources.list but it doesn't seem to change anything with the newer versions.

Is there something I am missing?

Oh, and one more thing.  When I install flash for mozilla from Synaptic flash hangs firefox.  Any help would be appreciated.

Gregg Bolinger

---

### Post by antwerx on 2005-06-27
Hello -  I found** [The Unofficial Ubuntu Guide](http://ubuntuguide.org/) **to be a great help for your specific question.

Essentially there are other Apt Sources to add. These are the **Universe Sources**. However they are more bleeding edge etc thus potentially less stable. 

I have not had any problems using the Universe sources so far except for attempting to add a quick launch to the Gnome Panel for Tux Paint. My daughter loves Tux Paint. 

Apparently it clobbered the Gnome Panel config and had to delete the default config file so beaware of that one for sure.

---

### Post by gdboling on 2005-06-27
[QUOTE=antwerx]Hello -  I found** [The Unofficial Ubuntu Guide](http://ubuntuguide.org/) **to be a great help for your specific question.

Essentially there are other Apt Sources to add. These are the **Universe Sources**. However they are more bleeding edge etc thus potentially less stable. 

I have not had any problems using the Universe sources so far except for attempting to add a quick launch to the Gnome Panel for Tux Paint. My daughter loves Tux Paint. 

Apparently it clobbered the Gnome Panel config and had to delete the default config file so beaware of that one for sure.[/QUOTE]

Thanks. I've looked at that guide and have added the locations and then did an update to apt-get.  Still not getting newer versions.  I will check it again to make sure I did everything correctly.  Thanks.

Gregg

---

### Post by gdboling on 2005-06-27
Ok, it seemed to pick up some more updates.  However, firefox is still only 1.0.2 when it should be 1.0.4.  Is there a good way to manually install it?  So that it is part of the repositoty and apt knows that it has been updated?

---

### Post by angkor on 2005-06-27
[QUOTE=gdboling]Ok, it seemed to pick up some more updates.  However, firefox is still only 1.0.2 when it should be 1.0.4.  Is there a good way to manually install it?  So that it is part of the repositoty and apt knows that it has been updated?[/QUOTE]

I think 1.0.4 is in the backports repos. 

But remember Ubuntu doesn't include program (version) upgrades during the 6 months release, it just includes security updates. The Ubuntu firefox package (1.0.2) does get all the security fixes but doesn't change it's version number. 

If you want bleeding edge software (less than 6 months old) you'll need to install it manually or request a backport.

---

### Post by gdboling on 2005-06-27
Ok, I understand now.  Thanks.  I appreciate the information.

---

