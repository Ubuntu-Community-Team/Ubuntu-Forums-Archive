---
title: "Nautilus on Xubuntu can't open files properly"
date: 2018-09-13
forum: General Help
---

### Post by otlsmoz on 2018-09-13
Hey. I just installed Nautilus on my almost fresh install of Xubuntu because I prefer it over Thunar. Problem is it can't open files properly: for example if I try to open an image or archive file by double clicking, nothing happens except the animated "working" icon appears beside my cursor for a rather long time. Right click + "Open With *preferred application*" doesn't work either. Right click + "Open With Other Application", however, works with whatever application is fit to handle the file in question. Any ideas as to why this occurs and how to fix it? No such behavior occurs in Thunar. Thanks.

Edit: I just noticed that Nautilus opens files just fine when it is NOT set as a preferred application. When I set it as the preferred file manager, it breaks. Weird.

---

### Post by paolobenve on 2018-09-29
I have the same issue on various xubuntu+nautilus install. Who can help me?

---

### Post by #&amp;thj^% on 2018-09-29
If Nautilus is set as the preferred file manager with "exo-preferred-applications", it no longer opens files. It opens only directories,

Once Nautilus is unset as the default file manager (Thunar is chosen, for example), it starts to work fine again, opening files properly.

I doubt this will be fixed anytime soon.
See Bug Report here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1778069](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1778069)
So to sum it up if you use Nautilus on Xubuntu unset nautilus as preferred.
I myself find Thunar a very nice file manager. ;)

---

### Post by oldos2er on 2018-09-29
> **paolobenve said:**
> I have the same issue on various xubuntu+nautilus install. Who can help me?

Please start your own thread; thread "hijacking" is considered rude here, and is confusing for everyone involved.

Thanks.

---

