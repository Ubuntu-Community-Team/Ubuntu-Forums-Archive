---
title: "Updating Ubuntu 13.04"
date: 2013-08-11
forum: General Help
---

### Post by Chris62 on 2013-08-11
Hi,

I am running 64-bit ubuntu 13.04 and have a minor query.

When I run Software Updater recently , I have been offered a lot of updates for Evolution such as updates for Evolution address book and Evolution  calendar. Evolution is not installed on my computer and I am wondering why I keep being offered these updates. If they are not necessary for some other aspect of Ubuntu, is there a way of stopping the from appearing every time I run Software Updater?

I know that some files to do with Evolution are, or might be, necessary for Ubuntu because when I first tried Ubuntu Evolution was installed by default, and I could not get it to work properly so I uninstalled it and ended up with a computer that would not boot. This was because, so i was told, Ubuntu required certain files used by Evolution in order to run properly

---

### Post by ibjsb4 on 2013-08-11
Evolution-data-server and data-server-common are the two packages that must be installed.  What do you show?

[ATTACH=CONFIG]245281[/ATTACH]

---

### Post by Chris62 on 2013-08-13
Hi, thanks for your reply. The files that it wants to install are:

Architecture independent files for Evolution Data server
Backend librarby for Evolution address books
Backend library for Evolution calendars
Client library for Evolution address books
Client library for Evolution calendars
Evolution database backend server
Evolution MIME message handling library

There isn't an Evolution date-server-common in the list and presumably I only need to install the Achitecture independent files for data-server?

---

### Post by ibjsb4 on 2013-08-13
I have not paid much attention to my evolution updates, but yours is looking ok to me.  Address and calendar seem to be part of the data-server package.  You could install [synaptic package manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9") and see if only the two evolution packages are installed.

```
sudo apt-get install synaptic
```

[ATTACH=CONFIG]245334[/ATTACH]

---

### Post by Chris62 on 2013-08-13
Thanks ibjs4,

The only e
Evolution stuff that is installed is evolution-data-server and evolution-data-server-common, so from the list produced by Software Updater I will install evolution-data-server and ignore the rest
Thanks for your help

---

