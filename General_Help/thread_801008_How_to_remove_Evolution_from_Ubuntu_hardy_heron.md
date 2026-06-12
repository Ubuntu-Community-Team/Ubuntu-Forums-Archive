---
title: "How to remove Evolution from Ubuntu hardy heron?"
date: 2008-05-20
forum: General Help
---

### Post by vlitzer on 2008-05-20
Hello there. After trying evolution for 2 weeks i came to the conclusion that it sucks :D, to slow, to much resource-consuming services that i dont use. So i want to remove it and anything related to. But when i start to check items to remove i noticed that removing them also removes LOTS of things including gnome panel (LOL?)

anyone knows some work around or how to remove only evolution? or is just imposible to get the thing out of my pc?

Thanks in advance!

---

### Post by cdtech on 2008-05-20
Try:

sudo apt-get remove --purge evolution

---

### Post by ozorba on 2008-05-20
Evolution is part of ubuntu-desktop packages. Just do not use it. From System-Preferences select Sessions Preferences and untick Evolution Alarm Notifier.

---

### Post by vlitzer on 2008-05-20
ive tried that! but they are a lot of services of evolution that still on my system

---

### Post by 620hun on 2008-05-25
```
aptitude search evolution
```

and ```
sudo apt-get remove
``` every stuff which has an "i" in front of it, except evolution-data-server-common

it doesn't remove any core parts of ub.:)

---

### Post by hexdsl on 2009-02-01
anyone confirm that the above code works for removing all Evolution related stuffs?

---

### Post by wu-stix on 2009-02-14
sudo apt-get autoremove evolution

You may still have the icon but you can get rid of this by right clicking the ubuntu symbol and then edit.

---

### Post by khonnsu on 2009-10-11
Yeah, this annoys the blip out of me.

I am running 64 bit hardy on a Thinkpad x61s. When I look down to packages matching 'evolution*', I'm seeing 15 different installable items.

Anyway, I have no use for any of them so I remove all the packages that don't also remove ubuntu-desktop. I go through my sessions options and remove evolution notifier. I am left with evolution-data-server and evolution-data-server-common.

Then I do:

lsof|grep -i evolution

So, this is as 'removed' as I can get it?

I have this machine running on a bare 11 watts and 100 wake-ups per second. The evolution-data-server is visible as a 'top' process and using noticeable resources.

All this and no manual entry for evolution or it's data server component.

Like seriously, what?

---

### Post by khonnsu on 2009-10-13
Alright folks...

One more place to look for evolution stuff is in firefox (or whatever apps you have that may be calling evolution).

On this system, firefox defaults to evolution for it's mail handler. By changing that value in firefox's options to ~anything else~ (preferences - applications), and doing the steps outlined earlier in this thread, I have prevented evolution from executing on my computer.

I still cannot get evolution-data-server out of my installed packages list - but there is now no trace of any code being executed. I have no evolution-data-server process and lsof generates nothing for evolution.

I think it's all about preventing anything from calling evolution and it's quiet as a mouse.

---

