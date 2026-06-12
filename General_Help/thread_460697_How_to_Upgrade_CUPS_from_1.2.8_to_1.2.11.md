---
title: "How to Upgrade CUPS from 1.2.8 to 1.2.11?"
date: 2007-05-31
forum: General Help
---

### Post by SendDerek on 2007-05-31
Hello All!

I would like to upgrade CUPS to the latest version of 1.2.11 from the version that comes with Fiesty 1.2.8.  I was hoping on finding a guide somewhere but I'm coming up short.

Is there anybody out there willing to help me give the upgrade a go?

Thanks for the help in advance!

-Derek

---

### Post by phidia on 2007-05-31
I don't know if it's safe or what it would do to your system but you could get the deb package from [http://packages.debian.org/cgi-bin/search_packages.pl?keywords=cups&searchon=names&subword=1&version=unstable&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=cups&searchon=names&subword=1&version=unstable&release=all)
and use sudo dpkg -i (check the man page for dpkg if you need to) to install it.

Another idea might be to change your repos to the release that's in development (gutsy gibbon) and just upgrade that package. _But_ the package manager will probably want to upgrade other packages as well-so you could end up with a broken system.

---

