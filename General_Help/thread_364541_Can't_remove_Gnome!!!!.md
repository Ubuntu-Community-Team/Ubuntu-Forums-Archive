---
title: "Can't remove Gnome!!!!"
date: 2007-02-18
forum: General Help
---

### Post by _linux_ on 2007-02-18
I just upgraded from Dapper to Edgy. Then I installed XFCE. So now I want to remove Gnome and have a pure XFCE desktop. I followed the Remove Ubuntu instructions [here ]("http://www.psychocats.net/ubuntu/purexfce")and this is what I get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gij is not installed, so not removed
Package libgcj-bc is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
  openoffice.org-l10n-en-za: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
E: Broken packages
```
I went to Synaptic and did Fix Broken Packages but I still get the same error. How can I fix it?

---

### Post by _linux_ on 2007-02-18
Okay, I finally got it to work. All I had to do was add openoff.org-l10n-en-gb and openoffice.org-l10n-en-za to the list of programs for apt-get to remove.

---

