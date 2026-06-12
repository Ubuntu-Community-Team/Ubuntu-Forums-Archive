---
title: "The best distro to use on enviorment headless and only run scripts"
date: 2016-10-20
forum: General Help
---

### Post by sed_faster on 2016-10-20
Hello,

I pretend create a machine headless for only run scripts! I think use Ubuntu Server, but this is the best option? Exist another system more light? Because the purpose is run script which do mathematical calculations. Sum, Division and Modules!

My knowledge about word gnu/linux is on Lubuntu and Ubuntu! Therefore only system debian!

Notice: I pretend access on this machine through my laptop via ssh, in port RJ-45. For this I think will set IPtables, because I pretend limited the access via this environment!

---

### Post by TheFu on 2016-10-22
Please check the translation of "pretend" - don't think it is being used the way you intend.  Not sure I understand the intent, so correcting that would be helpful.

"Best" is highly subjective, so it is impossible to say what the best server distro is.  There are lighter distros, there are rpm-based distros, there are more specific distros for different tasks.  The issue with lighter distros is that commonly used tools aren't pre-installed. Either you do without those tools or install each as needed, so the lighter distro gets a little heavier.  

Sometimes the lighter distros don't include all the device drivers necessary too. That can be a hassle.  For example, my NIC isn't supported by mini-Ubuntu so manually getting the correct driver and installing it is a hassle. What really sucks is that during the install, the correct driver **is** available, but not at first boot.

---

### Post by papibe on 2016-10-22
Hi Edgar_Oliveira.

Any distro that allow you a no GUI version would do. Ubuntu Server 16.04.1 would work just fine.

You also have to consider what language, and version, you want to use. Check the availability of what you want in the repositories.

For instance, let's say you want to use the R language in Ubuntu. Start here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) looking for the r-base package, and you have this: [http://packages.ubuntu.com/xenial/r-base](http://packages.ubuntu.com/xenial/r-base) (version 3.2.3-4).

If the version is behind of what you want, search for ppa's or other easy way to install new versions (like [this]("https://cran.r-project.org/bin/linux/ubuntu/README.html") for R).

Lastly, if even that is too behind your needs, you may need to look either for a distribution closer to upstream, say like arch, or a way to compile and install your software.

Just some thoughts. Let us know how it goes.
Regards.

---

