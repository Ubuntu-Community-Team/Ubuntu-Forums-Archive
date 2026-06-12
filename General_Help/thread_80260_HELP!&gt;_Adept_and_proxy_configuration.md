---
title: "HELP!&gt; Adept and proxy configuration"
date: 2005-10-21
forum: General Help
---

### Post by chocobanana on 2005-10-21
Greetings

I'm using Breezy on a number of computers which are behind a proxy. I have kde correctly configured for this proxy but I can't get Adept to work properly. 

It also doesn't have any configuration so how do I tell it to use a proxy?

Thanks

---

### Post by chocobanana on 2005-10-24
Hey!

I need help with this one!

Thanks

---

### Post by niclasc on 2005-10-31
Hi

I have the same problem. Adept dosen't seem to work behind a proxy.

Does anyone know how to get it working??

/Niclas

---

### Post by supenguin on 2005-12-13
Anyone figure this out? konqueror works fine, but adept can't download anything. synaptic and apt-get work fine though once I set them up to work with the proxy.

---

### Post by supenguin on 2005-12-20
Here I go replying to myself again. I got it figured out.  It is a known bug in adept, or more like a missing feature.  Adept uses the proxy settings from the command line environment variables instead of the KDE network settings.

Here's the bug report: [http://bugs.kde.org/show_bug.cgi?id=117185](http://bugs.kde.org/show_bug.cgi?id=117185)

And directions on how to get apt-get and adept working with a proxy that requires authentication:

[http://ubuntuforums.org/showthread.php?p=364026#post364026](http://ubuntuforums.org/showthread.php?p=364026#post364026)

---

### Post by clover on 2006-02-01
Have a look on my article at 
[http://shabdar.ws/content/view/23/1/]("http://shabdar.ws/content/view/23/1/")

I hope it can help you if you still have the problem ;)

---

