---
title: "How can I report a malformed package?"
date: 2024-10-22
forum: General Help
---

### Post by Acharn on 2024-10-22
I need to install git. When I try to install git, apt tries to install emacs-common. When it tries to install emacs-common, it fails:
```

$ sudo apt install emacs-common
[sudo] password for roger: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Suggested packages:
  emacs-common-non-dfsg ncurses-term
The following NEW packages will be installed:
  emacs-common
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
16 not fully installed or removed.
Need to get 0 B/16.1 MB of archives.
After this operation, 80.0 MB of additional disk space will be used.
(Reading database ... 361468 files and directories currently installed.)
Preparing to unpack .../emacs-common_1%3a29.3+1-1ubuntu2+esm1_all.deb ...
Unpacking emacs-common (1:29.3+1-1ubuntu2+esm1) ...
[B]dpkg: error processing archive /var/cache/apt/archives/emacs-common_1%3a29.3+1-1ubuntu2+esm1_all.deb (--unpack):
 trying to overwrite '/usr/include/emacs-module.h', which is also in package emacs28 28.1~1.git5a223c7f2e-kk3+22.04
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)[/B]
Errors were encountered while processing:
 /var/cache/apt/archives/emacs-common_1%3a29.3+1-1ubuntu2+esm1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
How can I report this? Normal bug reporting refuses to accept it because the package is not installed. The problem is in the package in the repository. Someone maintains the repositories. How can I find out who? Or is there a single email address to send problems to? Please help me.

---

### Post by ian-weisser on 2024-10-22
Looks like you have emacs packages from two different sources, and those packages are incompatible.

If all your emacs packages are from the same source, the problem is very likely to vanish.

---

### Post by davetheoldcoder on 2024-10-22
> When I try to install git, apt tries to install emacs-common.

That's odd. In Ubuntu 24.04.1, emacs-common is not a dependency for git.

---

### Post by Acharn on 2024-10-23
I don't have packages from two different sources. The package for emacs 29.4 is trying to overwrite something from the package for emacs 28.1. I had a terrible time trying to uninstall emacs 28. Has anybody successfully installed emacs 29.4 in the last couple of days? Who maintains the package repositories, and how can I contact them?

Or, if you're right, how do I uninstall completely emacs 29.4, get all packages from the same repository, and install them with their dependencies?

---

### Post by Acharn on 2024-10-23
Yes, I agree it's strange. I have no idea what's going on with that.
```

sudo apt install git
[sudo] password for roger: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 emacs-bin-common : Depends: emacs-common (= 1:29.3+1-1ubuntu2+esm1)
 emacs-el : Depends: emacs-common (= 1:29.3+1-1ubuntu2+esm1)
 emacs-gtk : Depends: emacs-common (= 1:29.3+1-1ubuntu2+esm1)
 git : Depends: liberror-perl but it is not going to be installed
       Depends: git-man (> 1:2.47.0) but it is not going to be installed
       Depends: git-man (< 1:2.47.0-.) but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

I've tried 'sudo apt --fix-broken install' and it fails because it tries to install emacs-common.

---

### Post by deadflowr on 2024-10-23
emacs28 is from the emacs ppa.
Ubuntu has never packaged an emacs28.
Ubuntu only packages emacs.
Whose version may or may not be related to 28 or 29 or whatever.

You got emacs28 from here: [https://launchpad.net/~kelleyk/+archive/ubuntu/emacs](https://launchpad.net/~kelleyk/+archive/ubuntu/emacs)

Not a bug.
This is something you need to fix yourself.

nothing will be installable until you fix the emacs issue.

You stated you've tried removing emacs28, but how?

---

### Post by Acharn on 2024-10-23
First, I tried 'sudo apt remove emacs,' then I tried 'sudo snap remove emacs' (I've since learned I didn't need 'sudo' there). Then I tried 'sudo dpkg -r emacs,' then I went to synaptic package manager and marked everything related to emacs for removal. By the way, there is no entry for emacs-module.h in my /usr/include directory. I've now removed emacs 29.4 from my computer, but I'm still getting the same error message when I try to reinstall emacs.

---

### Post by yancek on 2024-10-23
>   I've now removed emacs 29.4 from my computer, but I'm still getting the same error message when I try to reinstall emacs. 				

In post 6, it was suggested you remove emacs28 and you removed 29?  You were asked in that same post how you tried to remove emacs28 but did not answer.  emacs28 is from a ppa so you need to remove that.  Check in /etc/apt/sources.list.d directory to see if you have a ppa for emacs 28.  Then try the suggestions at the link below.

[https://www.omgubuntu.co.uk/2019/12/how-to-remove-ppa-ubuntu](https://www.omgubuntu.co.uk/2019/12/how-to-remove-ppa-ubuntu)

---

### Post by Acharn on 2024-10-24
I'm sorry, the first part of my reply at #7 describes how I removed emacs 28. It was several days later that I removed emacs 29, which I cannot reinstall. I've decided to just reinstall ubuntu 24.04.1. I'm retired, and I'm old, and I have all the time in the world and no very valuable data.

---

### Post by davetheoldcoder on 2024-10-24
I've been using emacs as my primary text editor for a long time. But when I installed Ubuntu 24.04, I had a couple of annoying issues with emacs that I was unable to solve. I finally gave up and switched to gnome-text-editor. :sad:

---

### Post by deadflowr on 2024-10-24
> **Acharn said:**
> I'm sorry, the first part of my reply at #7 describes how I removed emacs 28. It was several days later that I removed emacs 29, which I cannot reinstall. I've decided to just reinstall ubuntu 24.04.1. I'm retired, and I'm old, and I have all the time in the world and no very valuable data.

I guess if you reinstalled the point is now moot.
But for the record you removed emacs which is not emacs28.
Those are 2 completely different packages.

---

### Post by Acharn on 2024-10-24
> **davetheoldcoder said:**
> I've been using emacs as my primary text editor for a long time. But when I installed Ubuntu 24.04, I had a couple of annoying issues with emacs that I was unable to solve. I finally gave up and switched to gnome-text-editor. :sad:
I've become enamored of emacs, and really want to succeed in configuring a working copy. It's been very difficult, because I have no real reason to use a fancy editor like this. Open Office does everything I really need, and easier (that might change as I master emacs). Right now I'm unable to backup my /home directory, but I'm willing to abandon my current installation. I've got plenty of time on my hands, and very little important data.

---

