---
title: "Call a script when battery state changes"
date: 2007-06-12
forum: General Help
---

### Post by Smiley-Man on 2007-06-12
How can I call a script when the battery state changes in ubuntu?  

Without using apmd as apm not compiled into kernel?

---

### Post by DagMan on 2007-06-12
Don't know if this is what you mean by the state changing, but to have a script look to see if you are on battery power or ac power you can do like this

#!/bin/bash

if on_ac_power ; then
 echo "on ac power"
else
 echo "on battery power"
fi


If you want something to run when the power state changes from battery to ac then you can look what actions happen you plug in and unplug your cable by doing this
tail -f /var/log/acpid | grep "received event"
and pluging and unplugging.

If you take a look at the files in /etc/acpi/events to see how your laptop might interpret something like that and send it to a script in /etc/acpi which would be able to do something with it.

For an example of how to hook to when your battery cable is plugged and unplugged for changing power management, Take a look at this page from gentoo but be warned that the directory structure is a little differant so it's talking about /etc/acpi/actions which in ubuntu is /etc/acpi

code listing 2.6 to 2.10
[http://www.gentoo.org/doc/en/power-management-guide.xml](http://www.gentoo.org/doc/en/power-management-guide.xml)


Hope that helps.  I don't know how to set something up that will check battery level or anything without making a script that runs in the background and looks periodically but it should be simpler or at least more efficiant to achieve since the panel applet and power manager do it already.

---

### Post by Smiley-Man on 2007-06-13
Thanks for the reply but had sorted it.

Just needed to call a script when ac plugged in and out.

Which I found out is easy to do by creating an event action in /etc/acpi/events.

---

### Post by southernman on 2007-06-13
I know your a smiling and all, but when you solve your own problem wouldn't it be fair if you marked your post as resolved... at least post behind yourself saying so. That way... well, I think you see the in depth post someone went through... on your behalf. 

Just seems fair is all. But, glad you sorted out your own problem. ;)

---

### Post by DagMan on 2007-06-13
It's really nice how people on forums of other distros edit the titles to add [resolved] so others with the same problem have a better indication of where to go, but it's never been done here that I've seen so I guess it's a big ask since it's not the convention here and it's too late to change it.  It sure makes for one huge mess when searching for a problem though, and causes people to post over and over about the same issues in many cases.
Smiley did come back to post the problem resolved though... but I know where you're coming from.  I reckon a huge red banner asking people to search first and edit the title [resolved] when it applies, should be put at the top of every page of all the help sections.

---

