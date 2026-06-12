---
title: "Update confusion"
date: 2022-01-07
forum: General Help
---

### Post by coley9225 on 2022-01-07
Hello all, I hope everyone had a great holiday season, and this thread finds you all well.
I do my updates/upgrades in terminal. This morning, i ran sudo apt upgrade && apt list -- upgradable, like I do almost daily. I glance through too see what's going to be upgraded. This morning I saw 2 items that I'm unsure of. The first is "python3-commandnotfound:amd64(20.04.4,20.04.5)", and the other is "command-not-found:amd64:(20.04.4,20.04.5)". I wanted to know if these are normal, and what exactly are these upgrades. I ran the upgrades, and no system crash(yet), be was just wondering what these are, what they do, and is this normal. If anyone can clarify this I would be grateful. Thanks.

---

### Post by TheFu on 2022-01-07
python3-commandnotfound is a real package.
```
$ dpkg -l python3-commandnotfound*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                    Version      Architecture Description
+++-=======================-============-============-===========================>
ii  python3-commandnotfound 20.04.4      all          Python 3 bindings for comma
```

**command not found** is an error.  Looks like a program isn't available - not in the path or corrupted or removed.

I hope you run 
```
sudo apt update
sudo apt full-upgrade
```
weekly.
And run 
```
sudo apt autoremove
sudo apt autoclean
```
every 2-4 weeks.
If you have versioned backups, can you compare the current files against the last good backup set? Which files have changed or are added/missing now that you do not expect?

---

### Post by TheFu on 2022-01-07
BTW
```
$ command-not-found
command-not-found: command not found

```
It isn't a program that we run directly.

```
$ apt search command-not-found
Sorting... Done
Full Text Search... Done
command-not-found/focal-updates,focal-updates,now 20.04.4 all [installed]
  Suggest installation of packages in interactive bash sessions

packagekit-command-not-found/focal-updates,focal-security 1.1.13-2ubuntu1.1 amd64
  Offer to install missing programs automatically

python3-commandnotfound/focal-updates,focal-updates,now 20.04.4 all [installed,automatic]
  Python 3 bindings for command-not-found.
```
Looks like it is connected to bash ... probably the program that looks up which package a command is in when the command we type isn't available. I wouldn't worry at all. Convenience.

---

### Post by coley9225 on 2022-01-07
Thanks TheFu, I just wanted to make sure I didn't make a mistake by upgrading these. I don't run full-upgrade, not clear(yet) on what that does. I tried system upgraade once, and had to fall back on my backups to get going again. I also have been holding off on auto remove and auto clean, because I've read that bad things sometimes happen, but if these are things that I should do, I have multiple backups so I could recover quickly in the event of a system meltdown. I will run auto remove and auot clean today and see what happens, and possibly full upgrade as well. Thanks again.

---

### Post by TheFu on 2022-01-07
The manpage for apt-get explains what each option does in plain language.

---

### Post by coley9225 on 2022-01-07
Thanks TheFu. I ran all of the items you suggested, and nothing to remove. I may be somehow keeping my stem cleaner than I thought. I'll take a look at the man pages, just so I better understand what it is that I'm doing. You(as always) have been very helpful. I'll go ahead and mark this thread as solved. On an off topic question... I recently saw a poster looking for help with a printer. I have a similar printer and had issues. I wanted to post a link to the thread I started so he could see what I did, as well as helpful posts from other, more expeienced users. How do I post a link to another thread, so I'll know in the future. If you recommend I start a new thread, I can do that, just thought this would be easier. Thanks.

---

### Post by TheFu on 2022-01-07
copy/pasting the URL doesn't work?

---

### Post by coley9225 on 2022-01-07
I'll give that a shot. Thanks.

---

### Post by schragge on 2022-01-07
> **TheFu said:**
> python3-commandnotfound is a real package.
**command-not-found** is a real package as well, and it depends on **python3-commandnotfound**.
```
[COLOR=green]$[/COLOR] apt show command-not-found[COLOR=green]
Package: command-not-found
Version: 20.04.5
Priority: standard
Section: admin
Origin: Ubuntu
[...]
Depends: python3-commandnotfound (= 20.04.5)
Suggests: snapd
Task: standard
[...]
Description: Suggest installation of packages in interactive bash sessions
 This package will install a handler for command_not_found that looks up
 programs not currently installed but available from the repositories.[/COLOR]
```
It installs an APT update hook in **/etc/apt/apt.conf.d/50command-not-found**. The script it runs in that hook is **/usr/lib/cnf-update-db**

---

