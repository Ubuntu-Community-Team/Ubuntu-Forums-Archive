---
title: "How do I install kde and remove gnome?"
date: 2007-06-20
forum: General Help
---

### Post by cdiem on 2007-06-20
After reading a tutorial at psychocats.net and trying kubuntu-desktop, I liked it very much. It is removed now, but I wanna switch to KDE. Is there a way to install kde and all the applicaions there (kaffeine, amarok, knetworkmanager, etc.) and remove gnome? I want to try everything in kde, not only kde-core or something; every single last program there. Would this be possible, without having to reinstall my computer with a kubuntu disc?

---

### Post by Bachstelze on 2007-06-20
You can install all of kde with just

```
sudo apt-get install kde
```

Amarok, Kaffeine of KWIFIManager are not in there, though...

---

### Post by cdiem on 2007-06-20
That's what I mean; do I have to manually install all such applications afterwards? And, I'd like to remove gnome and all the metapackages of it, because I think kde would be faster if I remove it. I'd like to concentrate on qt applications. How do I remove gnome? Would something like sudo aptitude remove ubuntu-desktop work? Or do I have to run sudo aptitude remove gnome?

---

### Post by Bachstelze on 2007-06-20
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

This will tell you how to remove gnome. As for the extra KDE apps like Amarok and friends, yes, you'll have to install them separately after you've installed KDE, as they're not part of KDE itdelf.

---

### Post by cdiem on 2007-06-20
Stupid me spamming; I think I saw the solution at the purekde section of psychocats.net. Removing ubuntu feisty would be a big pasting of programs in the terminal.

---

### Post by cdiem on 2007-06-20
Thank you; I just now saw your answer :)
And this about the applications sound actually great; thus I will configure the system with the apps I like. 
Thanks again.

---

### Post by rakku-toki telkio-kuuni on 2007-06-20
I think if you don't want to have all the apps installed, you should install *kde-core*, instead of *kde*!

from [http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core):

    * kdebase - This is the absolute bare minimum to run KDE. You will get very little frills, and you may be missing what you consider a lot of essential software.
    * kde-core - This metapackage contains another minimal configuration for KDE but has enough to satisfy most users. The one major missing component is kde-guidance, the package that allows you to configure in the control panel preferred screen resolution and refresh rate.
    * kubuntu-desktop - This is Kubuntu's default set of applications and services.
    * kde - Everything but the kitchen sink... actually, this may have the kitchen sink, too! This metapackage points to all the KDE-related packages available.

---

### Post by Qu4k3R on 2007-06-20
Remove ubuntu-desktop window manager [with aptitude]

> 
sudo aptitude update
sudo aptitude remove ubuntu-desktop


Then remove all gnome applications listed in psychocats site:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)


PS:
You can use KDE (windows manager) and have both KDE and GNOME installed..

---

