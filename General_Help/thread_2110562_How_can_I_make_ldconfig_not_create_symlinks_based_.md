---
title: "How can I make ldconfig not create symlinks based on the SONAMES of common libraries?"
date: 2013-01-30
forum: General Help
---

### Post by hackaxle on 2013-01-30
McAfee Platinum support cannot seem to help me with this so I thought I might ask here. I am trying to install McAfee Agent and McAfee Virus Scan for Linux onto Ubuntu 12.04. However, after I install it anytime an ldconfig is performed, or a package is installed by apt-get for example it completely breaks the system.

Here is what I think is happening:

ldconfig is creating symlinks that point common libraries to McAfee files anytime ldconfig is run.

They suggested I find out how to make ldconfig not create symlinks based on the SONAMES of common libraries.

I can temporarily fix the issue by stopping the cma and nails service and then renaming two files:

/lib/ld-mfert.so.2 to /lib/mfert.so.2 and /lib/ld-nails.so.2 to /lib/nails.so.2

after I install a package I then reverse the actions, renaming the files to the original names and start the services back up.

Does anyone know how I can fix this so I don't have to rename these files every time I want to install a package?

ld-linux.so.2 I believe is the culprit.

Before installing McAfee:

ld-linux.so.2 -> i386-linux-gnu/ld-2.13.so

After ldconfig is ran after installing McAfee:

ld-linux.so.2 -> ld-mfert.so.2

ld-mfert.so.2 -> /opt/McAfee/runtime/2.0/lib/ld-linux.so.2

---

### Post by n664dc on 2013-10-28
You are correct. The McAfee package is very broken, in more ways than this. I have 1.9.0.28822.

Please try this before installing McAfee:
ln -sf /lib/i386-linux-gnu/ld-linux.so.2 /lib/ld-~fix-linux.so.2

Then also check your links in /usr/lib to ensure they are not pointing at McAfee files. My /usr/lib/libstdc++.so.6 was.

See also: [https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/915995](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/915995)

Please also evaluate why you are using McAfee on Linux, and if it is prudent or useful.

---

