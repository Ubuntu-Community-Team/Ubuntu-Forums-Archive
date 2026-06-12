---
title: "Update Manager Wants To Update Held Back Locally Built Package"
date: 2013-02-26
forum: General Help
---

### Post by buzzingrobot on 2013-02-26
Update Manager wants to update a locally built version of a package in the Ubuntu repositories. I built the package locally to add features I need. I suppressed updates via "echo 'MyPackage hold' | sudo dpkg --set-selections"

As expected, a "sudo apt-get update && sudo apt-get upgrade" shows the package is held back.

Update Manager, however, constantly indicates an update is available, and that the repository version of my package is the one needing updating.

Can I convince Software Update to stop being annoying and just pretend this package does not exist?

---

### Post by matt_symes on 2013-02-26
Hi

Try using apt-mark

```
sudo apt-mark hold <package-name>
```Maybe update manager ignores dpkg. I don't know as i don't use it.

EDIT:

Then again i've just read this from the man page.
> 
hold
           hold is used to mark a package as held back, which will prevent the package from being automatically installed,
           upgraded or removed. The command is only a wrapper around dpkg --set-selections and the state is therefore maintained
           by dpkg(1) and not affected by the --file option.So ignore this advice.

Have you tried to see whether it actually gets updated if you hit yes, as you can always put it back ?

Kind regards

---

