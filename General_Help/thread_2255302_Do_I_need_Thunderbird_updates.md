---
title: "Do I need Thunderbird updates?"
date: 2014-12-04
forum: General Help
---

### Post by Sleepy-zz-John on 2014-12-04
Hi,
     I use SeaMonkey,  not Thunderbird,  but I get a lot of Thunderbird updates which usually accompany Firefox updates which I do need.

Since these Thunderbird updates use up quite a bit of time and bandwidth,  I'm wondering whether I really need them,  and it not,  how should I cancel them?

I believe there's quite a lot of commonality between SeaMonkey and Thunderbird.   Would cancelling Thunderbird updates have any adverse effect on my SeaMonkey, I wonder?

---

### Post by vasa1 on 2014-12-04
What does
```
apt-cache policy thunderbird

```show?

I don't have thunderbird installed and I see this:
```
thunderbird:
  Installed: (none)
  Candidate: 1:31.3.0+build1-0ubuntu0.14.04.1
  Version table:
     1:31.3.0+build1-0ubuntu0.14.04.1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:24.4.0+build1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```If you have thunderbird installed, get rid of it by running
```
sudo apt-get purge thunderbird
```

---

### Post by deadflowr on 2014-12-04
^^Agreed.
If you don't use thunderbird, you don't have to have it installed.

I use it on one machine, and on another I don't.
On the other I removed it, plain and simple.
Haven't had any issues.

You might also want to remove the .thunderbird hidden folder, if there is one, in you home folder.

As far as I know thunderbird and seamonkey are completely separate from one another and have no bearing if one or the other is not installed, or is installed.

---

### Post by Sleepy-zz-John on 2014-12-04
> **vasa1 said:**
> What does
```
apt-cache policy thunderbird

```show?  Thanks vasa1.   It shows 
```
 thunderbird:
  Installed: 1:31.3.0+build1-0ubuntu0.12.04.1
  Candidate: 1:31.3.0+build1-0ubuntu0.12.04.1
  Version table:
 *** 1:31.3.0+build1-0ubuntu0.12.04.1 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
        100 /var/lib/dpkg/status
     11.0.1+build1-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages 
```
So in my case it's all up-to date as a result of recent unnecessary downloads.  Seems it came as a default installation together with Firefox some while ago when I upgraded to Precise >  If you have thunderbird installed, get rid of it by running
```
sudo apt-get purge thunderbird
```
Right!   Many thanks.  Looks like that's what I should do now.

---

### Post by Sleepy-zz-John on 2014-12-05
Thanks for the confirmation Deadflowr.   I was being cautious because once,  quite a while ago when I decided to remove the default e-mail programme that came with Firefox (forgot its name but it was the predecessor to Thunderbird),  it caused me all sorts of problems.   Seems that at that time,  many of the files supposedly only a part of the e-mail programme were actuallydependencies shared by other programmes and their removal ended up breaking my desktop  :(     Hopefully we've all progressed beyond those kind of dependency anomalies these days!    Anyway I'll still keep my fingers crossed as I remove Thunderbird  :)

---

### Post by vasa1 on 2014-12-05
> **Sleepy-zz-John said:**
> ...
So in my case it's all up-to date as a result of recent unnecessary downloads.  Seems it came as a default installation together with Firefox some while ago when I upgraded to Precise 
Right!   Many thanks.  Looks like that's what I should do now.
When you upgrade, all previous software (installed from the software center and not from ppas or elsewhere) existing on your system is upgraded if such software is present in the repositories for the version you're upgrading to. So, at some time you or someone with access to your computer and your login password *did* install t'bird.

---

### Post by deadflowr on 2014-12-05
If ever in doubt about whether or not a package you want to remove might also pull dependencies for other packages, you can use the -s(--simulate) flag in the apt-get command.
Something like
```
sudo apt-get purge -s <packagenamehere>
```
It'll then simulate what changes would happen, but not actually do those changes.
Luckily though, Mozilla apps tend to be more independent than most.

---

### Post by vasa1 on 2014-12-05
I forget whether t'bird was ever a default in Ubuntu. If you've been upgrading for a long time it's possible that that's how t'bird got in without you actually installing it.

---

### Post by deadflowr on 2014-12-05
> **vasa1 said:**
> I forget whether t'bird was ever a default in Ubuntu. If you've been upgrading for a long time it's possible that that's how t'bird got in without you actually installing it.

I think tbird been the default email client since 11.10.
But it definitely is the default for 12.04 and up.

If memory serves thunderbird replaced evolution around the same time libreoffice replaced openoffice.
But those changes were not related to each other, rather more coincidental.

Adding: I mean for Ubuntu 'buntu, and not the other 'buntus.
I have no idea about the others, except I think Kubuntu tried thunderbird at one point...

---

### Post by vasa1 on 2014-12-05
> **deadflowr said:**
> ...
But it definitely is the default for 12.04 and up.
...
Yes, it's listed [here]("http://packages.ubuntu.com/precise/ubuntu-desktop"). What confused me is that this thread is labelled with **lubuntu** and I'm not sure that Lubuntu ever included t'bird by default.

---

### Post by Rex Bouwense on 2014-12-05
The current default is Sylpheed.  Since I began using Lubuntu (before official recognition) I have always had to install Thunderbird.  It has never been a default install.

---

