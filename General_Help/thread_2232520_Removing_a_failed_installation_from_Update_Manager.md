---
title: "Removing a failed installation from Update Manager"
date: 2014-07-02
forum: General Help
---

### Post by jim62 on 2014-07-02
In my desperate attempt to install a printer, I appear to have done something that I should not have done. In my Update Manager I now get the following error, even after a restart.

ERROR###ERROR###ERROR###ERROR###ERROR###ERROR###ERROR
W:Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/saucy/main/source/Sources](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/saucy/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead

Any idea how I fix this and remove this package trying to install itself?

Thanks.

---

### Post by deadflowr on 2014-07-02
Open the program Software and Updates.
Go to the section Other Software
Uncheck, or simply remove the entries for that ppa.
Re run the software updater.
Beyond that
Go to the launchpad page for that ppa and check and see if the ppa is still available for that version of Ubuntu, and if so re-apply.

Edit: As a sidenote, if the printer is working, then you probably don't even need the ppa anymore.

Double Edit: Taking the time to look at the ppa, it seems it has not been updated for some time now.
The last version supported was 11.10, which as been end of life for a year now, i think.

---

### Post by jim62 on 2014-07-02
Thank you, that seem to have done the trick.

---

