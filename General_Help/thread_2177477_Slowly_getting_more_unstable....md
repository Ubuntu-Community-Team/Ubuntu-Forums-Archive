---
title: "Slowly getting more unstable..."
date: 2013-09-28
forum: General Help
---

### Post by formerflyboy2 on 2013-09-28
Over the past few months I've noticed my installation of 12.04 LTS getting more and more unstable. It started out with error messages popping up during startup but I don't have those available. I've noticed that the package updater wasn't starting so I tried to get it going manually and got the following error:

  Could not initialize the package information

An unresolvable problem occurred while initializing the package information.


Please report this bug against the 'update-manager' package and include the following error message:


'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

At this point I can't update any packages and the errors are getting more and more frequent. I tried using the command line but the same error is the result. It took me forever to get YNAB! (running under wine) and xTuple (for my business) up and running and I'd hate to have to lose the setup by wiping and reinstalling.

Any help is greatly appreciated and needed.

Jeff Day
iDevice Rx

---

### Post by TheFu on 2013-09-28
Run these ```

sudo apt-get update && sudo apt-get dist-upgrade

```
Then copy/paste the warning/errors in the output here.  Please wrap the output in "code" tags like I did so it is easier to read.

Also, if there are any warnings or errors in the log files - /var/logs/* - those would be useful too.

I hope we can figure this out.

---

