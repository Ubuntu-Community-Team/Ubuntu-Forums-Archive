---
title: "Unable to load Gnome"
date: 2006-12-31
forum: General Help
---

### Post by PAM on 2006-12-31
I am current running xubuntu 6.10 and am very impressed.

However, an untoward event occured which caused some problems.

After cruising the forums for similar problems, rebuilding GDM seemed to be a good way to go and fixed most of the issues.

The remaining issue(s) can be illistrated by trying to install anything via Synaptic. For example, the error messages for whois are;

dependency problems - leaving unconfigured
Setting up whois (4.7.14) ...
Setting up xwhois (0.4.2-8) ...

details ...

Errors were encountered while processing:
 cnews
 trn
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up cnews (cr.g7-39) ...
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gnome -- is libgnome2-perl installed?)
debconf: falling back to frontend: Dialog
hostname: Unknown host
dpkg: error processing cnews (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of trn:
 trn depends on inews | inewsinn; however:
  Package inews is not installed.
  Package cnews which provides inews is not configured yet.
  Package inewsinn is not installed.
dpkg: error processing trn (--configure):
 dependency problems - leaving unconfigured

Your thoughts would be greatly appreciated.

Thanks and Enjoy,

---

