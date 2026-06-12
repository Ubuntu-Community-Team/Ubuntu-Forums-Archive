---
title: "List of kernels"
date: 2021-05-04
forum: General Help
---

### Post by linerman on 2021-05-04
Hi,

I am quite confused regarding my installed kernels.
I would like to know how many kernels Ubuntu has as a default number (3?).

```
dpkg --list | grep linux-image
rc  linux-image-5.4.0-42-generic                5.4.0-42.46                          amd64        Signed kernel image generic
rc  linux-image-5.4.0-58-generic                5.4.0-58.64                          amd64        Signed kernel image generic
rc  linux-image-5.4.0-59-generic                5.4.0-59.65                          amd64        Signed kernel image generic
rc  linux-image-5.8.0-34-generic                5.8.0-34.37~20.04.2                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-36-generic                5.8.0-36.40~20.04.1                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-38-generic                5.8.0-38.43~20.04.1                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-40-generic                5.8.0-40.45~20.04.1                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-41-generic                5.8.0-41.46~20.04.1                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-43-generic                5.8.0-43.49~20.04.1                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-44-generic                5.8.0-44.50~20.04.1                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-45-generic                5.8.0-45.51~20.04.1+1                amd64        Signed kernel image generic
rc  linux-image-5.8.0-48-generic                5.8.0-48.54~20.04.1                  amd64        Signed kernel image generic
ii  linux-image-5.8.0-49-generic                5.8.0-49.55~20.04.1                  amd64        Signed kernel image generic
ii  linux-image-5.8.0-50-generic                5.8.0-50.56~20.04.1                  amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04               5.8.0.50.56~20.04.34                 amd64        Generic Linux kernel image


```

Is this list of all my installed kernels (mean - take space of HDD)? If yes, than to me it looks too much. 
I guess, three would be enough.
I do not have any problems with 5.8 ver, so one 5.4 and two 5.8 would do a thing, am I right?

Also, I though that command "apt-get autoremove" does remove all of the kernels apart from last 3 (or 5?). But it did not. I ran a command couple of times and still the list looks like above.
Anyone could help me with that mess?

---

### Post by tea for one on 2021-05-04
Have a close look at the beginning of each line of your output.

rc= removed (some configuration files remain)
ii  = installed

Here is another way to find installed kernels:-
```
ls /boot | grep vmlinuz-

```

---

### Post by deadflowr on 2021-05-04
The only installed kernels are the one listed as ii.
All rc listings mean no kernel installed, however their are still leftover config files on the system.
You can clear those out with a quick one-liner like this
```
dpkg -l | awk '/^rc/{print $2}' | xargs sudo apt purge -y
```

The autoremove command works like the remove command, as it removes packages but doesn't remove config files.
The alternative purge command does remove those so
```
 sudo apt remove <package>
```
removes the package but keeps configs,
and
```
sudo apt purge <package>
```
removes the package and removes all related configs.
and 
```
sudo apt autoremove
```
removes just like remove does, and also leaves configs like remove does.
but
```
sudo apt autoremove --purge
```
will remove the packages and any leftover configs.

hope that helps.

---

### Post by tea for one on 2021-05-04
> **deadflowr said:**
> 
You can clear those out with a quick one-liner like this
```
dpkg -l | awk '/^rc/{print $2}' | xargs sudo apt purge -y
```

I like this one - very succinct

---

### Post by deadflowr on 2021-05-04
> **tea for one said:**
> I like this one - very succinct

I kind of modified it from what I learned from this: [http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/]("http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/")
I found I could drop specific package listings (like dpkg -l linux*) and just list everything with plain empty dpkg -l, and I could simply replace the ^ii with ^rc and cut out the running kernel section, more or less.

For what it's worth there are plenty of ways to remove old kernels.
autoremove is simply the easiest, most of the time.
I ran the commands in the link once upon a time, before autoremove could remove kernels,; it hasn't always been the case.
Then I discovered [purge-old-kernels]("http://manpages.ubuntu.com/manpages/xenial/man1/purge-old-kernels.1.html") which was in the bikeshed package, but has since been moved into the byobu package.
DougS also found another option he posted here about: [https://ubuntuforums.org/showthread.php?t=2452692&p=14003294#post14003294]("https://ubuntuforums.org/showthread.php?t=2452692&p=14003294#post14003294").
I think he posted a better more thorough description somewhere else, but I'm not gonna dig for it.

Oh, and of course their is always the old standby of manually typing in the full names of each kernel to remove.
(But who would ever need to do that, right?)

---

### Post by ajgreeny on 2021-05-04
I have to admit that I prefer to do things in a more manual way because I prefer to keep a very close eye on all updates and upgrades, including kernels.

I have also occasionally found that the autoremove command wants to remove a few packages that I have installed as they were needed by something I have installed from a source other than the standard repos, eg get-iplayer where the repository version did not work well, or didn't work at all.

I use terminal to update with aliases in my ***~/.bash_aliases*** of
```
alias ud='sudo apt update && apt list --upgradable'
alias ug='sudo apt full-upgrade'
```
The first checks repos and then lists every package that will be upgraded so I can quickly see if a new kernel is coming; the second carries out the upgrade.
If a new kernel is coming I will run ```
sudo apt autoremove --purge -s
```
This shows all packages that will be purged when I run it again without the -s option (simulate), allowing me to ensure that nothing I want to keep is to be removed.

Finally if I need to remove a older unneeded kernel version I first check those installed with ***ls /boot | grep vmlinuz*** as shown by **tea for one** above and then remove the unwanted version of the three with, for example ***sudo apt purge *5.4.0-70**** which will also remove the no longer needed header and tools packages of the same version.

This may all sound complicated but I'm so used to doing it that it is much quicker than any other method that I have used in the past and it means I have full and total control of everything.

---

### Post by deadflowr on 2021-05-04
> Then I discovered purge-old-kernels which was in the bikeshed package, but has since been moved into the byobu package.
I guess purge-old-kernels has been deprecated in the latest releases: [https://bugs.launchpad.net/ubuntu/+source/byobu/+bug/1686138]("https://bugs.launchpad.net/ubuntu/+source/byobu/+bug/1686138")

As I posted lots of methods out there to fully remove old kernels.
Some quick and easy and some long arduous and mildly annoying.

FWIW,
As far as autoremove wanting to remove other packages, you can set them with *apt-mark manual <package-name>* to prevent that from happening to them.

---

### Post by ajgreeny on 2021-05-04
> **deadflowr said:**
> < SNIP >

FWIW,
As far as autoremove wanting to remove other packages, you can set them with *apt-mark manual <package-name>* to prevent that from happening to them.
Oh boy!
I have to say that is one of the uses of apt and autoremove that I had not caught up with; it will be extremely useful once I have noted something I want or need to keep installed.

I should have known Linux would have a way to do something as simple(?) as that!!  Many thanks deadflowr.

---

### Post by Dennis N on 2021-05-04
If you use "unattended-upgrades" for your Security Updates, it automatically removes old kernel versions to keep 3.
To see installed kernels, Synaptic Package Manager is helpful. You could also use Synaptic Package Manager to remove sets of old kernel packages. See this for outline of the removal method:
[https://ubuntuforums.org/showthread.php?t=2417139&p=13853344#post13853344](https://ubuntuforums.org/showthread.php?t=2417139&p=13853344#post13853344)

---

### Post by ajgreeny on 2021-05-05
I always disable unattended upgrades as I much prefer to do things at my own time rather than the OS's choosing.

I do use synaptic occasionally but generally only tpo search for and install packages, certainly not any more for updates and upgrades which are better done in terminal, in my opinion, using those aliases shown earlier.

Perhaps I'm just an old fuddy-duddy (old certainly, fuddy-duddy I will leave to others to decide!) but where I can, I like to do things with as much control as is possible and not leave it all to the OS.

---

### Post by Doug S on 2021-05-05
> **deadflowr said:**
> DougS also found another option he posted here about: [https://ubuntuforums.org/showthread.php?t=2452692&p=14003294#post14003294]("https://ubuntuforums.org/showthread.php?t=2452692&p=14003294#post14003294").
I think he posted a better more thorough description somewhere else, but I'm not gonna dig for it.

Yes, I really like [that kernel management tool]("https://code.launchpad.net/linux-purge"), and recommend it. I'll have to dig around also to find if I did a better description of it somewhere else, ha ha. Perhaps [the overview page]("https://launchpad.net/linux-purge"). The problem for some would be that it is a git download. For reasons already covered herein, I do not like to use "autoremove". I pretty much only ever use the --choose option, to select what I want it to do. However, I recently got into some kernel troubles that then prevented updates due to configuration and dependency issues, even this tool with --choose gave up. But using the --fix option instead worked fine, and thereafter I could go back to the --choose option.

EDIT: I had a screen shot and example run [here]("https://ubuntuforums.org/showthread.php?t=2457790&p=14019702#post14019702").

---

### Post by deadflowr on 2021-05-05
> EDIT: I had a screen shot and example run [here]("https://ubuntuforums.org/showthread.php?t=2457790&p=14019702#post14019702").

What's funny is I remember you posted in that thread. What I forgot was that I did too.

---

### Post by linerman on 2021-05-15
Thank you guys for all the anwers and help!

I have learnt a lot :)

I've got two more questions:

1. I did
```
dpkg -l | awk '/^rc/{print $2}' | xargs sudo apt purge -y
```

but that command left some old kernel folders in /lib/modules.

I dig the folder and found that in some I have got Build folders , and in the others there are some external drivers for my ethernet cards (I installed external dkms driver for my eth card)
I assume that these files are old, so may I safety delete all of these files? 
(I am talking about removed kernels folders, not the installed one of course!)

2. I do like linux-purge software. Anyone could provide me a faq how to install from git or where I may read about such process?

---

### Post by Doug S on 2021-05-15
> **linerman said:**
> 2. I do like linux-purge software. Anyone could provide me a faq how to install from git or where I may read about such process?I think you would just have to install the git package. Then use the command listed on the linux-purge code page to create a copy. Then run it. Example:

```
doug@s19:~/ubuntu-forums-example$ git clone https://git.launchpad.net/linux-purge
Cloning into 'linux-purge'...
remote: Enumerating objects: 676, done.
remote: Counting objects: 100% (676/676), done.
remote: Compressing objects: 100% (484/484), done.
remote: Total 676 (delta 270), reused 213 (delta 41)
Receiving objects: 100% (676/676), 101.84 KiB | 318.00 KiB/s, done.
Resolving deltas: 100% (270/270), done.
doug@s19:~/ubuntu-forums-example$ cd linux-purge
doug@s19:~/ubuntu-forums-example/linux-purge$ sudo ./linux-purge --choose
[sudo] password for doug:
```And I'll end up here (older screen shot, re-used here):

---

### Post by TheFu on 2021-05-15
Today, I did a few commands to clean up the last remaining 4.15 kernels, modules, headers on my systems. They are all running a 5.4 kernel now, except 1 which will have the OS upgraded tonight (in theory).

```
dpkg -l 'linux-*-4.15*'
```
provides a list.
```
sudo apt purge 'linux-*-4.15*'
```
purges all the related kernels, headers, and modules for v4.15 kernels.

Clearly, you are expected to look at the list to be purged before answering 'y'.

Both **dpkg** and **apt** support package name globbing similar to what bash supports.

Right now, there are some old 5.4.0.x kernels, headers, modules leaving traces behind, so I'll be a little more selective about the globbing.

```
$ dpkg -l 'linux-*-5*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name             Version       Architecture  Description
+++-================-=============-=============-=====================================
**un**  linux-headers-5. <none>        <none>        (no description available)
ii  linux-headers-5. 5.4.0-72.80~1 amd64         Linux kernel headers for version 5.4.
ii  linux-headers-5. 5.4.0-73.82~1 amd64         Linux kernel headers for version 5.4.
un  linux-hwe-5.4-do <none>        <none>        (no description available)
ii  linux-hwe-5.4-he 5.4.0-72.80~1 all           Header files related to Linux kernel 
ii  linux-hwe-5.4-he 5.4.0-73.82~1 all           Header files related to Linux kernel 
un  linux-hwe-5.4-im <none>        <none>        (no description available)
un  linux-hwe-5.4-so <none>        <none>        (no description available)
un  linux-hwe-5.4-to <none>        <none>        (no description available)
**rc ** linux-image-5.4. 5.4.0-70.78~1 amd64         Signed kernel image generic
ii  linux-image-5.4. 5.4.0-72.80~1 amd64         Signed kernel image generic
ii  linux-image-5.4. 5.4.0-73.82~1 amd64         Signed kernel image generic
un  linux-image-unsi <none>        <none>        (no description available)
un  linux-image-unsi <none>        <none>        (no description available)
un  linux-image-unsi <none>        <none>        (no description available)
**rc**  linux-modules-5. 5.4.0-70.78~1 amd64         Linux kernel extra modules for versio
ii  linux-modules-5. 5.4.0-72.80~1 amd64         Linux kernel extra modules for versio
ii  linux-modules-5. 5.4.0-73.82~1 amd64         Linux kernel extra modules for versio
**rc**  linux-modules-ex 5.4.0-70.78~1 amd64         Linux kernel extra modules for versio
ii  linux-modules-ex 5.4.0-72.80~1 amd64         Linux kernel extra modules for versio
ii  linux-modules-ex 5.4.0-73.82~1 amd64         Linux kernel extra modules for versio
```

See all the lines that don't start with '^ii', those are the ones I want to purge, but only the specific versions, not metapackages. Let's check if a little more specific globbing will work:
```
$ dpkg -l 'linux-***5.4.0-70***'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name             Version       Architecture  Description
+++-================-=============-=============-=====================================
un  linux-headers-5. <none>        <none>        (no description available)
rc  linux-image-5.4. 5.4.0-70.78~1 amd64         Signed kernel image generic
un  linux-image-unsi <none>        <none>        (no description available)
rc  linux-modules-5. 5.4.0-70.78~1 amd64         Linux kernel extra modules for versio
rc  linux-modules-ex 5.4.0-70.78~1 amd64         Linux kernel extra modules for versio
```

Nice. It found what we want, but nothing we don't want.  Time to purge ... 
```
$ sudo apt purge  'linux-***5.4.0-70***'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
... *[COLOR="#00FF00"]{lots of packages not on the system listed here}[/COLOR]*
The following packages will be REMOVED:
  linux-image-5.4.0-70-generic* linux-modules-5.4.0-70-generic*
  linux-modules-extra-5.4.0-70-generic*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 180288 files and directories currently installed.)
Purging configuration files for linux-modules-extra-5.4.0-70-generic (5.4.0-70.78~18.04.1) ...
Purging configuration files for linux-modules-5.4.0-70-generic (5.4.0-70.78~18.04.1) ...
dpkg: warning: while removing linux-modules-5.4.0-70-generic, directory '/lib/modules/5.4.0-70-generic' not empty so not removed
Purging configuration files for linux-image-5.4.0-70-generic (5.4.0-70.78~18.04.1) ...

```

And to check things before rebooting, re-run the initial dpkg cmd.  Checking ... all good. There are a few meta-packages left (doc, source, tools) in the list along with the installed kernel, headers, and modules needed for a working system.  If too many kernels were removed, I'd need to re-install them before rebooting. Always check your efforts.

I suppose the key point is that name globbing on Unix is much more capable than what we learned on MS-DOS.  We can put wildcards in places that MS-DOS/Windows cannot handle.  Also, don't think that a '.' means anything special in Unix. It is just another character, unlike on Windows where it is the beginning of a special "extension."  Unix doesn't have extensions. Humans find them useful, but the OS doesn't care.

---

