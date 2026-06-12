---
title: "Open Office Problem..."
date: 2007-12-08
forum: General Help
---

### Post by Nastydog on 2007-12-08
Hi

i updade my open office from the update manager tree days ago... and now i can't install anything...

when i run the update program it tells me this :

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

and then i run apt-get install -f :

Need to get 0B/37.8MB of archives.
After unpacking 2179kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 133738 files and directories currently installed.)
Preparing to replace openoffice.org-core 1:2.3.0-1ubuntu5 (using .../openoffice.org-core_1%3a2.3.0-1ubuntu5.3_i386.deb) ...
Unpacking replacement openoffice.org-core ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_1%3a2.3.0-1ubuntu5.3_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libtk680li.so')
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-core_1%3a2.3.0-1ubuntu5.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

What i can do to solve this? Thanks

---

### Post by PmDematagoda on 2007-12-08
Try:-

```
sudo rm /var/cache/apt/archives/openoffice.org-core_1%3a2.3.0-1ubuntu5.3_i386.deb
```

After that do:-

```
sudo apt-get update
```
Then do:-
```

sudo apt-get install -f
```

---

### Post by ace007 on 2007-12-17
Yup, it worked for me

---

