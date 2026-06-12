---
title: "How to install Rsyslog on Ubuntu Gusty ?"
date: 2008-02-13
forum: General Help
---

### Post by xnd on 2008-02-13
Hello!

Is there a way to replace the current system logging daemon (sysklogd) with Rsyslog ? I've noticed there are .deb packages but only for Ubuntu Hardy. 

How to deinstall sysklogd and install Rsyslog and of course, configure it and stuff? On Ubuntu 7.10?

Thanks!

---

### Post by xarquid on 2008-02-13
Greetings xnd,

Great choice for system logging. Yep, it will be available in Hardy. One way is to temporarily add the hardy repository to your /etc/apt/sources.list and run apt-get update and then apt-get install rsyslog

And this will install it and configure it. Then remove it from the /etc/apt/sources.list thereafter (hardy that is, and replace 'hardy' with 'feisty' again). Even though this is not highly recommended so I leave you with this excellent guide. This will take you a bit longer HOWEVER in the end it pays off!

Please use this guide from How to Forge (I did, and believe me...it's excellent and works like a charm afterwards). If you run into any issues, just let me or anyone in this thread know:

[http://www.howtoforge.com/logging_with_rsyslog_phplogcon_debian_etch](http://www.howtoforge.com/logging_with_rsyslog_phplogcon_debian_etch)

And it even offers you phpLogcon for an added utility benefit (which I have come to love)...so give it a whirl.

Sincerely,

Craig Huffstetler / xarquid / xq

---

### Post by xnd on 2008-02-13
A little OOPSIE:

sources.list:

```
deb http://ftp.lug.ro/ubuntu/ gutsy-security main restricted
deb-src http://ftp.lug.ro/ubuntu/ gutsy-security restricted main multiverse universe
deb http://ftp.lug.ro/ubuntu/ gutsy-security universe
deb http://ftp.lug.ro/ubuntu/ gutsy-security multiverse
deb http://ftp.lug.ro/ubuntu/ gutsy main universe restricted multiverse
deb-src http://ftp.lug.ro/ubuntu/ gutsy universe main multiverse restricted

deb http://ftp.lug.ro/ubuntu/ hardy-security main restricted
deb-src http://ftp.lug.ro/ubuntu/ hardy-security restricted main multiverse universe
deb http://ftp.lug.ro/ubuntu/ hardy-security universe
deb http://ftp.lug.ro/ubuntu/ hardy-security multiverse
deb http://ftp.lug.ro/ubuntu/ hardy main universe restricted multiverse
deb-src http://ftp.lug.ro/ubuntu/ hardy universe main multiverse restricted

```

apt-get update ..... [NO ERRORS]

apt-get install rsyslog :

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  rsyslog: Conflicts: system-log-daemon
E: Broken packages

```

Anything I could do?

---

### Post by xarquid on 2008-02-13
Just remove the hardy lines from the sources list and follow the guide linked. It will save you some time and...crazy conflicts.

The apt-get install didn't cause any problems because there was a file conflict before it ever took place.

Sorry about that. Follow the rsyslog install guide that I linked and then you can use:

apt-get remove sysklogd
And whatever else that it is replacing -- and while so screenshot it to eventually hang on your wall as a trophy! ;-)

Sincerely,

xq

---

