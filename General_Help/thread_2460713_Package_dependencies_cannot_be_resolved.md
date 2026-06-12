---
title: "Package dependencies cannot be resolved"
date: 2021-04-16
forum: General Help
---

### Post by 2CV67 on 2021-04-16
Hi!

13 April 2021, Software Updater offered me an update for my 20.10 including Kernel 5.8.0.49.54, which I tried to install, but the installation failed with the error message:
```
Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
Transaction failed: Package dependencies cannot be resolved
 The following packages have unmet dependencies:

grub-efi-amd64-signed: Depends: grub2-common (>= 2.02~beta2-36ubuntu3.31) but 2.04-1ubuntu35.6 is to be installed
```

I decided to just wait, hoping the problem would be sorted out at the next update.

Today I was offered the next update, including kernel 5.8.0.50.53 but I have the same error message...

No idea how to handle this!

Thanks for any help!

---

### Post by CelticWarrior on 2021-04-16
Please try, in terminal:
```
sudo apt update
sudo apt full-upgrade
```

Post back any errors.

---

### Post by Impavidus on 2021-04-16
What does```
apt-cache policy grub-efi-amd64-signed
```tell you?

2.04-1ubuntu35.6 is the correct version for grub2-common on 20.10, so it looks like something strange is going on with your grub-efi-amd64-signed. It shouldn't depend on grub2-common at all – at least, not directly.

---

### Post by ajgreeny on 2021-04-16
Have you in the past enabled any extra repos temporarily, eg third party PPAs or perhaps the "proposed" repos which have given you package versions that require dependencies that are now unavailable if those repos are no longer enabled.

---

### Post by ActionParsnip on 2021-04-17
I'm betting this is PPA based

---

### Post by 2CV67 on 2021-04-18
Well - thank you all for your contributions!

I ran
```
sudo apt update
sudo apt full-upgrade
```
which worked OK with no error messages & I am now running 5.8.0.50.53 with no problems.

I just wonder what the explanation is & whether that is the end of the story or not?

On the PPA's (which I looked at before running apt) there has been no recent activity.
Many years ago, I enabled the PPA for Grub Customizer.
GC is still installed & active, and thought I had found something significant when I just noticed that that PPA had been disactivated at previous upgrades, but in fact it seems to be no longer required & GC is available directly in the repos, so I suppose that is not relevant?
3 other old PPA's have also been disactivated at previous upgrades but they relate to programs no longer installed (Drawers, Variety, Canon printer) so I suppose are not relevant either.
Finally the PPA for David lynch's Rapid-Photo-Downloader is also disactivated.
RPD is installed & in use.
David Lynch seems to have stopped using the PPA and started using some direct-installation method I had never heard about.
I am not using the latest version of RPD on his site, but SynApt thinks my version is the latest so I suppose is not trying to take any action?

As for Impavidus's question & statement - sorry, I don't begin to understand...

Thanks again for your help!

---

### Post by jemaku on 2021-05-01
> **2CV67 said:**
> 
```

grub-efi-amd64-signed: Depends: grub2-common (>= 2.02~beta2-36ubuntu3.31) but 2.04-1ubuntu35.6 is to be installed
```


Today I got the same error from the graphical Software Updater on my Ubuntu 20.04 (that had not been updated for a while). Only the version numbers are a bit different:
```
grub-efi-amd64-signed: Depends: grub2-common (>= 2.02~beta2-36ubuntu3.31) mutta 2.04-1ubuntu26.11 tullaan asentamaan
```

But 
```

sudo apt update
sudo apt upgrade
``` 
installed more updates than Software Updater would, and solved the problem.

Only PPA I have is Google Chrome that had been disabled by an upgrade.

---

### Post by ActionParsnip on 2021-05-01
I bet PPAs are afoot

---

### Post by ajgreeny on 2021-05-01
If any PPAs are to blame for this, and we still don't really know, you could try installing ppa-purge and running it to remove the repositories and replace any packages from those errant PPAs with the default Ubuntu repo version, or if there is no default version just to remove the problem pakages.

If this problem stems from a PPA or its packages you may solve it by getting rid of those packages.

---

