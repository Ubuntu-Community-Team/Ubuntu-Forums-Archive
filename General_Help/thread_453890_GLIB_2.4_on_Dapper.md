---
title: "GLIB 2.4 on Dapper???"
date: 2007-05-24
forum: General Help
---

### Post by andrew.46 on 2007-05-24
Hi,

 I am attempting to compile the newest version of Sylpheed 2.4.2 to run on Dapper. But I am stuck with the following error on ./configure:

```
checking for GLIB - version >= 2.4.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: Test for GLib failed. See the 'INSTALL' for help.

```

 I could not see how to install an updated GLIB version for Dapper after searching Synaptic, although I did see bglibs-dev which may very well be what I need???

 Any thoughts on this? I note on the Install notes that Dapper is not officially 'confirmed to work' with this version, only Edgy (and not Feisty!).

            Thanks for your help,

                        Andrew

---

### Post by andrew.46 on 2007-05-24
Hi,

 Problem solved! I simply had to ferret around for the appropriate dev files for glib and then gtk+. And just for the record Sylpheed 2.4.2 works fine on Dapper :)

              Andrew

---

