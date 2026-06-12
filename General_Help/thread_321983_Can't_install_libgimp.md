---
title: "Can't install libgimp"
date: 2006-12-19
forum: General Help
---

### Post by Yaun on 2006-12-19
I am using dapper. I want to install libgimp2.0-dev so that I can install a GIMP plugin. So I type "sudo apt-get install libgimp2.0-dev", and I get the following message:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgimp2.0-dev: Depends: libgtk2.0-dev (>= 2.4.4-1) but it is not going to be installed
E: Broken packages

I tried "sudo apt-get install libgtk2.0-dev", but this gave the same error message, with the last line reading:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
And "sudo apt-get install libpango1.0-dev" gave:
  libpango1.0-dev: Depends: libpango1.0-0 (= 1.12.2-0ubuntu3) but 1.12.3-0ubuntu3 is to be installed

At the advice of a previous thread on the same topic, I added the lines
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
to my /etc/apt/sources.list, and then ran "sudo apt-get update", but that didn't fix the problem.

---

