---
title: "Xubuntu 15.04 not updating"
date: 2015-06-10
forum: General Help
---

### Post by John_Carver on 2015-06-10
[SIZE=3][B]When ppa/ubuntu/vivid is selected in software updater, updater will not update.
Unchecking allows update for all other sources.
Thoughts?[/B][/SIZE]

---

### Post by westie457 on 2015-06-10
What error messages do you get.
Post please the output of ```
sudo apt-get update
```

---

### Post by John_Carver on 2015-06-10
[B]W:Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.[/B]

---

### Post by buzzingrobot on 2015-06-10
The 404 response is the standard response when the URL does not exist.  In this case, no Vivid repository exists at the address. This can happen when a user updates to a new release but the PPA maintainer does not add packages for the release.

The updater's behavior is the result:  It tried to get an index of files that aren't there.

If you remove that PPA entry, or comment it out in the sources file, the updater should work.

---

### Post by John_Carver on 2015-06-10
What am I missing in updates when this line is removed?
And, is there a way to get a correct PPA?

---

### Post by buzzingrobot on 2015-06-10
The maintainer of that PPA has not created a Vivid section (i.e., a directory on the server) and added any Vivid packages to it, so you will not be missing anything.  Whatever packages(s) you installed from that PPA on an earlier version, they are not available for Vivid. 

You're getting the error because that line is telling the package manager to check a non-existent directory to determine if the package on your system can be updated with a newer package on that server. What happens when you remove the line is the error goes away.

You can look at the directory listing of all the sections maintained in that PPA here: [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/).

The maintainers primary page on launchpad.net (where PPA's live) is here: [https://launchpad.net/~tualatrix](https://launchpad.net/~tualatrix).  You'll see links to the individual PPA's midway down the page.

I don't see any Vivid work at those PPA's, so there is no "correct" PPA to add.

---

### Post by John_Carver on 2015-06-10
Thanks for taking the time and answering.
I appreciate it

---

