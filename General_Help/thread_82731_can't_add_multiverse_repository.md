---
title: "can't add multiverse repository"
date: 2005-10-27
forum: General Help
---

### Post by jleemans on 2005-10-27
Hi, 

I just installed Breezy Badger a few days ago (I'm new to Ubuntu).  Since yesterday I've been trying to add the breezy multiverse repository.  I've got the following lines in my sources.list:

[FONT="Courier New"]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse[/FONT]

When I start Synaptic, it gives me the following warning:
[FONT="Courier New"]W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)[/FONT]

Without the "multiverse" appended to the two lines mentioned above, everything works fine. I read the sources.list man page and looked in my browser under [http://us.archive.ubuntu.com/ubuntu/dists/breezy](http://us.archive.ubuntu.com/ubuntu/dists/breezy), I see that multiverse is really there, and I honestly don't see too much difference in layout with universe.  What I'm I missing here ? :confused: 

Thanks for the help !
Cheers,
Joeri

---

### Post by jleemans on 2005-10-27
Solved.  Did an apt-get update first.  I'm starting to see how this apt stuff works :smile:

---

### Post by jvictor on 2005-10-27
For me i'd to disable ipv6 , other than that id to do an nslookup every time

---

