---
title: "Command to completely remove app?"
date: 2013-02-08
forum: General Help
---

### Post by norcal618 on 2013-02-08
When removing unwanted software from my Ubuntu machine I used to use apt-get remove package followed by app-get autoremove. I recently read that that doesn't remove the config files. So I'm looking fpor a command to %100 remove all traces of an app. Would apt-get purge package && apt-get remove package then followed by apt-get autoremove do the trick? I searched around for an answer but couldn't find one that really explained it.

---

### Post by schragge on 2013-02-08
Yes, it would. And you don't need *apt-get remove package* after *apt-get purge package* - *purge* already includes *remove*.

---

### Post by ajgreeny on 2013-02-08
[LIST=1]
[*]**apt-get remove** just removes the package from the system folders but not all the dependencies, and not the configuration.
[*]**apt-get purge** removes the package and all system folder configurations, but again, not all dependencies.
[*]**apt-get autoremove** will remove any packages that were installed as dependencies of another package that is now no longer installed, but not the configurations of those dependencies.
[*]None of those commands will remove any configuration files and folders in your /home folder; you will need to do that task as a separate job.
[/LIST]
I use synaptic if I use a GUI app to manage packages not the software-centre, as it gives all those options plus others. It can find all unneeded dependencies, allow you to remove them but also lets you remove all configurations for those as well with the "Remove residual configuration" option in the left hand pane.

---

