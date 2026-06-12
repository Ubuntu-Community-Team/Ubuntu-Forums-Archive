---
title: "No address associated with hostname)"
date: 2014-01-24
forum: General Help
---

### Post by borgward on 2014-01-24
I am getting No address associated with hostname while downloading K3busing Synaptic package manager. I get the same kind of message on another laptop while running the update manager. I also get it when I try apt-get from the commandline. What to do?

---

### Post by Dave_L on 2014-01-29
Here are some similar problem reports with suggested solutions:

[http://askubuntu.com/questions/142508/how-to-fix-5-no-address-associated-with-hostname-error-while-updating](http://askubuntu.com/questions/142508/how-to-fix-5-no-address-associated-with-hostname-error-while-updating)

[http://ubuntuforums.org/showthread.php?t=1589734](http://ubuntuforums.org/showthread.php?t=1589734)

Do either of those help?

---

### Post by borgward on 2014-01-30
I already solved the problem. After looking at several years worth of comments about this problem,  and seeing it was a closed thread at ubuntuforums I took another look at the error message:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/packages.linuxmint.com_dists_nadia_import_i18n_Tra nslation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I decided something was wrong with the MergeList and posted "Problem With Merge List" at [http://ubuntuforums.org/showthread.php?t=2201760](http://ubuntuforums.org/showthread.php?t=2201760)

Below is the question I posted:

I read about changing router settings. Did not think the problem was there. Connected my laptop directly to my isp's cable. was able to ping w/no errors. Then tried apt-get and update manager again, getting same error message.

Something wrong with /var/lib/apt/lists/packages.linuxmint.com_dists_nadia_import_i18n_Tra nslation-en that I posted above? what should it read?

Answer:

We most often see this as a result of a corrupted control file.
Try this:
terminal codes:
Code:

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

where "rm" removes the control files, "mkdir" makes a new directory, "update" syncs the data bases and repopulates the control files, and finally "upgrade" updates your installed packages to the latest versions available in the repository.

I would highly recommend commenting out /var/lib/apt/lists before running sudo rm -fr /var/lib/apt/lists just to be on the safe side.


[http://askubuntu.com/questions/14250...while-updating](http://askubuntu.com/questions/14250...while-updating) - Do not think that would have helped me one bit. ymmv

[http://ubuntuforums.org/showthread.php?t=1589734](http://ubuntuforums.org/showthread.php?t=1589734) - Again, a lot about internet settings. Not at all helpful as it does not address the root problem that the MergeList is corrupted.

---

