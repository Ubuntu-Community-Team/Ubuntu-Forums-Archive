---
title: "Software Updater Runs Even When Set to Never"
date: 2013-09-12
forum: General Help
---

### Post by adec2 on 2013-09-12
HI, Every time i boot up my computer Software Updater runs even though its setting is set to "never" Has anyone any ideas how to sort this out?

---

### Post by bkline on 2013-09-12
Sounds like the problem discussed here:

[http://ubuntuforums.org/showthread.php?t=2083798](http://ubuntuforums.org/showthread.php?t=2083798)

If I read that thread correctly, the proposed solution was to remove the update-notifier-common package.

---

### Post by adec2 on 2013-09-12
to remove it completely seems a little extreme. or would it be worth a try to remove it then reinstall it?

---

### Post by ibjsb4 on 2013-09-12
Nothing wrong with removing update-manager, but you do need to keep update-manager-core.  It can also be disabled 

[http://ubuntuforums.org/showthread.php?t=1966228&p=11895545#post11895545](http://ubuntuforums.org/showthread.php?t=1966228&p=11895545#post11895545)

---

### Post by adec2 on 2013-09-13
Thanks for this i unhidden the startup applications using this command:

sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop

then unchecked the updates program in there.
Many thanks! :)

---

