---
title: "Having your own repository."
date: 2004-11-19
forum: General Help
---

### Post by kelvinty on 2004-11-19
Hi everyone,

  I'm thinking about having setting up an Ubuntu repository right in my company's network. I'm a businessman and have a very small company but I would like to start installing Ubuntu on all (14) computers at work.

Basically ->

1) repository will be hosted on network server (customized Gentoo/Samba)
2) repository will be refreshing it's package contents with Ubuntu's servers every three days.
3) Ability to add custom packages.

Could anyone point out the way for it to work? I've finally found a distro that my office girls can use, and I have enough of troubleshooting Windows for them.

I would appreciate it lots if anyone could help me on this, mucho gracias!

---

### Post by darrell on 2004-11-19
This might help:

[Debian  Repository Howto](http://www.debian.org/doc/manuals/repository-howto/repository-howto.html) 

Darrell

---

### Post by Juergen on 2004-11-19
[QUOTE=darrell]This might help:

[Debian  Repository Howto](http://www.debian.org/doc/manuals/repository-howto/repository-howto.html) 

Darrell[/QUOTE]
At least apt-move isn't adapted to the different repository-structure ubuntu has and creates only Packages.gz for main.

Since it's a fairly large script, I haven't been in the mood to try to make it fully work so far, so I'm doing this ATM: 

Let apt-move create the pool of packages and create the Packages.gz manually for all packages. Then I move it to dists/warty/main/binary-386 and modify the checksums in dists/warty/Release.

I lose the info if a package is from universe or whereever, but otherwise it works.

I suppose the other apt-tools will have similar problems...

---

