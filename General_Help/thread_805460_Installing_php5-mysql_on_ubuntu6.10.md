---
title: "Installing php5-mysql on ubuntu6.10"
date: 2008-05-24
forum: General Help
---

### Post by maverick909 on 2008-05-24
Hello,

Im a newbie to ubuntu and I was trying to get my website up and running on ubuntu. I had apache2, php5 installed on my box. I realized I needed php5-mysql as well, I tried doing an apt-get install. I got the following error

apt-get install php5-mysql
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
  php5-mysql: Depends: php5-mysqli (= 5.1.2-1ubuntu3.10) but it is not going to be installed
              Depends: php5-common (= 5.1.2-1ubuntu3.10) but 5.1.6-1ubuntu2.7 is to be installed

Anybody has any idea, how  ineed to proceed over here?

---

