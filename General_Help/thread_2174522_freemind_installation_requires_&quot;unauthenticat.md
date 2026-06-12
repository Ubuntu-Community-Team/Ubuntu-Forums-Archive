---
title: "freemind installation requires &quot;unauthenticated sources&quot;?"
date: 2013-09-14
forum: General Help
---

### Post by andy.stevens on 2013-09-14
Hi,

I'm running 13.04 and found freemind 0.9.0+dfsg-2ubuntu1 in the Software Centre, but when I try to install it gives me an error
"Requires installation of untrusted packages
This requires installing packages from unauthenticated sources.
default-jre default-jre-headless freemind freemind-doc java-wrappers libbackport-util-concurrent-java libbcel-java libdom4j-java libgetopt-java libgnu-regexp-java libjaxen-java libjaxme-java libjdom1-java libjgoodies-common-java libjgoodies-forms-java libjibx1.1-java liblog4j1.2-java libqdox-java libxom-java libxpp2-java libxpp3-java simplyhtml"

This isn't the first time I've seen this error this week, though, as totem-plugins-extra and freecol give a similar message when I try to install those.  Which makes me think perhaps something more fundamental is broken or missing, rather than just these packages.  But what, and how can I check?


Andy

---

### Post by mcduck on 2013-09-15
That error is caused by having a software repository, but not the digital signing keys for it. The keys are used to verify the integrity of packages, and that they really come from correct source. (Confusingly, you get the warning message regardless of if the packages you currently install come from that source or not, as long as there is any repository configured but missing the keys.)

Assuming you have added some third-party repository recently, the easiest way to fix the warnings is to go check that repository's web page, find the security keys, and add them to your system.

If you have added more than one third-party repository lately, or can't remember when the warning messages started appearing, you could open Software Center, then go to Edit->Software Sources, and compare the information on Authentication-tab with the repositories on the Other Software-tab to find out which repository is missing it's key...

---

### Post by andy.stevens on 2013-09-23
Is there another way (log file, command line, ...) to tell which of the repositories it thinks is unauthenticated?  Asides from the standard Ubuntu ones that are ticked, there's only OpenPrinting (which has a key listed on the other tab) and the get_iplayer PPA on launchpad.  Neither of those are enabled at the moment and I'm still getting the error message; I even removed the PPA one entirely, but that made no difference (though adding it back doesn't appear to have downloaded any additional key).
I've tried telling it to Repair when the error message comes up, I've tried Restore Defaults on the Authentication tab, but still I get the error message.


Andy.

---

### Post by oldos2er on 2013-09-23
```
sudo apt-get update
``` should show you which repo is missing its key.

---

### Post by andy.stevens on 2013-09-24
> **oldos2er said:**
> ```
sudo apt-get update
``` should show you which repo is missing its key.

Thanks, that helps.  Looks like it might not be missing, just bad:

```
W:  GPG error: http://gb.archive.ubuntu.com raring Release: The following  signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive  Automatic Signing Key <ftpmaster@ubuntu.com>
```

Not  entirely sure what I can do about it, though.  I already tried using the  "Restore Defaults" button, but that didn't make any difference.


Andy.

---

### Post by oldos2er on 2013-09-25
Try Method #1 here: [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

---

### Post by andy.stevens on 2013-09-29
> **oldos2er said:**
> Try Method #1 here: [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

Didn't fancy deleting directories in /var myself, but following the instructions at [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061) I changed the mirror to a different one and the problem went away.

Thanks for the help.


Andy.

---

### Post by oldos2er on 2013-09-29
No deleting involved, just moving the old lists then recreating new ones. Glad you got it working.

---

