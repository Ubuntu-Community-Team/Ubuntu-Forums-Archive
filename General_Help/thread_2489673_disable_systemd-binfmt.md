---
title: "disable systemd-binfmt"
date: 2023-08-06
forum: General Help
---

### Post by bjlockie on 2023-08-06
I want to save 895ms. :-)

I tried:
$ sudo systemctl disable systemd-binfmt

but it comes back.

How do I disable it permanently?

---

### Post by #&amp;thj^% on 2023-08-06
Try this:
```
systemctl stop systemd-binfmt

```
then
```
systemctl mask systemd-binfmt
```
check with:
```
systemctl status systemd-binfmt
&#9675; systemd-binfmt.service
     Loaded: masked (Reason: Unit systemd-binfmt.service is masked.)
     Active: inactive (dead)


```
EDIT: is the time wort it?
> DESCRIPTION         top

       systemd-binfmt.service is an early boot service that registers
       additional binary formats for executables in the kernel.

---

### Post by bjlockie on 2023-08-06
> **1fallen said:**
> 
EDIT: is the time wort it?

Probably not.

It's in the background of stuff needed for the graphical.target, right?

---

### Post by #&amp;thj^% on 2023-08-06
I rebooted after making my suggestions and all went well, but some app's or drivers may need it. (I'm just not sure on yours though)
Man Page
```
SYSTEMD-BINFMT.SERVICE(8)   systemd-binfmt.service   SYSTEMD-BINFMT.SERVICE(8)

NAME
       systemd-binfmt.service, systemd-binfmt - Configure additional binary
       formats for executables at boot

SYNOPSIS
       systemd-binfmt.service

       /lib/systemd/systemd-binfmt

DESCRIPTION
       systemd-binfmt.service is an early boot service that registers
       additional binary formats for executables in the kernel.

       See binfmt.d(5) for information about the configuration of this
       service.

OPTIONS
       --unregister
           If passed, instead of registering configured binary formats in the
           kernel, the reverse operation is executed: all currently registered
           binary formats are unregistered from the kernel.

       --cat-config
           Copy the contents of config files to standard output. Before each
           file, the filename is printed as a comment.

       --no-pager
           Do not pipe output into a pager.

       -h, --help
           Print a short help text and exit.

       --version
           Print a short version string and exit.

SEE ALSO
       systemd(1), binfmt.d(5), wine(8)

systemd 252                                          SYSTEMD-BINFMT.SERVICE(8)

```
As a tester I need to get things like that out of the way when looking for problems on my end, so I re-enabled it. (And unmasked as well)
EDIT: Also see "man binfmt.d" there is more information for you.

---

