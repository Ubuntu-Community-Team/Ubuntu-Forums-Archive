---
title: "Is it normal to have multiple versions of libQtCore4?"
date: 2014-01-27
forum: General Help
---

### Post by publicface on 2014-01-27
Is this normal?  If not.... how did it happen and how can I fix it?  Thank you in advance.

ubuntu 12.04.4

[COLOR=#000000][FONT=Ubuntu]apt-cache policy libqtcore4[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]libqtcore4:[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]  Installed: 4:4.8.2+dfsg-2ubuntu1~precise1~ppa6[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]  Candidate: 4:4.8.2+dfsg-2ubuntu1~precise1~ppa6[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]  Version table:[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu] *** 4:4.8.2+dfsg-2ubuntu1~precise1~ppa6 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]        500 [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/) precise/main i386 Packages[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]        100 /var/lib/dpkg/status[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]     4:4.8.1-0ubuntu4.6 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]     4:4.8.1-0ubuntu4.5 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main i386 Packages[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]     4:4.8.1-0ubuntu4 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main i386 Packages[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]
[/FONT][/COLOR]

---

### Post by Lars Noodén on 2014-01-27
You have version 4:4.8.2+dfsg-2ubuntu1~precise1~ppa6 installed.  The others listed are what are still in the repository.  If you really wanted to, you could [pin](https://help.ubuntu.com/community/PinningHowto) a specific version, even if it is older.

---

