---
title: "OpenOffice.org"
date: 2005-03-21
forum: General Help
---

### Post by allknowing469 on 2005-03-21
When I was doing "apt-get upgrade" I got the following error towards the end when apt was setting everything up. 

Undoing prelinking of OpenOffice.org binaries... run-parts: /usr/share/openoffic e.org-debian-files/hooks/postinst.d/prelink exited with return code 1
dpkg: error processing openoffice.org-bin (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openoffice.org-gtk-gnome:
 openoffice.org-gtk-gnome depends on openoffice.org-bin (>= 1.1.2+1.1.3); howeve r:
  Package openoffice.org-bin is not configured yet.
dpkg: error processing openoffice.org-gtk-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-bin
 openoffice.org-gtk-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)

I was wondering how to fix this. I thought I read something similar to this before.  :-k

---

### Post by cdhotfire on 2005-03-21
delete the 2 files   

openoffice.org-bin
  openoffice.org-gtk-gnome

and install them again.

that should work.:-)

---

### Post by allknowing469 on 2005-03-21
That didn't work. I get this now

exited with return code 1
dpkg: error processing openoffice.org-bin (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openoffice.org-gtk-gnome:
 openoffice.org-gtk-gnome depends on openoffice.org-bin (>= 1.1.2+1.1.3); however:
  Package openoffice.org-bin is not configured yet.
dpkg: error processing openoffice.org-gtk-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-debian-files:
 openoffice.org-debian-files depends on openoffice.org-bin (>> 1.1.2+1.1.3); however:
  Package openoffice.org-bin is not configured yet.
dpkg: error processing openoffice.org-debian-files (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-bin (>> 1.1.2+1.1.3); however:
  Package openoffice.org-bin is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-help-en:
 openoffice.org-help-en depends on openoffice.org | language-support-en; however:
  Package openoffice.org is not configured yet.
  Package language-support-en is not installed.
dpkg: error processing openoffice.org-help-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-hyphenation-en-us:
 openoffice.org-hyphenation-en-us depends on openoffice.org (>= 1.0.3-3) | language-support-en; however:
  Package openoffice.org is not configured yet.
  Package language-support-en is not installed.
dpkg: error processing openoffice.org-hyphenation-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-thesaurus-en-us:
 openoffice.org-thesaurus-en-us depends on openoffice.org (>= 1.0.3-3) | language-support-en; however:
  Package openoffice.org is not configured yet.
  Package language-support-en is not installed.
dpkg: error processing openoffice.org-thesaurus-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-l10n-en:
 openoffice.org-l10n-en depends on openoffice.org (>> 1.1.1+1.1.2) | language-support-en; however:
  Package openoffice.org is not configured yet.
  Package language-support-en is not installed.
dpkg: error processing openoffice.org-l10n-en (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-bin
 openoffice.org-gtk-gnome
 openoffice.org-debian-files
 openoffice.org
 openoffice.org-help-en
 openoffice.org-hyphenation-en-us
 openoffice.org-thesaurus-en-us
 openoffice.org-l10n-en
E: Sub-process /usr/bin/dpkg returned an error code (1)


 ](*,)

---

### Post by cdhotfire on 2005-03-21
id say uninstall the packages:

  openoffice.org-bin
  openoffice.org-gtk-gnome
  openoffice.org-debian-files
  openoffice.org
  openoffice.org-help-en
  openoffice.org-hyphenation-en-us
  openoffice.org-thesaurus-en-us
  openoffice.org-l10n-en

then press reload, upgrade. Then try to install them again. Let me now if this doesnt work.

edit: install openoffice.org-bin alone after you upgrade. If this works, then install the other after it.

---

### Post by allknowing469 on 2005-03-22
I'll try that when I get home and let you know. 

Thanks

---

### Post by allknowing469 on 2005-03-23
Tried that and I am still getting the same error

Setting up openoffice.org-bin (1.1.3-8ubuntu1) ...
Undoing prelinking of OpenOffice.org binaries... run-parts: /usr/share/openoffice.org-debian-files/hooks/postinst.d/prelink exited with return code 1
dpkg: error processing openoffice.org-bin (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 openoffice.org-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any suggestions would be greatly appreciated.  [-o<

---

### Post by allknowing469 on 2005-03-25
Figured out what the problem was, it had something to do with "prelink". Used it to speed up the opening of OpenOffice. To fix it I had to do this...

sudo apt-get remove prelink

sudo apt-get upgrade

After doing that everything worked fine. Hope this helps anyone else who had the same error(s).   \\:D/

---

### Post by suoko on 2005-04-02
maybe the command  
sudo oooprelink -u
 could solve the problem without uninistalling prelink

---

### Post by toujours on 2005-04-05
I too have been getting this error code 1 message when I try to upgrade OOo.
However, if I try to remove the packages Synaptic just stops !

Any help ?

---

