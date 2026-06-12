---
title: "Learning APT:  Orphans and Autoremove"
date: 2015-02-08
forum: General Help
---

### Post by dbdaniel42 on 2015-02-08
I just did a fresh install of Xubuntu 14.04 on VirtualBox.  I'm well experienced in Linux but I mostly use Arch Linux (which is hosting my Xubuntu VM.)  Anyway I'm trying to get more familiar with APT.  I know the basics of how to install, uninstall, search, and a little bit of dpkg but I'm a little stumped at how APT handles orphans.  To test this I installed synaptic.  Looking back at /var/log/apt/history.log:

```
Start-Date: 2015-02-08  00:46:20
Commandline: apt-get install synaptic
Install: libept1.4.12:amd64 (1.0.12, automatic), rarian-compat:amd64 (0.8.1-5ubuntu1, automatic), sgml-data:amd64 (2.0.9-1, automatic), docbook-xml:amd64 (4.5-7.2, automatic), librarian0:amd64 (0.8.1-5ubuntu1, automatic), synaptic:amd64 (0.81.1ubuntu1)
End-Date: 2015-02-08  00:46:33
```

OK so far so good.  It installed synaptic and marked its dependencies as "automatic."  Now to test out removing it.

```
Start-Date: 2015-02-08  05:11:09
Commandline: apt-get purge synaptic
Purge: synaptic:amd64 (0.81.1ubuntu1)
End-Date: 2015-02-08  05:11:11
```

After I did that APT was prompting me that it had un-needed packages I could remove with apt-get autoremove so I do.

```
Start-Date: 2015-02-08  05:13:13
Commandline: apt-get autoremove --purge
Purge: libept1.4.12:amd64 (1.0.12)
End-Date: 2015-02-08  05:13:14
```

But it only removed the very first dependency and left the others in place.  In between the Install and remove I only did one other APT transaction which updated three totally unrelated packages.  I didn't install anything else that would have depended on those packages that synaptic required.

```
Start-Date: 2015-02-08  04:48:59
Commandline: apt-get upgrade
Upgrade: mugshot:amd64 (0.2.3-1, 0.2.5-0ubuntu0.1), xfdesktop4-data:amd64 (4.11.6-1ubuntu1, 4.11.8-0ubuntu0.1), xfdesktop4:amd64 (4.11.6-1ubuntu1, 4.11.8-0ubuntu0.1)
End-Date: 2015-02-08  04:49:06
```

So yea this is my first stumping block in trying to learn APT.  In Arch and its package manager Pacman, every package is either "Explicity Installed" or "Installed as a dependency" and a standard query will tell you which it is.  If a package was installed as a dependency but is no longer required by anything it's listed as an orphan (there is no autoremove function in Pacman but there is a command to list all orphans and then uninstall from that list.)  Is that at all similar to how APT handles this?

---

### Post by v3.xx on 2015-02-08
As for apt-get, there are things like ..
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
and maybe
[https://wiki.ubuntu.com/SystemCleanUpTool](https://wiki.ubuntu.com/SystemCleanUpTool)

Deborphan may be more to your liking.  Use with care.
[https://www.google.com/search?q=Deborphan&ie=utf-8&oe=utf-8#q=removing+unnecessary+packages+with+deborphan&revid=81788483](https://www.google.com/search?q=Deborphan&ie=utf-8&oe=utf-8#q=removing+unnecessary+packages+with+deborphan&revid=81788483)

---

### Post by Bashing-om on 2015-02-08
dbdaniel42; Hi ! Welcome to the forum .

> 
Anyway I'm trying to get more familiar with APT.

My go-to when I want to know:
[http://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites](http://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites)

What I do in the case of removed packages' and config files remain ->
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package with the following command.
From a 'dpkg -l ' listing The state is rc, the package is removed, but the config files are not removed
To remove all the packages marked as rc.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```
As food for thought.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by dbdaniel42 on 2015-02-09
> **Bashing-om said:**
> dbdaniel42; Hi ! Welcome to the forum .


My go-to when I want to know:
[http://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites](http://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites)

What I do in the case of removed packages' and config files remain ->
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package with the following command.
From a 'dpkg -l ' listing The state is rc, the package is removed, but the config files are not removed
To remove all the packages marked as rc.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```
As food for thought.[INDENT][INDENT]inquiring minds want to know
[/INDENT]
[/INDENT]


That's helpful info but that's not quite what I was asking about.   I was asking about removing orphan **packages**, not config files.  For example I install package foo and packages bar1, bar2, and bar3 and installed as dependencies of foo.  If I later remove package foo then bar1-3 would be considered orpahns (packages that were installed as dependencies but are no longer needed because the dependent package has been removed.)  In the example I gave in the OP, "apt-get autoremove" removed one orphan but left the others alone.

I was thinking about this and doesn't APT have the concept of optional dependencies?  I was thinking maybe the reason "apt-get autoremove" didn't remove everything is because they happened to be optional dependencies for other packages II had installed.  Is there any way to check this?  Can I for example query a package and see what packages depend on it and if it's a hard dependency or an optional one?

---

### Post by mc4man on 2015-02-09
The example you used *seems* to indicate  - 
apt & autoremove  only deal with dependencies, not packages installed as a depends of a recommended package. (recommends are auto installed
So when installing synaptic - 

libept1.4.12 > a depend of synaptic
rarian-compat > a recommend of synaptic
librarian0 > a depend of rarian-compat
docbook-xml > a depend of rarian-compat
sgml-data > a depend of docbook-xml

so if you were to remove rarian-compat then the rest would be shown by autoremove

---

### Post by ian-weisser on 2015-02-09
> **dbdaniel42 said:**
> But it only removed the very first dependency and left the others in place.  In between the Install and remove I only did one other APT transaction which updated three totally unrelated packages.  I didn't install anything else that would have depended on those packages that synaptic required.

Confirmed in 14.10.
It's not you. It's not some strange way apt works. It's a straight-up bug.
'install foo' immediately followed by 'autoremove foo' should return the package system to the previous state. It doesn't.
Neither dependencies nor recommends are uninstalled by autoremove. They should be - they are all apt-marked as 'auto', and the only package that depends upon them is getting removed.

The bug report is at [https://bugs.launchpad.net/bugs/1419839](https://bugs.launchpad.net/bugs/1419839) 
Do NOT leave a 'me too' comment on the bug report. Instead, click the 'affects me too' link at the top of the bug page, and subscribe to it.
Other gurus on this thread, feel free to try the procedure in the bug report and see if you get a different result.

---

### Post by mc4man on 2015-02-09
use apt-cache show package to get extended info
Ex.
apt-cache show rarian-compat

---

### Post by ptn107 on 2015-02-09
Something useful to help your understanding?
```
apt-mark showauto > automatic.list
apt-mark showmanual > manual.list
apt-mark showhold > holds.list
```
Check out each list.

---

