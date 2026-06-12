---
title: "upgrade impossible from Ubuntu 12.10-13.04"
date: 2013-10-25
forum: General Help
---

### Post by dixfranke on 2013-10-25
Hello all,

I am running Ubuntu on a netbook. My uname -a looks like this:

Linux blackasice 3.5.0-25-generic #38-Ubuntu SMP Mon Feb 18 23:28:26 UTC 2013 i686 i686 i686 GNU/Linux

I have a problem, namely that I am not able to update my version of Ubuntu, nor any of my software through the Update Manager or Ubuntu Software Center.

[B]When I follow the automatic update prompt for 13.04, I get the following "internal error" message
[/B]
ExecutablePath
  /usr/share/apport/apportcheckresume
Package
  linux-image-3.5.0-25-generic
ProblemType
  Kerneloops
Annotation
  This occurred during a previous suspend and prevented it from resuming properly. The resume processing hung very near the end and will have appeared to have completed normally.
Architecture
  i386
DistroRelease
  Ubuntu 12.10
Failure
  late resume
InterpreterPath
  /usr/bin/python3.2mu
MarkForUpload
  True
ProcCmdline
  /usr/bin/python3 /usr/share/apport/apportcheckresume
ProcEnviron
  TERM=linux
  PATH=(custom, no user)
Tags
  resume suspend resume-late-hang
Uname
  Linux 3.5.0-25-generic i686
UnreportableReason
  E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_quantal_partner_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.


[B]As well, when I try sudo apt-get update, I get the following error message in the terminal:
[/B]

Reading package lists... Error!
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) quantal Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) quantal Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/Release](http://extras.ubuntu.com/ubuntu/dists/quantal/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_quantal_partner_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.



Thank you very much for your help, suggestions, and/or references to other threads.

Dix Franke

---

### Post by Tom_Conklin on 2013-10-25
What version are you running currently?

---

### Post by dixfranke on 2013-10-25
12.10

---

### Post by Tom_Conklin on 2013-10-25
Sorry, You have to upgrade one version at a time, you can't go from 12.10 to 13.04. It would be easier and quicker to do a fresh install  of 13.04

---

### Post by westie457 on 2013-10-25
> **Tom_Conklin said:**
> Sorry, You have to upgrade one version at a time, you can't go from 12.10 to 13.04. It would be easier and quicker to do a fresh install  of 13.04
12.10 to 13.04 is a one step upgrade.

@[[COLOR=#000000]dixfranke[/COLOR]]("http://ubuntuforums.org/member.php?u=1320299")

Take a look at this, it should help you. [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

---

### Post by Tom_Conklin on 2013-10-25
Oops, my bad.

---

### Post by dixfranke on 2013-10-25
it worked: thanks!

---

