---
title: "Command redirection help"
date: 2008-06-01
forum: General Help
---

### Post by abracadaver on 2008-06-01
I have googled and experimented, but can't get any love.  I'm trying to figure an easy way to remove kde4 since 'apt-get autoremove kubuntu-kde4-desktop' only removes the metapackage.  Here is what I think should work but doesn't remove anything:

apt-cache pkgnames | grep kde4 | sudo apt-get autoremove

Any help?

Thanks!
-Shawn

---

### Post by issih on 2008-06-01
With a bit of luck just:

"sudo apt-get autoremove" all on its own will sort you out.

Apt-get should now keep track of what is installed as a dependency. and once you remove the parent package, autoremove should be able to purge anything not referenced by an installed package any more.

Thats the theory anyway...

---

### Post by abracadaver on 2008-06-01
> **issih said:**
> With a bit of luck just:

"sudo apt-get autoremove" all on its own will sort you out.

Apt-get should now keep track of what is installed as a dependency. and once you remove the parent package, autoremove should be able to purge anything not referenced by an installed package any more.

Thats the theory anyway...

No luck.  I've read that it is because I installed with apt instead of aptitude which would uninstall all dependencies of the metapackage.  I tried installing again with aptitude and then removing, but no joy there either.

I'm reading through xargs manpage now, but any gurus are welcome to help :-)

Thanks!
-Shawn

---

### Post by abracadaver on 2008-06-01
> **abracadaver said:**
> I have googled and experimented, but can't get any love.  I'm trying to figure an easy way to remove kde4 since 'apt-get autoremove kubuntu-kde4-desktop' only removes the metapackage.  Here is what I think should work but doesn't remove anything:

apt-cache pkgnames | grep kde4 | sudo apt-get autoremove

Any help?

Thanks!
-Shawn

So this seemed to work.

apt-cache pkgnames | grep kde4 | xargs sudo apt-get -y autoremove

-Shawn

---

### Post by issih on 2008-06-01
That certainly was the case, and the major difference between apt and aptitude, but as I understand things apt was improved fairly recently, it certainly seems to work for me on hardy heron, merrily removing things automagically.

Are you running an older version?, am I totally misinformed?

---

### Post by abracadaver on 2008-06-01
> **issih said:**
> That certainly was the case, and the major difference between apt and aptitude, but as I understand things apt was improved fairly recently, it certainly seems to work for me on hardy heron, merrily removing things automagically.

Are you running an older version?, am I totally misinformed?

I am running a fresh install of Kubuntu Hardy Heron.  I wanted to try out KDE4 so I apt installed kubuntu-kde4-desktop and it installed kde4.  I was able to launch KDE4 and run it, however it is lacking features etc and I saw that 4.1 would be available shortly.

When I do an apt-get remove kubuntu-kde4-desktop or autoremove, it only uninstalls 1 package (kubuntu-kde4-desktop).

-Shawn

---

### Post by abracadaver on 2008-06-02
> **abracadaver said:**
> So this seemed to work.

apt-cache pkgnames | grep kde4 | xargs sudo apt-get -y autoremove

-Shawn

Found this other thread.

[http://ubuntuforums.org/showthread.php?p=5097772#post5097772](http://ubuntuforums.org/showthread.php?p=5097772#post5097772)

-Shawn

---

### Post by mcduck on 2008-06-02
```
sudo apt-get remove kde4 && sudo apt-get autoremove
```
(Replace "kde4" with the name of the package you used when you installed kde4)

When running "apt-get autoremove" you don't need to give it any additional information, it will automatically remove everything that was installed as dependencies for some other package if the original package has been uninstalled.

---

### Post by abracadaver on 2008-06-02
> **mcduck said:**
> ```
sudo apt-get remove kde4 && sudo apt-get autoremove
```
(Replace "kde4" with the name of the package you used when you installed kde4)

When running "apt-get autoremove" you don't need to give it any additional information, it will automatically remove everything that was installed as dependencies for some other package if the original package has been uninstalled.

No.  That was the original problem.  It removes the 1 package only:

$sudo apt-get remove kubuntu-kde4-desktop && sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  kubuntu-kde4-desktop
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 32.8kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 173174 files and directories currently installed.)
Removing kubuntu-kde4-desktop ...
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

-Shawn

---

### Post by mcduck on 2008-06-02
> **abracadaver said:**
> No.  That was the original problem.  It removes the 1 package only:

$sudo apt-get remove kubuntu-kde4-desktop && sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  kubuntu-kde4-desktop
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 32.8kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 173174 files and directories currently installed.)
Removing kubuntu-kde4-desktop ...
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

-Shawn

That's only the output for the first part of the command. If that's all you get the "apt-get autoremove" wasn't even executed yet.

---

### Post by abracadaver on 2008-06-02
> **mcduck said:**
> That's only the output for the first part of the command. If that's all you get the "apt-get autoremove" wasn't even executed yet.


May be, but then I ran this and got this.  Should be the same:

$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

-Shawn

---

