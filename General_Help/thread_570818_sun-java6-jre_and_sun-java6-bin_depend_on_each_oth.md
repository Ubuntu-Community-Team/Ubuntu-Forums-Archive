---
title: "sun-java6-jre and sun-java6-bin depend on each other and can't install"
date: 2007-10-08
forum: General Help
---

### Post by flypeyton on 2007-10-08
I tried to install sun-java6-jre and it shows dependency on sun-java6-bin. So I downloaded sun-java6-bin from another PC and copied it to this Ubuntu PC. And I double-clicked on the sun-java6-bin and it showed an error of dependency on sun-java6-jre. This drives me crazy. In a terminal, I used "dpkg -i" to try to install two packages at the same time. But still encounter the same problem and got broken configurations. So anyone has any ideas on this?

---

### Post by rsambuca on 2007-10-08
Why don't you just install them from the Synaptic Package Manager?

---

### Post by flypeyton on 2007-10-08
First, thanks for the reply. I tried double-click on the .deb packages. I think that actually use Synaptic Package Manager to install. But I still got the dependency problem. Do you mean any other way to install packages using Synaptic. BTW, my Ubuntu PC's USB wireless card can't connect to internet, which once could connect to a weak wireless signal of my school but couldn't under Ubuntu (I already used ndiswrapper to install the driver.) So I guess that I can't use something like apt-get.

---

### Post by zvacet on 2007-10-08
[http://ubuntuforums.org/showthread.php?t=475312&highlight=package+no+internet]("http://ubuntuforums.org/showthread.php?t=475312&highlight=package+no+internet")

And try to solve problem with your wireless.Post here if you need any help.

---

