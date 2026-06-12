---
title: "gftp unmet dependencies"
date: 2005-10-17
forum: General Help
---

### Post by cytoplasm on 2005-10-17
Trying to install gftp:

[FONT="Courier New"]sprotsman@phobos:~$ sudo apt-get install gftp Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gftp: Depends: gftp-gtk (= 2.0.18-6) but it is not going to be installed
        Depends: gftp-text (= 2.0.18-6) but it is not going to be installed
E: Broken packages[/FONT]

Also tried the following:

[FONT="Courier New"]sprotsman@phobos:~$ sudo apt-get install gftp gftp-gtk gftp-text gftp-common
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gftp: Depends: gftp-gtk (= 2.0.18-6) but 2.0.18-10 is to be installed
  gftp-text: Depends: gftp-common (= 2.0.18-6) but 2.0.18-10 is to be installed
E: Broken packages[/FONT]

---

### Post by bluck on 2005-10-17
problem persist after a `sudo apt-get update` ?

---

### Post by cytoplasm on 2005-10-17
Yes.  Actually there seems to be a problem with running `apt-get update` right now.  It results in a `GPG Error ... BADSIG`.  Check out some of the recent posts.  It has come up in at least three threads that I've seen thus far in the last hour.

---

### Post by bluck on 2005-10-17
[QUOTE=cytoplasm]Yes.  Actually there seems to be a problem with running `apt-get update` right now.  It results in a `GPG Error ... BADSIG`.  Check out some of the recent posts.  It has come up in at least three threads that I've seen thus far in the last hour.[/QUOTE]

hmm, maybe a prob with certain repositories, as i have no problems running `apt-get update`

---

### Post by cytoplasm on 2005-10-17
I noticed (when using synaptic) there there are two different versions (one for gftp and another for gftp-common.  This time I just attempted the following:

[FONT="Courier New"]sprotsman@phobos:~$ sudo apt-get install gftp-common
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gftp-gtk
The following NEW packages will be installed:
  gftp-common gftp-gtk
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 347kB of archives.
After unpacking 3424kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  gftp-gtk gftp-common
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main gftp-gtk 2.0.18-10
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main gftp-common 2.0.18-10
  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gftp/gftp-gtk_2.0.18-10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gftp/gftp-gtk_2.0.18-10_i386.deb)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gftp/gftp-common_2.0.18-10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gftp/gftp-common_2.0.18-10_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/FONT]

I then tried again the the `--fix-missing` but this didn't resolve the problem.

---

### Post by cytoplasm on 2005-10-17
There must be a problem with the US mirrors.  I removed the "us" references to the URLs within the source.list file and then ran the update and then `sudo apt-get install gftp-common`.  This worked and all is well.

---

### Post by bluck on 2005-10-17
[QUOTE=cytoplasm]I noticed (when using synaptic) there there are two different versions (one for gftp and another for gftp-common.  This time I just attempted the following:

[FONT="Courier New"]sprotsman@phobos:~$ sudo apt-get install gftp-common
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gftp-gtk
The following NEW packages will be installed:
  gftp-common gftp-gtk
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 347kB of archives.
After unpacking 3424kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  gftp-gtk gftp-common
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main gftp-gtk 2.0.18-10
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main gftp-common 2.0.18-10
  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gftp/gftp-gtk_2.0.18-10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gftp/gftp-gtk_2.0.18-10_i386.deb)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gftp/gftp-common_2.0.18-10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gftp/gftp-common_2.0.18-10_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/FONT]

I then tried again the the `--fix-missing` but this didn't resolve the problem.[/QUOTE]


hmm,  im using the ca.archive.ubuntu.com  sources, as i am in canada, without problem.

---

