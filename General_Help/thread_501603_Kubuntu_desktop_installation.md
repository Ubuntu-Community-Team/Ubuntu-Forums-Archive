---
title: "Kubuntu desktop installation"
date: 2007-07-15
forum: General Help
---

### Post by ali780 on 2007-07-15
I want to install Kubuntu desktop but When I use
sudo apt-get install kubuntu-desktop
It report a lot of error like this
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: adept but it is not going to be installed
                   Depends: amarok but it is not going to be installed
                   Depends: bicyclerepair but it is not going to be installed
                   Depends: bluez-pcmcia-support but it is not going to be installed
                   Depends: kde-guidance but it is not going to be installed
                   Depends: kdegraphics-kfile-plugins but it is not going to be installed
                   Depends: kdenetwork-filesharing but it is not going to be installed
                   Depends: keep but it is not going to be installed
                   Depends: language-selector-qt but it is not going to be installed
                   Depends: libgl1-mesa but it is not going to be installed
                   Depends: openoffice.org-kde but it is not going to be installed
                   Depends: python-adns but it is not going to be installed
                   Depends: python-cddb but it is not going to be installed
                   Depends: python-clientcookie but it is not going to be installed
                   Depends: python-crypto but it is not going to be installed
                   Depends: python-egenix-mxproxy but it is not going to be installed
                   Depends: python-egenix-mxstack but it is not going to be installed
                   Depends: python-egenix-mxtexttools but it is not going to be installed
                   Depends: python-egenix-mxtools but it is not going to be installed
                   Depends: python-epydoc but it is not going to be installed
                   Depends: python-eunuchs but it is not going to be installed
                   Depends: python-examples but it is not going to be installed
                   Depends: python-gadfly but it is not going to be installed
                   Depends: python-gd but it is not going to be installed
                   Depends: python-gdbm but it is not going to be installed
                   Depends: python-genetic but it is not going to be installed
                   Depends: python-geoip but it is not going to be installed
                   Depends: python-htmlgen but it is not going to be installed
                   Depends: python-htmltmpl but it is not going to be installed
                   Depends: python-id3lib but it is not going to be installed
                   Depends: python-imaging but it is not going to be installed
                   Depends: python-imaging-sane but it is not going to be installed
                   Depends: python-jabber but it is not going to be installed
                   Depends: python-kjbuckets but it is not going to be installed
                   Depends: python-ldap but it is not going to be installed
                   Depends: python-mysqldb but it is not going to be installed
                   Depends: python-netcdf but it is not going to be installed
                   Depends: python-newt but it is not going to be installed
                   Depends: python-pam but it is not going to be installed
                   Depends: python-parted but it is not going to be installed
                   Depends: python-pexpect but it is not going to be installed
                   Depends: python-pgsql but it is not going to be installed
                   Depends: python-pisock but it is not going to be installed
                   Depends: python-pqueue but it is not going to be installed
                   Depends: python-pyao but it is not going to be installed
                   Depends: python-pylibacl but it is not going to be installed
                   Depends: python-pyopenssl but it is not going to be installed
                   Depends: python-pyorbit but it is not going to be installed
                   Depends: python-pyvorbis but it is not going to be installed
                   Depends: python-pyxattr but it is not going to be installed
                   Depends: python-reportlab but it is not going to be installed
                   Depends: python-simpletal but it is not going to be installed
                   Depends: python-soappy but it is not going to be installed
                   Depends: python-sqlite but it is not going to be installed
                   Depends: python-stats but it is not going to be installed
                   Depends: python-syck but it is not going to be installed
                   Depends: python-unit but it is not going to be installed
                   Depends: python-xmpp but it is not going to be installed
E: Broken packages
 hO wcan I fix it?

---

### Post by merlinus on 2007-07-15
Which flavor and version of ubuntu are you using?

Also, you might try this:

```

sudo aptitude update && sudo aptitude install kubuntu-desktop

```

-merlin

---

### Post by Nythain on 2007-07-15
you should also make sure you have all of your repos enabled in your /etc/apt/sources.list file by
gksudo gedit /etc/apt/sources.list

then uncommenting any that start with
# deb
by remove the #

after saving you would want to
sudo apt-get update

then try installing the kubuntu-desktop package again, i would recomend using aptitude instead of apt-get for such a large metapackage
sudo aptitude install kubuntu-desktop

---

### Post by ali780 on 2007-07-15
I am using 7.04 fiesty

---

