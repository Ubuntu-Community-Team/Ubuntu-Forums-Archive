---
title: "Easy way to fix broken packages that works?"
date: 2012-12-02
forum: General Help
---

### Post by taunnt on 2012-12-02
OK I try this:

apt-get install aptitude
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 aptitude : Depends: libapt-pkg4.10
            Depends: libept1 but it is not going to be installed
            Recommends: aptitude-doc-en but it is not going to be installed or
                        aptitude-doc
E: Unable to correct problems, you have held broken packages.

Now for almost everything I try to install I get that error. I tried this:

# apt-get update
# apt-get upgrade
# apt-get install aptitude

and still same error. Can I list the broken packages then just delete those? I'm not liking 12.10 so far. All I get are error messeges. been using Ubuntu sense 9.04. Arg!

---

### Post by mc4man on 2012-12-02
Well this is not what's current in 12.10 so sounds like you did an upgrade vs. fresh install
aptitude : Depends: libapt-pkg4.[COLOR="Red"]10[/COLOR]
(it would be libapt-pkg4.[COLOR="Navy"]12[/COLOR] (apt-0.9.7.5ubuntu5 or 0.9.7.5ubuntu5.1

maybe try 
```
sudo apt-get clean && \
sudo apt-get -s dist-upgrade

```
If above looks ok re-run the dist-upgrade command without the -s (simulate

---

### Post by Cheesehead on 2012-12-02
> **taunnt said:**
> Can I list the broken packages then just delete those?

Yes. Use Synaptic or the 'debsums' package to list broken packages.

libapt-pkg4.10 does not exist in the Ubuntu repositories:
```
$ rmadison libapt-pkg4.12
libapt-pkg4.12 | 0.8.16~exp12ubuntu6~upgrader1 | lucid-updates | amd64, armel, i386, ia64, powerpc, sparc
libapt-pkg4.12 | 0.8.16~exp12ubuntu10 |       precise | amd64, armel, armhf, i386, powerpc
libapt-pkg4.12 | 0.8.16~exp12ubuntu10.2 | precise-security | amd64, armel, armhf, i386, powerpc
libapt-pkg4.12 | 0.8.16~exp12ubuntu10.6 | precise-updates | amd64, armel, armhf, i386, powerpc
libapt-pkg4.12 | 0.9.7.5ubuntu5 |       quantal | amd64, armel, armhf, i386, powerpc
libapt-pkg4.12 | 0.9.7.5ubuntu5.1 | quantal-updates | amd64, armel, armhf, i386, powerpc
libapt-pkg4.12 | 0.9.7.6ubuntu3 |        raring | armel
libapt-pkg4.12 | 0.9.7.6ubuntu5 |        raring | amd64, armhf, i386, powerpc

```

Don't try to install Aptitude until you have done a successful cache refresh (sudo apt-get update). Watch it carefully for error messages, and post those here.

---

### Post by ivotkl on 2012-12-02
You could also try fo "fix broken packages" from recovery mode.

---

