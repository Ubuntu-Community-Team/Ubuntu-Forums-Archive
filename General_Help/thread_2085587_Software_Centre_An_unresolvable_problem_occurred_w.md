---
title: "Software Centre An unresolvable problem occurred while initializing the package infor"
date: 2012-11-18
forum: General Help
---

### Post by CWZ on 2012-11-18
Ok i just installed Ubuntu 12.04 When i open " Software up to Date " and when I open " Ubuntu Software Center " I was getting a msg like ths

[LIST]
[*]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
[/LIST]
But then i restarted and now software center just closes with nothing said but " Software up to Date " still gives a msg  (the one above) I AM A ROOKIE IN THE UBUNTU /LINUX WOURLD >>>USE SMALL WORDS KEEP INSTRUCTIONS EASY AND FEEL FREE TO GIBBS SLAP ME](*,)

---

### Post by nothingspecial on 2012-11-18
Title changed to reflect the problem.

---

### Post by CWZ on 2012-11-18
Oh and i told ubuntu to report the problem it says 
     SORRY, THE APPLICATION UPDATE-APT-XAPIAN-INDEX HAS CLOSED UNEXPECTEDLY THE DETAILS BUTton says /usr/sbin/UPDATE-APT-XAPIAN-INDEX
 when i say send to that msg it says cant identifiy package

---

### Post by ibjsb4 on 2012-11-18
for the first problem in post #1:

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo rm /var/lib/apt/lists/* -vf

and follow with

sudo apt-get update

---

### Post by CWZ on 2012-11-18
1st Thx for the help ok heres what happend

[LIST]
[*]cw@cw:~$ sudo rm/var/lib/apt/lists/*-vf
[sudo] password for cw: 
sudo: rm/var/lib/apt/lists/*-vf: command not found
cw@cw:~$ sudo rm/var/lib/apt/lists/*-vf
sudo: rm/var/lib/apt/lists/*-vf: command not found
cw@cw:~$  rm/var/lib/apt/lists/*-vf
bash: rm/var/lib/apt/lists/*-vf: No such file or directory
cw@cw:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
cw@cw:~$
[/LIST]

---

### Post by ibjsb4 on 2012-11-18
> **CWZ said:**
> 1st Thx for the help ok heres what happend

[LIST]
[*]cw@cw:~$ sudo rm/var/lib/apt/lists/*-vf
[sudo] password for cw: 
sudo: rm/var/lib/apt/lists/*-vf: command not found
cw@cw:~$ sudo rm/var/lib/apt/lists/*-vf
sudo: rm/var/lib/apt/lists/*-vf: command not found
cw@cw:~$  rm/var/lib/apt/lists/*-vf
bash: rm/var/lib/apt/lists/*-vf: No such file or directory
cw@cw:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
cw@cw:~$
[/LIST]


Copy and paste that command, there are spaces missing in yours.

sudo rm /var/lib/apt/lists/* -vf

---

### Post by CWZ on 2012-11-18
Thx\\:D/
ok it worked ... but i got this at the end of the update

[LIST]
[*]Get:93 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en [11.9 kB]                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                                                             
  404  Not Found [IP: 91.189.91.15 80]
Fetched 21.5 MB in 18s (1,194 kB/s)                                                                                   
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
[/LIST]
 ???

---

### Post by ibjsb4 on 2012-11-18
Again in terminal:

cat -n /etc/apt/sources.list

And please post

---

### Post by CWZ on 2012-11-20
Ok these are the results pls bare with me here i am a very mobile professional and find little time for my self .....

[LIST]
[*]cw@cw:~$ cat -n /etc/apt/sources.list
[*]     1	# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/
[*]     2
[*]     3	# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
[*]     4	# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted
[*]     5
[*]     6	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
[*]     7	# newer versions of the distribution.
[*]     8	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
[*]     9	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
[*]    10
[*]    11	## Major bug fix updates produced after the final release of the
[*]    12	## distribution.
[*]    13	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
[*]    14	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
[*]    15
[*]    16	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
[*]    17	## team. Also, please note that software in universe WILL NOT receive any
[*]    18	## review or updates from the Ubuntu security team.
[*]    19	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
[*]    20	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
[*]    21	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
[*]    22	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
[*]    23
[*]    24	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
[*]    25	## team, and may not be under a free licence. Please satisfy yourself as to
[*]    26	## your rights to use the software. Also, please note that software in
[*]    27	## multiverse WILL NOT receive any review or updates from the Ubuntu
[*]    28	## security team.
[*]    29	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
[*]    30	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
[*]    31	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
[*]    32	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
[*]    33
[*]    34	## N.B. software from this repository may not have been tested as
[*]    35	## extensively as that contained in the main release, although it includes
[*]    36	## newer versions of some applications which may provide useful features.
[*]    37	## Also, please note that software in backports WILL NOT receive any review
[*]    38	## or updates from the Ubuntu security team.
[*]    39	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
[*]    40	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
[*]    41
[*]    42	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
[*]    43	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
[*]    44	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
[*]    45	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
[*]    46	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
[*]    47	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
[*]    48
[*]    49	## Uncomment the following two lines to add software from Canonical's
[*]    50	## 'partner' repository.
[*]    51	## This software is not part of Ubuntu, but is offered by Canonical and the
[*]    52	## respective vendors as a service to Ubuntu users.
[*]    53	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
[*]    54	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
[*]    55
[*]    56	## This software is not part of Ubuntu, but is offered by third-party
[*]    57	## developers who want to ship their latest software.
[*]    58	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
[*]    59	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
[/LIST]

---

### Post by ibjsb4 on 2012-11-20
Uncheck the "Source Code" box (in software sources) and that should fix your problem.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by CWZ on 2012-11-23
OK got it it workd no err's so thx thx thx:guitar:

---

### Post by ibjsb4 on 2012-11-23
welcome, welcome, welcome  :)

---

### Post by J3 Remy on 2013-10-10
I am trying to upgrade to 12.04.3 LTS, from 11.10, and I am having the same issue.  Below find the error that I get.

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en  Encountered a section with no Package: header
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I executed "sudo rm /var/lib/apt/lists/ *vf", ran the apt-get update, and unchecked the "Source Code" box in the Software Sources menu.

---

### Post by Bashing-om on 2013-10-10
J3 Remy; Hi !

You are trying to update a version that no longer has support. The repositories are no longer in existence.
To upgrade follow this tutorial:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Best of luck and applied efforts !

[INDENT][INDENT]this will help, cheers
[/INDENT][/INDENT]

---

