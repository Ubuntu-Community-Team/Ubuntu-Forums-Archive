---
title: "Server vs Desktop for NAS + Plex Media Server"
date: 2013-02-15
forum: General Help
---

### Post by manu081 on 2013-02-15
I have an old HP notebook that I am going to make into a NAS. It is a HP Pavilion dv6000 from 2007.

Specs are 1.7GHz AMD Athlon 64 X2 Dual Core processor, 2.5GB DDR2 RAM and an nVidia GeForce Go 6150 graphics chip. Yes these specs are quite dated. It will be connected to the network via its 10/100 Ethernet adapter.

Currently I've got my 2TB external hard drive connected to the Linksys WRT610n wireless router but I've given up using its built in NAS capability as it's atrocious and thus want to make this notebook into a NAS.

This laptop will share the external hard drive to all users on the network + run a version of Plex Media Server. That's it, it will not be used for anything else.

I know the processor isn't good enough to transcode most HD content on the fly but I'm trying to maximize what I can get out of this machine for the next 6-9 months at which point I will probably invest into a more powerful machine.

So, getting back to the question on hand: should I go with Ubuntu Desktop version or Ubuntu Server edition?

Thanks, really appreciate the input.

---

### Post by Thee on 2013-02-15
I'm not sure does Plex require somekind of mySQL database or something else that requires you to have a server edition of Ubuntu, but if it doesnt, then IMO, it's only important that the desktop is as lite as possible, so your CPU can handle the HD content better, so Server or not - shouldn't really matter as long as it's lite.

---

### Post by manu08 on 2013-02-15
I think Plex creates a database based on what movies & TV shows it finds on the specified location. This is done automatically by the software as it pulls data (such as album art, director, cast etc) directly from places like themoviedb.org and thetvdb.com. I'm not sure about a need for mySQL.

Between a fresh install of Ubuntu desktop & Ubuntu server, which is less resource intensive? This way the CPU will spend less resources running the OS and have more available for transcoding whenever possible.

---

### Post by Thee on 2013-02-15
That I do not know, maybe someone else can say, but I do know that if you want speed, go with Lubuntu or Xubuntu.

---

