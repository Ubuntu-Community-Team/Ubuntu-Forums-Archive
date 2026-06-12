---
title: "cant install xfishtank"
date: 2006-10-27
forum: General Help
---

### Post by searayman on 2006-10-27
mike@mike-desktop:~$ sudo apt-get install xfishtank
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
  openoffice.org-l10n-en-za: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
  xfishtank: Depends: libx11-6 but it is not going to be installed
             Depends: libxext6 but it is not going to be installed
E: Broken packages
mike@mike-desktop:~$ 



after all that id does not work, i tried installing from synaptic to but it also failed.

---

