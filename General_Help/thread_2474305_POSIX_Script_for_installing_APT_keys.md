---
title: "POSIX Script for installing APT keys"
date: 2022-04-26
forum: General Help
---

### Post by ameinild on 2022-04-26
Hi everyone!

With the release of Ubuntu 22.04, APT now throws a warning if a repository key is in the legacy trusted keyring ([FONT=courier new]/etc/apt/trusted.gpg[/FONT]).

Because the [FONT=courier new]apt-key [/FONT]command has been deprecated for some time, I created a script to help install the keys in the proper place ([FONT=courier new]/usr/share/keyrings[/FONT]).

The script is available on [github.com/ameinild/add-apt-key]("https://github.com/ameinild/add-apt-key").

I would appreciate if anyone would like to test this script, and please report back if there are some specific keytypes that are not recognized or if you encounter other errors, then I'll try to fix it.

Remember to include the exact command you ran when reporting an issue. Thanks! :cool:

---

