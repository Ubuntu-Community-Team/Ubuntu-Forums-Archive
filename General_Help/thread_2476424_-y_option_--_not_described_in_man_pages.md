---
title: "-y option -- not described in man pages"
date: 2022-06-25
forum: General Help
---

### Post by straitsfan on 2022-06-25
Was doing some terminal work today with apt install -y while being assisted by someone, but I can't find in the man pages a description of -y for either of these commands.  How would I have known about this?  Just curious in case I need to use it again.

---

### Post by yetimon_64 on 2022-06-25
> **straitsfan said:**
> Was doing some terminal work today with apt install -y while being assisted by someone, but I can't find in the man pages a description of -y for either of these commands.  How would I have known about this?  Just curious in case I need to use it again.
Seems you are right that it is not listed in "man apt" (first time I've ever checked after reading your post); I'm not entirely sure why.

However in "man apt" there is  ...
```
SEE ALSO
       **apt-get**(8), apt-cache(8), sources.list(5), apt.conf(5), apt-config(8), The APT User's guide in /usr/share/doc/apt-doc/, apt_preferences(5), the APT Howto.
```
If you follow this and read the options in "man apt-get" (which I've bolded/highlighted here) the "-y" option and all the other useful options eg. "-s" (simulate), "-f" (fix broken) etc., that also work with apt, are documented there.

---

### Post by TheFu on 2022-06-26
> **straitsfan said:**
> Was doing some terminal work today with apt install -y while being assisted by someone, but I can't find in the man pages a description of -y for either of these commands.  How would I have known about this?  Just curious in case I need to use it again.

apt is from apt-get, so any options not inside it are passed to apt-get.
```
       -y, --yes, --assume-yes
           Automatic yes to prompts; assume "yes" as answer to all prompts and
           run non-interactively. If an undesirable situation, such as
           changing a held package, trying to install an unauthenticated
           package or removing an essential package occurs then apt-get will
           abort. Configuration Item: APT::Get::Assume-Yes.
```

I think apt started as a script for apt-get, but at some point became a separate program.  I always just assume that apt is still a wrapper around apt-get and some other tools. This is probably incorrect now, but it does seem to work that way.

apt does make some things much easier and merges apt-get, apt-search, dpkg-query, and some parts of dpkg into a single tool.  It also still has a warning that apt shouldn't be used in scripts, of which we all should pay attention.  I don't ever use -y with apt.  How hard is it to look at the terminal, see the question and press <enter> when needed?  A few times, scanning the list of packages to be added/removed and seeing some very important ones that, if removed, would break the system, has saved me from trashing a system and needing to restore from backups or an LVM snapshot.

---

