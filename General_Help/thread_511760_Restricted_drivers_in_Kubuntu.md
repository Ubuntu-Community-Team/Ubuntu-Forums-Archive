---
title: "Restricted drivers in Kubuntu?"
date: 2007-07-28
forum: General Help
---

### Post by knadoor on 2007-07-28
Hi,

How do I access restricted drivers in Kubuntu?

And lastly for the DVD release of Kubuntu, will it contain KDevelop in it?

thanks :)

---

### Post by dreadlord_chris on 2007-07-28
> **knadoor said:**
> Hi,

How do I access restricted drivers in Kubuntu?

And lastly for the DVD release of Kubuntu, will it contain KDevelop in it?

thanks :)

```

kdesu restricted-manager

```

There is a chance that restricted-manager isn't installed on your Kubuntu system (it wasn't on mine) - if this is the case:
```

sudo apt-get install restricted-manager

```

I have no answer for your second question....

---

### Post by knadoor on 2007-08-02
Thanks.

But once installed using that command will it install and function just like the restricted drivers manager in Ubuntu??

---

### Post by Vince4Amy on 2007-08-02
Yes it does function the same as the one in Ubuntu. It will download Synaptic package manager.

---

### Post by dreadlord_chris on 2007-08-02
> **knadoor said:**
> Thanks.

But once installed using that command will it install and function just like the restricted drivers manager in Ubuntu??

They are one and the same - so yes...

---

### Post by dreadlord_chris on 2007-08-02
> **Vince4Amy said:**
> Yes it does function the same as the one in Ubuntu. It will download Synaptic package manager.

huh? It won't download Synaptic Package Manager - the Restricted Manager downloads & installs drivers...

---

### Post by Vince4Amy on 2007-08-02
It does download it. The Restricted manager package includes the Synaptic package manager in order to work properly.

---

### Post by dreadlord_chris on 2007-08-02
> **Vince4Amy said:**
> It does download it. The Restricted manager package includes the Synaptic package manager in order to work properly.

Huh, what do you know - it does.... 
Never noticed since Synaptic is one of the first things I install in Kubuntu - just never really liked Adept....

:lolflag:

---

### Post by knadoor on 2007-08-02
I don't have Kubuntu installed right now, I'll install 7.10 when it's released over my summer break (have uni now) but wanted to clear a few things up.

Also, how would you access these restricted drivers? Obviously the Gnome Desktop is different to KDE's. :)

---

### Post by dreadlord_chris on 2007-08-02
> **knadoor said:**
> I don't have Kubuntu installed right now, I'll install 7.10 when it's released over my summer break (have uni now) but wanted to clear a few things up.

Also, how would you access these restricted drivers? Obviously the Gnome Desktop is different to KDE's. :)

Alt-F2 and type in restricted-manager
should work in either GNOME or KDE

edit: Now that I think about it - I do believe it needs to be run with root privs, so
GNOME:
```

gksudo restricted-manager

```
and KDE:
```

kdesu restricted-manager

```
should do the trick....

---

