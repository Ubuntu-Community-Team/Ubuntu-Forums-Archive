---
title: "How to downgrade Thunderbird to 24.6.0-0ubuntu1"
date: 2014-07-23
forum: General Help
---

### Post by temmokan on 2014-07-23
Latest "stable" upgrade of Thunderbird to 31.0 is severely broken (see bug [1036338]("https://bugzilla.mozilla.org/show_bug.cgi?id=1036338")). It renders all mail servers using self-signed certificates, or using self-created root CAs unreachable.

In my case it's a blocker. But I can't also see simple and obvious way to downgrade Thunderbird to its previous stable version, 24.6.0-0ubuntu1. Is it possible to find that .deb file and re-install it?

My advice to those who haven't yet upgraded their Thunderbird - do not, until correction is published.

Thank you in advance.

---

### Post by kc1di on 2014-07-23
you can find [it here.]("http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/t/thunderbird-mozilla-build/")

---

### Post by temmokan on 2014-07-23
@kc1di, thank you very much!

---

### Post by kc1di on 2014-07-24
Your Welcome enjoy :)

---

### Post by pgf on 2014-08-01
i'm helping a friend with this same downgrade:  in the interests of causing minimal collateral damage to their system, is there a way to use apt-get install thunderbird=<version> to do this downgrade?  or must we use dpkg?  (and if dpkg -- how safe is that?  i really don't want this to turn into a morass of twisty little dependencies.)

my first tries of "apt-get install thunderbird=24.6.0" and "apt-get install thunderbird=24.6.0-0ubuntu1" result in "Version '24.6.0' for 'thunderbird' was not found".

many thanks for your advice.

---

### Post by ezekiel_quacks on 2014-08-05
Someone else already suggested Ubuntuzilla packages, but if you want the Ubuntu-flavored packages for Thunderbird 24.6.0, as I did, then maybe the half hour I just spent tracking them down can help you too!   You can download the packages from [here](https://launchpad.net/ubuntu/+source/thunderbird/1:24.6.0+build1-0ubuntu0.14.04.1). The specific page for i386 builds is [here](https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa/+build/6083154), and the specific page for amd64 builds is [here](https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa/+build/6083151).  You'll need to use dpkg (not apt-get) to install these, and then you'll want to pin these (or use Package -> Force Version in Synaptic) to keep them from being upgraded to 31.0.

---

### Post by ray field on 2014-08-07
I am a little bit confused:

My experience with Thunderbird 31 was disastrous, so I tried to downgrade. The version I now have (after quite a few failed attempts) is 24.6.0 -- however according to Synaptic, it's not Thunderbird, but thunderbird-mozilla-build. Which works fine, I guess, except it lacks Unity (Gnome?) integration -- which I really miss, particularly the blue envelope indicator on the Unity panel.

I have tried to remove this version and install one of the versions on the page ezekiel_quacks pointed to, however, I am at a loss to know which files I should install in which order.

---

