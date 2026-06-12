---
title: "apt-get in local folder, problem"
date: 2016-08-31
forum: General Help
---

### Post by steve12342 on 2016-08-31
Hello All:
On my own computer, I can use "apt-get install" to install global level packages; but if I try to do the same--on my university-shared computer--I find that I cannot use "apt-get," I can't use "sudo apt-get," because _I lack root privileges_.  Of course I could write my system administrator, each time I need an apt-get; but I have to wonder: since "apt-get" seems to be such an important part of Ubuntu, isn't there a way around this apparent conundrum?
Thanks,
Steve

---

### Post by &amp;KyT$0P# on 2016-08-31
If you haven't admin rights of that system, then no there is no way around it, you have to contact the system administrator.  It's "their machine" and really it's their decision what software gets to be run on it.

That said, if they don't want to install a package, and:
1) the software offers a usable source release or pre-compiled tarball,
2) all pre-requisites are already installed on the machine, **and**
3) the admin is OK with you using the source/tarball for your user account only...


But, again, either way, you need to contact the admin.

---

### Post by steve12342 on 2016-09-01
I used quick reply but do not see my reply today.  While the administrator will allow me to download files, including tar balls; I can't use a command with sudo or apt-get.  But MobaXterm has a package manager that starts installing a package with "/bin/apt-cyg install <package name>."  The administrator allows this.  And I used Moba to install nano, for instance.

---

