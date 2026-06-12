---
title: "New installs not detecting dependencies during CONFIGURE"
date: 2005-04-04
forum: General Help
---

### Post by oberones on 2005-04-04
I'm running into an odd situation when trying to install programs from scratch; it's not detecting the dependencies even though I know they're there. For example:

I wanted to install gFTP so I downloaded the source and ran "./configure". It failed saying that GTK+ needed to be installed first. I checked in Synaptic and was able to locate GTK+, but decided to give it the benefit of the doubt and install GTK+ from source. When I tried to do this, GTK failed during "./configure" saying it needed Pengo, ATK, and Glib, all of which I was able to find in Synaptic. I then tried to install Pengo, ATK, and Glib from source, and they all complained about their own missing dependencies during "./configure" Is there some environment variable I need to be updating? Does Ubuntu install these apps in weird locates that I need to point to during "./configure"? If anyone can help me with this, I would really appreciate it. Thanks in advance!

---

