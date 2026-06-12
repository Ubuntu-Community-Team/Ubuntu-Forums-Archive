---
title: "http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz cannot be found"
date: 2006-10-29
forum: General Help
---

### Post by wootton on 2006-10-29
Hello,

I'm trying to install Easy Ubuntu on Dapper.  Using Google I found this page:

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_use_Easy_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_use_Easy_Ubuntu)

However the url 
[FONT="Courier New"]
[http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz)[/FONT]

used in the command

[FONT="Courier New"]wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz)[/FONT]

Cannot be resolved.

1) Why is this?
2) HOw do I install Easy Ubuntu if the URL cannot be resolved?

Many thanks

Jack

---

### Post by Oki on 2006-10-29
Hi, I have tried to use EasyUbuntu myself for the last two days, but it looks like the site is down(dont know why). I have used [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/) before.

But you could insted use Automatix2; you will get what you look for. 
[http://www.getautomatix.com/](http://www.getautomatix.com/) I belive Automatix2 has the same or more the nEasyUbuntu did.

---

### Post by wootton on 2006-10-29
Oki, thank you for your reply.

However after executing this command:

[FONT="Courier New"]sudo apt-get update[/FONT]

I encountered this error:

[FONT="Courier New"]Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg)  Temporary failure resolving ‘antesis.freecontrib.org’[/FONT]

I decided to continue anyway, and then had this problem:

[FONT="Courier New"]E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it.[/FONT]

In fact this last error is why I wanted to install Easy Ubuntu, to try and sort out an update problem I have, whether by command line or gui I receive the previously mentioned 'flashplugin-nonfree' error.

Thanks

Jack

---

### Post by gvgerman on 2006-10-29
from a search of forum messages, many are having issues w/ freecontrib.org

some messages state there has been a DDoS attack and the servers are down

some messages speak of the easyubuntu developers leaving

until freecontrib is back up, other forum messages are saying automatix is the easiest alternative

---

### Post by wootton on 2006-10-29
I try this.  But I get the following error when I run [FONT="Courier New"][COLOR="Gray"]sudo apt-get update[/COLOR][/FONT]


[FONT="Courier New"][COLOR="Gray"]
Errhttp://antesis.freecontrib.org breezy Release.gpg
Temporary failure resolving ‘antesis.freecontrib.org’
Fetched 382B in 2m5s (3B/s)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg)  Temporary failure resolving ‘antesis.freecontrib.org’
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
[/COLOR][/FONT]

---

### Post by ianmacgregor on 2006-10-29
The freecontrib repo is part of PLF (Penguin Liberation Front) and they are closing. See: [http://plf.zarb.org/](http://plf.zarb.org/)

Might as well comment it out in your sources.list.

---

