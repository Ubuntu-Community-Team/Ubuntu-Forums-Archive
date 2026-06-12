---
title: "Upgrade Ubuntu Without Gnome Updating..."
date: 2014-03-27
forum: General Help
---

### Post by Sparrow40k1 on 2014-03-27
So, I have been a Windows user my whole life but have always switched to and from Ubuntu or other distros as I have always been interested but either something has gone wrong or software I need isn't available for the platform and wine proves to challenging at times..
I was working on what I found to be the best (in my opinion) environment for Windows users to switch to Linux, but after a Ubuntu upgrade the entire this was gone due to incompatibly issues.
I was running Ubuntu 12.04 and I don't know what version of Gnome - I always just type "sudo apt-get install gnome-shell" every time I go onto a Linux machine.
I want to have the latest version of Ubuntu, like 13.04 and onward, but I don't want Gnome to update and wreck it all.
In a perfect world, it would be awesome if Gnome only updated if all extensions were compatible, but that sounds like an extreme challenge for me to bother looking into.

So, sometime within this week I am going to install Ubuntu 12.04 again and try to recreate my environment. But any help on how to stay up to date and not break anything would be awesome!!

Thank you.

---

### Post by Sparrow40k1 on 2014-03-28
So, naturally as I do have 12.04 installed. There are updated and of course a later version of Ubuntu avaliable..
Any ideas on how I can update without anything happening to Gnome?

---

### Post by Navneet_Kumar on 2014-03-28
U can upgrade using the 'Software Updater' and gnome will be upgraded as well to the latest supported version...and i assure that it will be pleasant to watch........

---

### Post by Sparrow40k1 on 2014-03-29
I just updated threw the Update Manager and everything is fine. Now I just need to find a way to update to Ubuntu 13.10.

---

### Post by buzzingrobot on 2014-03-29
You might consider instaling Ubuntu Gnome.

---

### Post by oldos2er on 2014-03-29
> **Sparrow40k1 said:**
> I just updated threw the Update Manager and everything is fine. Now I just need to find a way to update to Ubuntu 13.10.

Why not do a clean install of 13.10? Or you could wait until April 17 and update directly to 14.04 (LTS).

---

### Post by Sparrow40k1 on 2014-03-30
Because the extension I have in Gnome won't work. I had 13.10 but only 2 extensions that I use worked..

---

### Post by buzzingrobot on 2014-03-30
> **Sparrow40k1 said:**
> Because the extension I have in Gnome won't work. I had 13.10 but only 2 extensions that I use worked..

Because extensions are are typically created by users and indy developers, they very often aren't update in synch with a new Gnome release. Neither are they updated when Gnome updates.  Sometimes, returning to extensions.gnome.org to reinstall an extension that has stopped working after a Gnome upgrade will do the trick.

Occasionally, manually updating the Gnome version in an extension's metadata.json file will also convince it to work if it is otherwise compatible.

---

