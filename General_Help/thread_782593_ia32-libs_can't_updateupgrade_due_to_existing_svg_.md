---
title: "ia32-libs can't update/upgrade due to existing svg_loader.so from VMware Server"
date: 2008-05-05
forum: General Help
---

### Post by OzzyFrank on 2008-05-05
With this Hardy upgrade, I've managed to get around most things that wouldn't upgrade or update, but this one with **[COLOR="DarkRed"]ia32-libs[/COLOR]** persists:

**[COLOR="DarkSlateGray"]E: /var/cache/apt/archives/ia32-libs_2.2ubuntu10_amd64.deb: trying to overwrite `/usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so', which is also in package vmware-server[/COLOR]**

What's the best solution for this? Cheers

---

### Post by joshsmith on 2008-05-05
the error message explains the problem perfectly, read it!

two packages controlling the same file.
remove vmware
upgrade i32-libs
install vmware

---

### Post by OzzyFrank on 2008-05-05
Er, the error message might explain it perfectly for some... and "read it!" I actually did (including with the exclamation mark). To you that error message might say "This is what you need to do" but to me it says "Something is wrong... better ask first before doing something stupid!".

To you, the course may have been absolutely clear, and I must seem like some annoying imbecile, but call me hopeful, I was thinking there might even be a way of fixing this without the need to uninstall both packages in question (or even just vmware)... because to an idiot like me, it seems I could do all that and end up with the same message.

Will accept more suggestions before proceeding... even from other Ubuntu Nazis.

---

### Post by OzzyFrank on 2008-05-05
Yup... did the suggested, knowing I should really wait for people with knowledge to comment on this, and while ia32 upgraded OK, now I get this error when trying to reinstall vmware:

E: /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_amd64.deb: subprocess pre-installation script returned error exit status 1

OK, so mark it for complete removal and try again... VMware now installs, but:

E: /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_amd64.deb: trying to overwrite `/usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so', which is also in package ia32-libs

OK, I've read it... oh, ok, so I just now unistall ia32, then reinstall vmware... then uninstall vmware and reinstall ia32, then...

Anyone know the _real_ answer to this dilemma??

---

### Post by OzzyFrank on 2008-05-05
I thought I'd see what renaming svg_loader.so would do, and it does nothing... even though technically the file is no longer in the folder, I still get the message:

E: /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_amd64.deb: trying to overwrite `/usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so', which is also in package ia32-libs

What can I do to get out of this loop of uninstalling and reinstalling both of them?

---

### Post by joshsmith on 2008-05-06
hey,
sorry if i came off bad, it really wasnt intentional, although i dont know if it was nazi level :)

i'll try and explain what is happening:
the package manager is really cool. it stores a list of all files own by a package (you can see it in synaptic with right clikc>show installed files). when  you install a package it puts all these files onto the disk. when you remove a package it gets rid of them all. when you upgrade a package it gets rid of all the old ones and puts all the new ones (for security fixes this will generally be the same set of files, but for bigger upgrades the file list changes). all of this ensures you can never have an inconsistent hard drive state, and also programs can leave junk behind when you install them as the package manager controls it all.
you cant have 2 programs controlling the same file, as what would the package manager do when you got rid of one of them.
i was hoping you were stuck in a version change where from old version to new version the control of the file svg_loader.so moved from one package to the other,, meaning you would have to uninstall both, and reinstall (if it did it in the wrong order) but that wasnt the case

are you installing vmware from the official ubuntu repos. there shouldnt be any conflicting packages there.
if you are using a third party repo, they are doing something wrong and should maybe be notified about the incompatibility.  or ubuntu guys should be probably be told if it is just their packages. file a bug

however, for the immediate problem, check this thread:
[http://ubuntuforums.org/showthread.php?t=670029](http://ubuntuforums.org/showthread.php?t=670029)
which shows how you can force the packages to install

---

### Post by OzzyFrank on 2008-05-06
I'm definitely using the Ubuntu repo packages, since there are no 64-bit versions from VMware, and the i386 ones won't install (ie without being forced). I originally wanted to use the latest, but gave in and installed via Synaptic. Yes, I would have thought there'd be no conflicts doing it this way, too.

This might be worthy of filing a bug, but I don't know where to do that, so will look around later when I have some time (if anyone knows the link, please supply it).

That page regarding forced installs is good, so will have to sit down and have a good read through when I can and try to utilise that. The fact it has steps to take when the **-f** option fails looks promising.

---

### Post by OzzyFrank on 2008-05-08
Using the info from that link, I tried:

**[COLOR="DarkRed"]sudo dpkg -i --force-overwrite /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so[/COLOR]**

but instead of a promising result, it spat out:

[B][COLOR="Indigo"]dpkg-deb: `/usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so' is not a debian format archive
dpkg: error processing /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so[/COLOR][/B]

so therefore using **sudo apt-get -f install** afterward as suggested didn't work.

---

### Post by OzzyFrank on 2008-05-08
OK, I tried another approach and it worked (though it still complains):

**[COLOR="DarkRed"]sudo dpkg -i --force-overwrite /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_amd64.deb[/COLOR]**
[COLOR="Blue"](Reading database ... 196194 files and directories currently installed.)
Unpacking vmware-server (from .../vmware-server_1.0.4-1gutsy2_amd64.deb) ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so', which is also in package ia32-libs
**Setting up vmware-server (1.0.4-1gutsy2) ...**[/COLOR]

---

### Post by joshsmith on 2008-05-08
before you read the following, are you sure you are using just the gutsy repos. do you have third party repos (check in system>admin>software sources) it is just a bit weird that one of the packages ends with -gutsy and the other with -ubuntu. do you have the proposed or backports repo enabled. nobody else on the internet seems to have this problem, so my guess is you have some other repo enabled



yeah that is the expected output. i really meant this line:
"sudo dpkg -i --force-overwrite /var/cache/apt/archives/libmpeg3hv_1%3a2.1.0-1svn20080102akirad1_i386.deb"

so if it gives you this error:
E: /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_amd64.deb
do 
sudo dpkg -i --force-overwrite /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_amd64.deb

EDIT: i see you already know this bit. but still check your repos

---

### Post by joshsmith on 2008-05-08
ok i was stupid,  i wasnt paying attention reading this thread. 

the real issue is this:
you are now using hardy, but you are installing an old package from gutsy.
this = bad, and you should change to a hardy package straight away

my original advice should have been 
remove vmware
upgrade ia32-libs
install vmware (but a hardy verion, and you wont have any more problems)

---

### Post by OzzyFrank on 2008-05-08
OK, seems that it didn't install prooperly or something, as VMware Server wouldn't load. I tried to do a reinstallation via Synaptic, but it returned a generic sub post whatever message. Here is the last bit from the terminal from what I assumed was a successful install:

[COLOR="Blue"]Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.[/COLOR]

Any ideas?

---

### Post by OzzyFrank on 2008-05-08
> **joshsmith said:**
> ok i was stupid,  i wasnt paying attention reading this thread. 

the real issue is this:
you are now using hardy, but you are installing an old package from gutsy.
this = bad, and you should change to a hardy package straight away

my original advice should have been 
remove vmware
upgrade ia32-libs
install vmware (but a hardy verion, and you wont have any more problems)

I did the uninstall of vmware and upgrade of ia32 at the beginning. I have no idea why it wants Gutsy packages... I mean, even though I still have some Gutsy repos in there, they are mostly official, and they should by rights be ignored by Ubuntu in favour of Hardy ones.

I just removed all the Gutsy repos, and then removed vmware, but this is what I got when trying to reinstall it through Synaptic:

**[COLOR="#4b0082"]Could not mark all packages for installation or upgrade[/COLOR]**

[COLOR="Indigo"]The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.[/COLOR]

[COLOR="Blue"]vmware-server:

Package vmware-server has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list[/COLOR]

And yes, I did do something to deserve all this: I hit the Upgrade button! (Besides that, all I did was trust Ubuntu to upgrade, update and install stuff without a big balls up... not like I deleted the Hardy entries in sources.list - that I had to create as the upgrade didn't!! - and told it to use the Gutsy ones!)

---

### Post by OzzyFrank on 2008-05-08
And for the terminal again:

**sudo apt-get -f install vmware-server**
[COLOR="Blue"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vmware-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package vmware-server has no installation candidate[/COLOR]

This is becoming a drag, hehehe....

---

### Post by joshsmith on 2008-05-08
ok you cant expect old third party gutsy repos to be supported by ubuntu hardy. it is up to them to change, and they wont change the gutsy ones but will make new repos for hardy

so your new error messages make sense, you have remove the repo for vmware-server so now there is no place to get it from

you need to add a hardy repo (a possible way to do this is to go into software sources > third party software and edit each of the entries and change the gutsy bit to hardy)

simplest bet, disable gutsy repos in hardy unless you know what your doing. they are not designed to be necessarily compatible. you need hardy repos, or find the packages you were getting from third parties from the official repos. 

your problems arent really ubuntus fault. upgrade your third party repos to hardy, and if none exist, in general, get rid of them

edit: 
in response to "I have no idea why it wants Gutsy packages... I mean, even though I still have some Gutsy repos in there, they are mostly official, and they should by rights be ignored by Ubuntu in favour of Hardy ones."
it uses gutsy repos if these are the only ones available. if you haven't give it a hardy repo you cant expect it to use the hardy version.  when using third party repos, it is up to you to look after them through upgrades, which generally (for good repos) means just changing the word gutsy to hardy

---

### Post by OzzyFrank on 2008-05-08
First off, I didn't realise a third party repo was needed for vmware. When I first installed it back in Edgy or Feisty I did it with the standard repos, or at least didn't manually add any to achieve this.

As for it not being Ubuntu's fault, well let's say the fact that before, during and after the upgrade no Hardy repos were ever added to my sources.list is not **my** fault. I made a copy of all the repos, changed the Gutsy to Hardy... and now I've disabled the Gutsy ones... or should I have just left it the way Ubuntu did after getting Hardy? (seriously... there was not one Hardy in sight in my sources.list)
[COLOR="Purple"]
"if you haven't give it a hardy repo you cant expect it to use the hardy version[/COLOR]" - Dude, I am _stressing_ here that I have added Hardy versions of all the repos, whether they actually exist or not! Gutsy ones were disabled when I got the last error. If Hardy vmware is for some reason on some new Hardy repo I don't have, someone please pass along the link.

---

### Post by OzzyFrank on 2008-05-08
Glad you guys don't have this problem... and it gets weirder. Now, I've deleted all mention of "gutsy" from sources.list, yet in Software Sources 2 repos, both Medibuntu ones, were still "gutsy". Also, there are 2 references to **WineHQ** which don't appear in sources.list. Are there other sources/repo files I should know about? Obviously there has to be, more info on this would be welcome. Anyway, none of this would be affecting vmware, but in case you need to ask, yes I did change the Medibuntu one to hardy.

Since I removed the Gutsy repos, wmware has disappeared from Synaptic... only the 2 vmware-server-kernel packages remain.

Never seen anything like this, hehe! And in response to having 2 versions of each repo before, ie Gutsy and Hardy, never had any problems doing that previously, and do that since you can still get updates for apps that haven't caught up (and therefore don't have the latest repo). Never had _any_ conflict of any kind before, and I am sure this doesn't explain why vmware is now missing from my world now that the Gutsy repos have been deleted.

Goggled and found a Feisty tutorial so modified the address and tried that:

[COLOR="DarkRed"]deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy-commercial main[/COLOR]

but updating in the terminal I get:

[COLOR="Blue"]W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy-commercial/main/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/hardy-commercial/main/binary-amd64/Packages.gz)  404 Not Found[/COLOR]

Looking around, I see people asking about Hardy vmware:

[COLOR="DarkRed"]Is there any chance the VMWare Server package will be in the repos for Hardy x64?

Or a simple howto?[/COLOR]

... and the Feisty repo address I converted (above) was from a tutorial in the time of Gutsy that said you had to use the Feisty repo as there wasn't a Gutsy version yet.

Damn, I had a working VMware Server till all this crap with ia32 and removing vmware to try and fix things. That's why I really wanted to hold off uninstalling it, coz I had a feeling it would cause more grief than it fixed, hehe. Next suggestions? Working repos would be welcome too!

---

### Post by OzzyFrank on 2008-05-08
More Hardy-VMware hell from forums etc:

[COLOR="DarkRed"]I've googled the problem with VMWare server for Hardy. Are there plans to make VMWare Server avaliable in the repos as per Gutsy? I'm running Hardy x64 RC on Sun, April 20 (fresh install).[/COLOR]
[COLOR="Blue"]I really don't think so... this time Canonical is sponsoring VirtualBox.[/COLOR]

[COLOR="DarkRed"]Any chance that vmware-server will be supported on Hardy? Currently there isn't even a package for Gutsy, yet it was supported on Feisty with the ubuntu commercial repos and easily installable.[/COLOR]
[COLOR="Blue"]At the moment is it not possible to complie the vmware modules in hardy.. was anybody successful?[/COLOR]

[COLOR="DarkRed"]Apparently kernel 2.6.23 introduced a change that severely breaks VMware Server. See [http://servervirtualization.blogs.techtarget.com/2007/10/10/linux-kernel-2623-win-for-xen-and-kvm-and-a-loss-for-vmware/](http://servervirtualization.blogs.techtarget.com/2007/10/10/linux-kernel-2623-win-for-xen-and-kvm-and-a-loss-for-vmware/)[/COLOR]

I might try this (it's compiling it, but even that hasn't worked for some with Hardy from what I have seen - hopefully this tutorial works):

**vmware-server in hardy**
[http://ubuntuforums.org/showpost.php?p=4357442&postcount=10](http://ubuntuforums.org/showpost.php?p=4357442&postcount=10)
or
[http://users.piuha.net/martti/comp/ubuntu/en/server.html](http://users.piuha.net/martti/comp/ubuntu/en/server.html)

... but I am gonna hold off till I am sure there are no repos I am missing that would fix it.

---

### Post by OzzyFrank on 2008-05-08
This is from an article dated May 3:

[COLOR="DarkRed"]Now that most of the modern world has upgraded to Ubuntu 8.04 I&#8217;ve begun to see comments regarding VMware Server no longer working.  You may have used my previous article, Installing VMware Server on Ubuntu 7.10, which has worked great.  Now that 8.04 &#8220;Hardy&#8221; is installed things have become a bit more complicated unfortunately.

The problem is that VMware has not updated their latest versions to make use of the latest kernel, GCC or gnome libraries.  So, we&#8217;ve got two options.

1. Wait for a new VMware release and hope they patch everything.
2. Follow the rest of this tutorial and get your hands dirty on the terminal.  We can make it work, but we have to hammer it into submission.[/COLOR]

For the tutorial in full:

[http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/)

---

### Post by OzzyFrank on 2008-05-12
So nobody know of a repo I can add that will get me a version of VMware suitable for 64-bit Hardy? Having removed the Gutsy repos Synaptic still doesn't see a "vmware-server" anywhere.

---

