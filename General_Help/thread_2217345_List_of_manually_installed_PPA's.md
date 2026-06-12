---
title: "List of manually installed PPA's"
date: 2014-04-16
forum: General Help
---

### Post by jkossis on 2014-04-16
Hello all,

I am trying to find a way to get a list of PPA's that I have manually installed. I don't want it to include the system default ones that come with a fresh install. The reason for this is I am trying to make an installation script that will install my commonly used programs when I decide to update my system. Any commands for this? Thanks for any help!

---

### Post by monkeybrain20122 on 2014-04-16
All of them are in /etc/apt/sources.list.d. You can just backup that folder and copy it over in your new install and then run sudo apt-get update. But you have to edit the files in the folder because their entries are specific to the Ubuntu release (so e.g change all the occurrences of 'precise' to 'saucy' in all these files if you move from 12.04 to 13.10) Also, some ppas may not be available for 14.04 if that is what you plan to install because it may take a while for them to be set up.

---

### Post by jkossis on 2014-04-16
Thank you for the response!

---

### Post by papibe on 2014-04-16
Hi jkossis.

This [thread]("http://ubuntuforums.org/showthread.php?t=2216217&highlight=backup+ppa") and the links included there might be useful too.

Hope it helps.
Regards.

---

