---
title: "Tracker not finding much"
date: 2007-07-05
forum: General Help
---

### Post by Ed.Corcoran on 2007-07-05
I installed Tracker about a week ago. And it's not finding much at all. It doesn't find all the files it should and it doesn't find all the meta-information that it should. I really want a good desktop search program (specifically so that I can search within my .doc files) and I'd like to use Tracker rather than Beagle or Google Desktop Search because it integrates into the Gnome Desktop. But right now, it's useless.

Is there a way to rebuild my Tracker database? Or something like Beagle's Exercise_the_dog to make index faster?

---

### Post by Franko30 on 2007-07-10
> **Ed.Corcoran said:**
> 
Is there a way to rebuild my Tracker database?

Hi,

to rebuild the index, do the following:

[LIST]
[*]end/kill tracked (for instance via gnome-system-monitor)
[*]go to **/home/yourdirectory/.Tracker/databases** and delete all files and folders in this directory
[*]in the **.Tracker** directory, edit the tracker,cfg file to be sure all the directories you want to be indexed have an entry in this file
[*]restart tracker manually ba typing **trackerd** in a terminal
[*]to see even more of what's going on, use the **trackerd --verbosity=1** option
[*]check, if trackerd is part of the automatic startup programs in System->Settings->Sessions, so that it starts up automatically after the next reboot
[/LIST]

As for speed: I found trackerd to be much (days) faster than beagle when indexing tens-of-thousands of files across all my NFS- and Samba-mounted NAS-shares of my network.

Cheers

Franko30

---

