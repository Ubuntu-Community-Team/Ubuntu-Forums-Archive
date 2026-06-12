---
title: "---uninstall a package completely"
date: 2014-06-07
forum: General Help
---

### Post by bzhao on 2014-06-07
For the long time passed I have been having this problem, but I did not care to much, which
is: 
For never installed package redmine:
$dpkg -l redmine 
dpkg-query: no packages found matching redmine
After I purge it (apt-get purge redmine):
$dpkg -l redmine
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                  Version         Architecture    Description
+++-=====================-===============-===============-===============================================
un  redmine               <none>          <none>          (no description available)

As per these info, I know the system still  know the redmine package is "un" status,  not the same as the status the redmine package is not never installed

For Ubuntu 14.04 system, After I run apt-get autoremove,  I use dpkg -l remine command ang get:
dpkg-query: no packages found matching redmine

But for Ubuntu 12.04 system, I have try run apt-get autoremove, apt-get autoclean and apt-get clean command,
I alway get the status like from dpkg -l redmine:
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                  Version         Architecture    Description
+++-=====================-===============-===============-===============================================
un  redmine               <none>          <none>          (no description available)


Please help me with the command I can use to clean the package installation footprint
I still did not care to much about this problem, but the solution will make my script simpler.

---

### Post by bapoumba on 2014-06-07
Have you tried with ```
dpkg --purge redmine 
```?
No idea what redmine is.. /me goes to have a look.

>  purge  The  package  is  selected  to be purged (i.e. we want to remove
              everything from system directories, even configuration files).

---

### Post by stalkingwolf on 2014-06-07
even though you have completely removed the package there may still be a folder in your home folder , this happens with thunderbird i know.
Go to Home >view> show hidden files.  look for a folder named redmine if its there delete it.

---

### Post by bzhao on 2014-06-10
> **bapoumba said:**
> Have you tried with ```
dpkg --purge redmine 
```?
No idea what redmine is.. /me goes to have a look.

Yes I did "sudo dpkg --purge redmine", the case is still there!

---

### Post by bzhao on 2014-06-10
Finally I got the solution form manpage dpkg:
 run: sudo dpkg --clear-avail

---

### Post by bapoumba on 2014-06-10
Ah good to know :)
Please mark your thread as solved (under Thread tools), thanks.

---

