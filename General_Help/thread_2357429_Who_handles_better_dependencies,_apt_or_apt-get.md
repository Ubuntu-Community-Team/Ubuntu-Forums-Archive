---
title: "Who handles better dependencies, apt or apt-get?"
date: 2017-04-02
forum: General Help
---

### Post by joan_carles2 on 2017-04-02
I think that apt and apt-get share most of the code. So both options have similar performance and should have the same behaviour.


However somewhere in askubuntu forum I read next:


> apt was designed to fix some of the fundamental dependency flaws in apt-get. As it is a wrapper, apt is therefore higher level, and also loses some backward compatibility and scripting features.

Is that correct? I think this is not correct. I think they are not correct.

Rgds and thks

---

### Post by TheFu on 2017-04-03
Don't forget aptitude.  I find that aptitude is smarter when complex dependencies are needed compared to apt or apt-get.  It is nice to be able to reject mysql as a solution when I've decided to run mariaDB instead. Shouldn't be too much of any issue anymore, but on 14.04 systems, I've been burned by hard mysql dependencies in some packages.

I suspect the real answer is a little more complex.  Nothing can replace reading the manpage for each command carefully.
```
APT(8)                                APT                               APT(8)

NAME
       apt - command-line interface

SYNOPSIS
       apt [-h] [-o=config_string] [-c=config_file] [-t=target_release]
           [-a=architecture] {list | search | show | update |
           install pkg [{=pkg_version_number | /target_release}]...  |
           remove pkg...  | upgrade | full-upgrade | edit-sources |
           {-v | --version} | {-h | --help}}

DESCRIPTION
       apt provides a high-level commandline interface for the package
       management system. It is intended as an end user interface and enables
       some options better suited for interactive usage by default compared to
       more specialized APT tools like apt-get(8) and apt-cache(8).
...
SCRIPT USAGE AND DIFFERENCES FROM OTHER APT TOOLS
       The apt(8) commandline is designed as an end-user tool and it may
       change behavior between versions. While it tries not to break backward
       compatibility this is not guaranteed either if a change seems
       beneficial for interactive use.

       All features of apt(8) are available in dedicated APT tools like apt-
       get(8) and apt-cache(8) as well.  apt(8) just changes the default value
       of some options (see apt.conf(5) and specifically the Binary scope). So
       you should prefer using these commands (potentially with some
       additional options enabled) in your scripts as they keep backward
       compatibility as much as possible.

SEE ALSO
       apt-get(8), apt-cache(8), sources.list(5), apt.conf(5), apt-config(8),
       **The APT User's guide in /usr/share/doc/apt-doc/,** apt_preferences(5),
       the APT Howto.


``` It goes on with deeper knowledge and compares the different options with those of apt-get.

manpages are awesome.

---

### Post by vasa1 on 2017-04-03
> **joan_carles2 said:**
> ...
However somewhere in askubuntu forum I read next:
...
It's always nice to provide the source of any quotation :)
Here it is: [http://askubuntu.com/a/829866](http://askubuntu.com/a/829866)

And, as TheFu, pointed out, the man pages are usually more reliable than opinions even if the latter are stated as fact.

I don't know why the poster wrote> apt was designed to fix some of the fundamental dependency flaws in apt-get

Edit: if you're interested in following the development of apt, [https://lists.debian.org/deity/](https://lists.debian.org/deity/) is one place to visit:
> Debian Mailing Lists

deity

APT packages maintenance
Debian has a friendly frontend to its package maintenance system. Its codename is deity (now known as APT) and its development is discussed here. The -digest is open to everyone.
This list is not moderated; posting is allowed by anyone.



---

