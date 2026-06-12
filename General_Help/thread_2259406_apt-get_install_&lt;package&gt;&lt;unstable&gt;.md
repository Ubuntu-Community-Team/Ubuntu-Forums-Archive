---
title: "apt-get install &lt;package&gt;/&lt;unstable&gt;"
date: 2015-01-04
forum: General Help
---

### Post by bmike1 on 2015-01-04
[COLOR=#282828][FONT=helvetica][SIZE=3]A specific version of a package can be selected for installation by
following the package name with an equals (=) and the version of the package to select. This will cause that version to be located and selected for install. Alternatively, a specific distribution can be selected by following the package name with a slash (/) and the version of the distribution or the Archive name (i.e. stable, testing, unstable).
 
source: [http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

So this is saying to me you don't need the PPA to install the latest version but can instead do:
<package>=<version>

If that is so we don't need to add PPAs to our systems. IN other words PPAs are just a way to make it so that we are always running the latest version of the package regardless of if it works whereas we choose what we want to run with:
<package>=<version>[/SIZE][/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica][SIZE=3]okay.... after further research I discovered that <package>=<version> is only used to downgrade a package which has just been upgraded and found not to work and that to install an unstable package in an otherwise wise testing system (I think ubuntu is on a testing repo) you:[/SIZE][/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica][SIZE=3]
[/SIZE][/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica][SIZE=3]   apt-get install <package>/<stable/testing/unstable>[/SIZE][/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica][SIZE=3] [/SIZE][/FONT][/COLOR]
[SIZE=3]This is supposed to work on a Debian system but it does not work in Ubuntu. Is there a way to force an unstable package (while maintaining the testing repository) onto your system?[/SIZE]
[SIZE=3]
[/SIZE]

---

### Post by Impavidus on 2015-01-04
You can force a specific version of a package, provided that specific version is available from your software sources. The purpose of PPAs is to add new software sources.

---

### Post by schragge on 2015-01-04
Ubuntu doesn't have an equivalent of Debian unstable repository. See [http://askubuntu.com/questions/442058](http://askubuntu.com/questions/442058). The closest thing Ubuntu has is an alias *devel* that always points to the release being developed. E.g. currently it points to vivid.

---

