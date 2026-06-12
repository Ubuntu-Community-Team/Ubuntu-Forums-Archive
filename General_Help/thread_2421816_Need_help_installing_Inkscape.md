---
title: "Need help installing Inkscape"
date: 2019-06-27
forum: General Help
---

### Post by Donnie Love on 2019-06-27
I need to install Inkspace 0.92.4 on Lubuntu 14.04.


[LIST]
[*]                                          Software Center gives me this error:

The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f 
[*]I entered apt-get install -f and it says:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? 
[*]                                                                                                                                                                                                                                                         I don't know what third party repositories are or how to disable them. 
[/LIST]

---

### Post by TheFu on 2019-06-27
Sorry, but 14.04 is a dead release. 

Support ended a few months ago so all the repositories are gone. There haven't been any patches since, that includes security patches.

Move to 16.04 or 18.04, both are LTS releases with 5 yrs of support from their release date.

---

### Post by Donnie Love on 2019-06-27
OK. Thank you.

---

### Post by coffeecat on 2019-06-27
Forum Feedback and Help is not for technical support enquiries.

*Thread moved to **General Help**.*

Lubuntu has a shorter support time than Ubuntu. Lubuntu 14.04 has been out of support for over 2 years. Support for Lubuntu 16.04 ended in April this year. The currently supported Lubuntu LTS is 18.04.

---

