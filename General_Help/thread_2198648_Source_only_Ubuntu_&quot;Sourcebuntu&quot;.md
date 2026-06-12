---
title: "Source only Ubuntu &quot;Sourcebuntu&quot;"
date: 2014-01-09
forum: General Help
---

### Post by Tristan_Williams on 2014-01-09
I am in love with Gentoo, but I seriously cannot install it. No matter how hard I try, something goes wrong every single time which renders it unuseable.
So I decdided to take on a project which I know I can achive more easily.

Here is my question:

How can I set it up to where apt does not install any pre-built binaries, and only compile from the source repositories?
I realize that some packages are not available as source packages, so there would have to be a way to install the normal way too.

Here is my idea so far:

- Use apt-build for EVERYTHING

- Make it so that apt-build installs dependencies from source (it currently installs the specified program from source, and installs dependencies the normal way)

- MAYBE make a system like Gentoos "USE" flags


I would also like to note that I am building this "Sourcebuntu" from the minimal install, available here: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by jones quest on 2014-01-10
As you already know you can install only source packages in any Linux distro. Just remove all binary repos and only use the source repos. The USE-flags are however unique to Gentoo.

Have you tried Sabayon Linux? It's a Gentoo derivate, but much easier to set up.

You could also try the following guide and turn Ubuntu to gentoo:
[http://m.wikihow.com/Install-Gentoo-Linux-from-Ubuntu](http://m.wikihow.com/Install-Gentoo-Linux-from-Ubuntu)

---

