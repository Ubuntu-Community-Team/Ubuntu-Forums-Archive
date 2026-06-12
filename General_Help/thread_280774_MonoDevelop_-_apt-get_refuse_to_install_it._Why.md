---
title: "MonoDevelop - apt-get refuse to install it. Why?"
date: 2006-10-20
forum: General Help
---

### Post by JaRoLLz on 2006-10-20
Dear all,

I've been trying to install monodevelop by using apt-get:
[FONT="Lucida Console"]
sudo apt-get install mono mono-gmcs mono-gac mono-utils monodevelop[/FONT]

but then i got an error message like this:
[FONT="Lucida Console"]
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mono: Depends: mono-common (= 1.1.13.6-0ubuntu3) but 1.1.13.6-0ubuntu3.1 is to be installed
        Depends: mono-jit (= 1.1.13.6-0ubuntu3) but 1.1.13.6-0ubuntu3.1 is to be installed
E: Broken packages[/FONT]

How can i do something about this? What should i do to make the install work? What's the meaning of this?

---

