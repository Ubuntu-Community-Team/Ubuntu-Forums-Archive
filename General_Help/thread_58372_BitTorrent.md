---
title: "BitTorrent"
date: 2005-08-19
forum: General Help
---

### Post by Saponification on 2005-08-19
I'm fairly new to *Linux*, so this may be a rather silly question. How do I find out what ports *GNOME BitTorrent* is using? I'm aware bit torrent by default users 6881-6889,but I've seen other applications that start off using different ports. Also, how can I change the ports the program is using?

Secondly, I downloaded *BitTornado* but it's only the source. How can I compile it?

---

### Post by darksbane on 2005-08-20
I'm fairly new to linux as well, I've been tinkering in it for a few years but never really seriously got into it but I'm hoping to now.

Assuming what you downloaded is in a tar file go to the command line and put in:

**tar -xzvf <filename>** this unpacks the file
**ls** see what new directory was created
**cd <new directory>** go to the new directory
**./configure**
**make **
**make install**

I think that should work....If I'm wrong could someone please correct me :)

---

### Post by gorkhal on 2005-08-20
[QUOTE=Saponification]I'm fairly new to *Linux*, so this may be a rather silly question. How do I find out what ports *GNOME BitTorrent* is using? I'm aware bit torrent by default users 6881-6889,but I've seen other applications that start off using different ports. Also, how can I change the ports the program is using?

Secondly, I downloaded *BitTornado* but it's only the source. How can I compile it?[/QUOTE]

You really dont need to compile BitTornado from source. Just get BitTornado and BitTornado-gui from Synaptic. Make sure you have universe in your synaptic repository. If not check [HERE](http://ubuntuguide.org/#extrarepositories).

Once you have bittornado installed, its a snap to change the ports, just goto Prefs and fiddle with the port range.

---

