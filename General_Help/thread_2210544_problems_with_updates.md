---
title: "problems with updates"
date: 2014-03-11
forum: General Help
---

### Post by christon74 on 2014-03-11
Good evening every Ubunter:)

Just like with Windows, some crazy things can happen with Ubuntu. You try to keep your Pc up to date, you know that your network is enabled and that you have a connection but you are asked to check your connection! :confused:   ](*,) (update manager)

Or the updates will simply not download (update manager) and so you resort to the terminal and type this:
  	 	 	 	   sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude full-upgrade

And yet you get this strange messages:

Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Translation-en
  Unable to connect to antesis.freecontrib.org:http:
91% [Working]W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (110: Connection timed out)

W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources)  Unable to connect to antesis.freecontrib.org:http:

W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources)  Unable to connect to antesis.freecontrib.org:http:

W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages)  Unable to connect to antesis.freecontrib.org:http:

W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages)  Unable to connect to antesis.freecontrib.org:http:

W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-en_GB](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-en_GB)  Unable to connect to antesis.freecontrib.org:http:

W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-en](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-en)  Unable to connect to antesis.freecontrib.org:http:

W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en_GB](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en_GB)  Unable to connect to antesis.freecontrib.org:http:

W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en)  Unable to connect to antesis.freecontrib.org:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.


Has this ever happened to anybody else out there? hum?

---

### Post by deadflowr on 2014-03-11
It is no surprise that any repos for breezy would be down.

What version of Ubuntu are you actually running?

In the meantime, best to disable those repos.
open software sources, and go to "other software", and then uncheck the entries for that repo listed.

---

### Post by raja.genupula on 2014-03-11
unable to connect ....either server issue or completely that links not available.

try to change your server and try again.

---

### Post by christon74 on 2014-03-11
Hello deadflower and raja :D
The version I am running is Ubuntu 12.04 LTS and this very moment I am listening to BBC radio Scotland on the web [ I am connected]
Ah yes, something which is far from obvious: I live in France _ Thonon-Les-Bains_ Haute-Savoie.

---

### Post by ian-weisser on 2014-03-11
> **christon74 said:**
> Just like with Windows, some crazy things can happen with Ubuntu. You try to keep your Pc up to date, you know that your network is enabled and that you have a connection but you are asked to check your connection!

That server does not respond.
You are trying to connect to a server that is not responding.
It's not Ubuntu's problem, nor Windows'.

---

### Post by christon74 on 2014-03-12
Aha;) Thank you Ian. So it is the server which is at fault.....
Anyway when I click on start it reads 'software up to date'

---

### Post by 3rdalbum on 2014-03-12
> **christon74 said:**
> Aha;) Thank you Ian. So it is the server which is at fault.....
Anyway when I click on start it reads 'software up to date'

Yes. The Ubuntu servers are fine, no problems there. It sounds like you have added an extra repository that is no longer present. The repository appears to be for Ubuntu 5.10 which was released in 2005 and End Of Life as of 2007, so no wonder it is not working. It doesn't affect the rest of your system though as you have found out.

---

