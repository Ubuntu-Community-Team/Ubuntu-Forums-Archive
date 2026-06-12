---
title: "Failed to download repository information"
date: 2014-04-30
forum: General Help
---

### Post by grier-devon on 2014-04-30
So I went to so some updates today and the the update manager tells me "failed to update some packages", so then I go to "software and updates" to reload the repositories to see if there is something  wrong with a ppa I am using and I get this....
> Failed to download repository information
W:Failed to fetch [http://repo.steampowered.com/steam/dists/precise/steam/i18n/Translation-en](http://repo.steampowered.com/steam/dists/precise/steam/i18n/Translation-en)  Error reading from server. Remote end closed connection [IP: 23.59.190.115 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Any idea what this is and how to fix it?

---

### Post by kc1di on 2014-04-30
go system settings >Software & Updates > other tab and uncheck the steampowered repo.

in a terminal type : ```
sudo apt-get update
``` 
then see if the you can do the upgrade.

if that works and you need the steampowered repo you have to reinstall the ppa. good luck

---

### Post by grier-devon on 2014-04-30
Thanks so much for the post. I will give it a try. I did not install the ppa so I am assuming the ppa installed when I installed steam. How do I know which ppa from steam to install, like do I get the ppa from launchpad or valve website?

---

