---
title: "sudo =  segmentation fault (core dumped)"
date: 2007-05-22
forum: General Help
---

### Post by rackley on 2007-05-22
Hey all,

I've had this problem now with both Edgy and Feisty Fawn, both Ubuntu and Kubuntu flavors.  I have a Dell D620 laptop. Here's how the saga goes:

I do a clean install from CD-ROM.  It boots up and everything is happy.  I run the updater to update whatever packages are out of date.

Reboot.

Desktop comes up with a slew of error popups (from all the programs that tried to run and crashed.)  Any attempt to sudo causes a segmentation fault.

```
rackley@rackley-laptop:/$ sudo su -
Password: 
Segmentation fault (core dumped)
rackley@rackley-laptop:/$
```

Even ls is broken:

```
rackley@rackley-laptop:/$ ls -l
ls: unrecognized prefix: su
ls: unparsable value for LS_COLORS environment variable
total 84
Segmentation fault (core dumped)
rackley@rackley-laptop:/$
```

End of story.  Reformat and reinstall required because I can't do anything because I can't get root perms anymore.  Anybody have any ideas as to what could possibly hose up my system so badly from an automatic update?

---

