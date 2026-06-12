---
title: "software-properties-gtk crashing"
date: 2014-05-30
forum: General Help
---

### Post by aramil248 on 2014-05-30
when i click on setting on my update manager it just reloads the update manager so i go and do sudo software-properties-gtk in the terminal and i get this error 

aramil@ubuntu:~$ sudo software-properties-gtk
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 104, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 89, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 97, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 585, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.7/dist-packages/aptsources/distro.py", line 87, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
aramil@ubuntu:~$ 

i reinstalled software-properties-gtk and python2.7 because i saw it there but i keep getting the same error can someone please help me.

---

### Post by slickymaster on 2014-05-30
Hi aramil248, welcome to the forums.

> **aramil248 said:**
> when i click on setting on my update manager it just reloads the update manager so i go and do sudo software-properties-gtk in the terminal and i get this error 

aramil@ubuntu:~$ sudo software-properties-gtk
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 104, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 89, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 97, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 585, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.7/dist-packages/aptsources/distro.py", line 87, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
**[COLOR=#ff0000]aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template[/COLOR]**
aramil@ubuntu:~$ 

i reinstalled software-properties-gtk and python2.7 because i saw it there but i keep getting the same error can someone please help me.

That might be the culprit. The distribution template might not have been updated. Can you please post the content of your **/usr/share/python-apt/templates/Ubuntu.info** file

---

### Post by aramil248 on 2014-05-30
```
ChangelogURI: [http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog](http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog)

Suite: precise
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 12.04 'Precise Pangolin'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: precise
ParentSuite: precise
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 12.04 'Precise Pangolin'

Suite: precise
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*12.04
MatchURI: cdrom:\[Ubuntu.*12.04
Description: Cdrom with Ubuntu 12.04 'Precise Pangolin'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: precise
Official: false
RepositoryType: deb
BaseURI: [http://archive.canonical.com](http://archive.canonical.com)
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: precise
Official: false
RepositoryType: deb
BaseURI: [http://extras.ubuntu.com](http://extras.ubuntu.com)
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: precise-security
ParentSuite: precise
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: precise-security
ParentSuite: precise
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: precise-updates
ParentSuite: precise
RepositoryType: deb
Description: Recommended updates

Suite: precise-updates
ParentSuite: precise
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: precise-proposed
ParentSuite: precise
RepositoryType: deb
Description: Pre-released updates

Suite: precise-proposed
ParentSuite: precise
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: precise-backports
ParentSuite: precise
RepositoryType: deb
Description: Unsupported updates

Suite: precise-backports
ParentSuite: precise
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

Suite: oneiric
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 11.10 'Oneiric Ocelot'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: oneiric
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 11.10 'Oneiric Ocelot'

Suite: oneiric
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*11.10
MatchURI: cdrom:\[Ubuntu.*11.10
Description: Cdrom with Ubuntu 11.10 'Oneiric Ocelot'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: oneiric
Official: false
RepositoryType: deb
BaseURI: [http://archive.canonical.com](http://archive.canonical.com)
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: oneiric
Official: false
RepositoryType: deb
BaseURI: [http://extras.ubuntu.com](http://extras.ubuntu.com)
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: oneiric-security
ParentSuite: oneiric
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: oneiric-security
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: oneiric-updates
ParentSuite: oneiric
RepositoryType: deb
Description: Recommended updates

Suite: oneiric-updates
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: oneiric-proposed
ParentSuite: oneiric
RepositoryType: deb
Description: Pre-released updates

Suite: oneiric-proposed
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: oneiric-backports
ParentSuite: oneiric
RepositoryType: deb
Description: Unsupported updates

Suite: oneiric-backports
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: natty
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 11.04 'Natty Narwhal'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: natty
ParentSuite: natty
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 11.04 'Natty Narwhal'

Suite: natty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*11.04
MatchURI: cdrom:\[Ubuntu.*11.04
Description: Cdrom with Ubuntu 11.04 'Natty Narwhal'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: natty
Official: false
RepositoryType: deb
BaseURI: [http://archive.canonical.com](http://archive.canonical.com)
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: natty
Official: false
RepositoryType: deb
BaseURI: [http://extras.ubuntu.com](http://extras.ubuntu.com)
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: natty-security
ParentSuite: natty
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: natty-security
ParentSuite: natty
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: natty-updates
ParentSuite: natty
RepositoryType: deb
Description: Recommended updates

Suite: natty-updates
ParentSuite: natty
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: natty-proposed
ParentSuite: natty
RepositoryType: deb
Description: Pre-released updates

Suite: natty-proposed
ParentSuite: natty
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: natty-backports
ParentSuite: natty
RepositoryType: deb
Description: Unsupported updates

Suite: natty-backports
ParentSuite: natty
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

Suite: maverick
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 10.10 'Maverick Meerkat'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: maverick
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*10.10
MatchURI: cdrom:\[Ubuntu.*10.10
Description: Cdrom with Ubuntu 10.10 'Maverick Meerkat'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: maverick
Official: false
RepositoryType: deb
BaseURI: [http://archive.canonical.com](http://archive.canonical.com)
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: maverick
Official: false
RepositoryType: deb
BaseURI: [http://extras.ubuntu.com](http://extras.ubuntu.com)
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: maverick-security
ParentSuite: maverick
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: maverick-updates
ParentSuite: maverick
RepositoryType: deb
Description: Recommended updates

Suite: maverick-proposed
ParentSuite: maverick
RepositoryType: deb
Description: Pre-released updates

Suite: maverick-backports
ParentSuite: maverick
RepositoryType: deb
Description: Unsupported updates

Suite: lucid
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 10.04 'Lucid Lynx'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: lucid
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*10.04
MatchURI: cdrom:\[Ubuntu.*10.04
Description: Cdrom with Ubuntu 10.04 'Lucid Lynx'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: lucid-security
ParentSuite: lucid
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: lucid-updates
ParentSuite: lucid
RepositoryType: deb
Description: Recommended updates

Suite: lucid-proposed
ParentSuite: lucid
RepositoryType: deb
Description: Pre-released updates

Suite: lucid-backports
ParentSuite: lucid
RepositoryType: deb
Description: Unsupported updates

Suite: karmic
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 9.10 'Karmic Koala'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: karmic
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*9.10
MatchURI: cdrom:\[Ubuntu.*9.10
Description: Cdrom with Ubuntu 9.10 'Karmic Koala'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: karmic-security
ParentSuite: karmic
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: karmic-updates
ParentSuite: karmic
RepositoryType: deb
Description: Recommended updates

Suite: karmic-proposed
ParentSuite: karmic
RepositoryType: deb
Description: Pre-released updates

Suite: karmic-backports
ParentSuite: karmic
RepositoryType: deb
Description: Unsupported updates

Suite: jaunty
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 9.04 'Jaunty Jackalope'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: jaunty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*9.04
MatchURI: cdrom:\[Ubuntu.*9.04
Description: Cdrom with Ubuntu 9.04 'Jaunty Jackalope'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: jaunty-security
ParentSuite: jaunty
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: jaunty-updates
ParentSuite: jaunty
RepositoryType: deb
Description: Recommended updates

Suite: jaunty-proposed
ParentSuite: jaunty
RepositoryType: deb
Description: Pre-released updates

Suite: jaunty-backports
ParentSuite: jaunty
RepositoryType: deb
Description: Unsupported updates

Suite: intrepid
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 8.10 'Intrepid Ibex'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: intrepid
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*8.10
MatchURI: cdrom:\[Ubuntu.*8.10
Description: Cdrom with Ubuntu 8.10 'Intrepid Ibex'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: intrepid-security
ParentSuite: intrepid
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: intrepid-updates
ParentSuite: intrepid
RepositoryType: deb
Description: Recommended updates

Suite: intrepid-proposed
ParentSuite: intrepid
RepositoryType: deb
Description: Pre-released updates

Suite: intrepid-backports
ParentSuite: intrepid
RepositoryType: deb
Description: Unsupported updates


Suite: hardy
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 8.04 'Hardy Heron'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: hardy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*8.04
MatchURI: cdrom:\[Ubuntu.*8.04
Description: Cdrom with Ubuntu 8.04 'Hardy Heron'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: hardy-security
ParentSuite: hardy
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: hardy-updates
ParentSuite: hardy
RepositoryType: deb
Description: Recommended updates

Suite: hardy-proposed
ParentSuite: hardy
RepositoryType: deb
Description: Pre-released updates

Suite: hardy-backports
ParentSuite: hardy
RepositoryType: deb
Description: Unsupported updates


Suite: gutsy
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu
BaseURI-sparc: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI-sparc: archive.ubuntu.com/ubuntu
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 7.10 'Gutsy Gibbon'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: gutsy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*7.10
MatchURI: cdrom:\[Ubuntu.*7.10
Description: Cdrom with Ubuntu 7.10 'Gutsy Gibbon'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: gutsy-security
ParentSuite: gutsy
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-sparc: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-sparc: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: gutsy-updates
ParentSuite: gutsy
RepositoryType: deb
Description: Recommended updates

Suite: gutsy-proposed
ParentSuite: gutsy
RepositoryType: deb
Description: Pre-released updates

Suite: gutsy-backports
ParentSuite: gutsy
RepositoryType: deb
Description: Unsupported updates


Suite: feisty
RepositoryType: deb
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 7.04 'Feisty Fawn'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: feisty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*7.04
MatchURI: cdrom:\[Ubuntu.*7.04
Description: Cdrom with Ubuntu 7.04 'Feisty Fawn'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: feisty-security
ParentSuite: feisty
RepositoryType: deb
BaseURI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Important security updates

Suite: feisty-updates
ParentSuite: feisty
RepositoryType: deb
Description: Recommended updates

Suite: feisty-proposed
ParentSuite: feisty
RepositoryType: deb
Description: Pre-released updates

Suite: feisty-backports
ParentSuite: feisty
RepositoryType: deb
Description: Unsupported updates

Suite: edgy
RepositoryType: deb
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 6.10 'Edgy Eft'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: edgy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*6.10
MatchURI: cdrom:\[Ubuntu.*6.10
Description: Cdrom with Ubuntu 6.10 'Edgy Eft'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: edgy-security
ParentSuite: edgy
RepositoryType: deb
BaseURI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Important security updates

Suite: edgy-updates
ParentSuite: edgy
RepositoryType: deb
Description: Recommended updates

Suite: edgy-proposed
ParentSuite: edgy
RepositoryType: deb
Description: Pre-released updates

Suite: edgy-backports
ParentSuite: edgy
RepositoryType: deb
Description: Unsupported updates

Suite: dapper
RepositoryType: deb
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 6.06 LTS 'Dapper Drake'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained (universe)
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software (Multiverse)
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: dapper
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*6.06
MatchURI: cdrom:\[Ubuntu.*6.06
Description: Cdrom with Ubuntu 6.06 LTS 'Dapper Drake'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: dapper-security
ParentSuite: dapper
RepositoryType: deb
BaseURI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Important security updates

Suite: dapper-updates
ParentSuite: dapper
RepositoryType: deb
Description: Recommended updates

Suite: dapper-proposed
ParentSuite: dapper
RepositoryType: deb
Description: Pre-released updates

Suite: dapper-backports
ParentSuite: dapper
RepositoryType: deb
Description: Unsupported updates

Suite: breezy
RepositoryType: deb
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: Ubuntu.mirrors
BaseURI-ia64: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 5.10 'Breezy Badger'
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: breezy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*5.10
MatchURI: cdrom:\[Ubuntu.*5.10
Description: Cdrom with Ubuntu 5.10 'Breezy Badger'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: breezy-security
ParentSuite: breezy
RepositoryType: deb
BaseURI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 5.10 Security Updates

Suite: breezy-updates
ParentSuite: breezy
RepositoryType: deb
Description: Ubuntu 5.10 Updates

Suite: breezy-backports
ParentSuite: breezy
RepositoryType: deb
Description: Ubuntu 5.10 Backports

Suite: hoary
RepositoryType: deb
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 5.04 'Hoary Hedgehog'
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: hoary
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*5.04
MatchURI: cdrom:\[Ubuntu.*5.04
Description: Cdrom with Ubuntu 5.04 'Hoary Hedgehog'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: hoary-security
ParentSuite: hoary
RepositoryType: deb
BaseURI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 5.04 Security Updates

Suite: hoary-updates
ParentSuite: hoary
RepositoryType: deb
Description: Ubuntu 5.04 Updates

Suite: hoary-backports
ParentSuite: hoary
RepositoryType: deb
Description: Ubuntu 5.04 Backports

Suite: warty
RepositoryType: deb
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu
Description: Ubuntu 4.10 'Warty Warthog'
Component: main
CompDescription: No longer officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: warty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*4.10
MatchURI: cdrom:\[Ubuntu.*4.10
Description: Cdrom with Ubuntu 4.10 'Warty Warthog'
Available: False
Component: main
CompDescription: No longer officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: warty-security
ParentSuite: warty
RepositoryType: deb
BaseURI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Ubuntu 4.10 Security Updates

Suite: warty-updates
ParentSuite: warty
RepositoryType: deb
Description: Ubuntu 4.10 Updates

Suite: warty-backports
ParentSuite: warty
RepositoryType: deb
Description: Ubuntu 4.10 Backports
```

---

### Post by slickymaster on 2014-05-30
Are you still running Precise or did you upgrade to Trusty? Please post the output you get of```
lsb_release -r
```

---

### Post by aramil248 on 2014-05-30
it shows 14.04 but i never upgraded to that i was planning to

---

### Post by slickymaster on 2014-05-30
What you have to is tho edit your **/usr/share/python-apt/templates/Ubuntu.info** file, adding to it the missing references to Trusty. In a terminal run the following:```
gksudo gedit /usr/share/python-apt/templates/Ubuntu.info
```you'll be prompt to enter your password. Type it and Gedit will open the file with write permissions.

Once there copy/paste this```
Suite: trusty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 14.04 'Trusty Tahr'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: trusty
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 14.04 'Trusty Tahr'

Suite: trusty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*14.04
MatchURI: cdrom:\[Ubuntu.*14.04
Description: Cdrom with Ubuntu 14.04 'Trusty Tahr'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: trusty
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: trusty
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: trusty-security
ParentSuite: trusty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: trusty-security
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: trusty-updates
ParentSuite: trusty
RepositoryType: deb
Description: Recommended updates

Suite: trusty-updates
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: trusty-proposed
ParentSuite: trusty
RepositoryType: deb
Description: Pre-released updates

Suite: trusty-proposed
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: trusty-backports
ParentSuite: trusty
RepositoryType: deb
Description: Unsupported updates

Suite: trusty-backports
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates
``` after the first line (the one that reads _[COLOR=#000000]ChangelogURI: [/COLOR][http://changelogs.ubuntu.com/changel...s_%s/changelog]("http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog")_) and before the line that reads _Suite: precise_

Save and close the file and run```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by aramil248 on 2014-05-30
thanks it worked

---

### Post by slickymaster on 2014-05-30
You're welcome. Happy *buntuing.

---

### Post by dannyboy79 on 2014-05-30
> **aramil248 said:**
> when i click on setting on my update manager it just reloads the update manager so i go and do sudo software-properties-gtk in the terminal and i get this error 

whenever you want to run a GUI based application with root priveleges you need to use gksudo or gksu, NOT just sudo by itself. There's an explaination as to why here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

So are you all upgraded to 14.04 or are you still running 12.04?

UPDATE: based on our twitter conversation, i think you're mixing up ppa's and repositories. PPA's are Personal Package Archive. It's similar to a repository in that it's a location that has .deb packages but it's a personal one, meaning someone created the ppa themselves, it's not hosted by ubuntu so it actually could contain virus's and bad code/packages. Repositories are where ubuntu stores all it's packages, think of it like an itunes store where you can download software. Guides that tell you to use a PPA should always have a warning that states that you should be cautious about enabling PPA's because of the simple fact that anyone can create a PPA and host debian packages there. the debian packages could be named a certain thing but that doesn't mean the package actually has that package. So most times people will suggest that you only use regular ubuntu repositories first and foremost. only if you reallly need to use a ppa should you. and it's good to google around first and read about what others are saying about the ppa.

---

### Post by aramil248 on 2014-05-30
> **dannyboy79 said:**
> So are you all upgraded to 14.04 or are you still running 12.04?

i had 12.04 but when i checked my ubuntu version it said 14.04 but i dont rember ever updating to that so some how my ubuntu got updated with out me knowing

---

### Post by dannyboy79 on 2014-05-30
what kernel are you running?
```
uname -r
```

what does lsb_release -a return?
```
lsb_release -a
```

---

### Post by aramil248 on 2014-05-30
kernal: 3.2.0-63-generic-pae
lsb_release: LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

---

### Post by dannyboy79 on 2014-05-30
something isn't right, your kernel is way old. you should be on 3.13 kernel at least.

---

### Post by aramil248 on 2014-05-30
so how do i run a newer kernal?

---

### Post by dannyboy79 on 2014-05-30
i don't think you properly upgraded. the guy helped you make it so that lsb_release -a reports that you're running 14.04 without actually helping you upgrade to it. i am honestly not sure what to do. what happens when you run
```
gksudo do-release-upgrade
```

---

### Post by aramil248 on 2014-05-30
it shows this "Checking for a new Ubuntu release
No new release found"

---

### Post by dannyboy79 on 2014-05-30
ok, you need to revert your file back to what you had in post #3, adding that 14.04 info was the wrong thing to do. So, edit your /usr/share/python-apt/templates/Ubuntu.info file and make it look like what you posted in post #3 again and we'll go from there.

---

### Post by aramil248 on 2014-05-31
uh when i open /user/share/python-apt/templates/Ubuntu.info its blank

---

### Post by dannyboy79 on 2014-05-31
hmmm, well let's make it like it was in post #3. so in a terminal issue the following command
```
gksudo gedit /usr/share/python-apt/templates/Ubuntu.info
```
and within that file copy and paste what you pasted from post #3, save the file and close gedit. Then issue the following
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

and we'll go from there.

---

### Post by aramil248 on 2014-05-31
ok done

---

### Post by dannyboy79 on 2014-05-31
what does this file show?
```
cat /etc/update-manager/release-upgrades
```
make sure it says "Prompt=lts" if it doesn't. you'll need gksudo priveleges to edit it because it's owned by root

---

### Post by aramil248 on 2014-06-01
it does show Prompt=lts

---

### Post by dannyboy79 on 2014-06-01
does running ```
gksudo update-manager-d
``` allow you to upgrade?

---

### Post by slickymaster on 2014-06-02
> **dannyboy79 said:**
> something isn't right, your kernel is way old. you should be on 3.13 kernel at least.
I agree, that's completely wrong.
> **dannyboy79 said:**
> i don't think you properly upgraded. the guy helped you make it so that lsb_release -a reports that you're running 14.04 without actually helping you upgrade to it. i am honestly not sure what to do. what happens when you run
```
gksudo do-release-upgrade
```
The OP's original post only addressed issues regarding the fact that software-properties-gtk was crashing which, as it turns out, was completely misleading because his problem is deeper than that, as I now read through the thread.

Now that you have reverted your **/usr/share/python-apt/templates/Ubuntu.info** file, can you please post here the output of the following commands:```
lsb_release -a && uname -r
``````
cat /usr/share/python-apt/templates/Ubuntu.info
``````
sudo apt-get update && sudo apt-get upgrade && sudo do-release upgrade
```so we can see how his now your system.

---

### Post by aramil248 on 2014-06-02
@dannyboy79 when i run gksudo update-manager-d nothing happens

@slickmaster 
```
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty
3.2.0-63-generic-pae


```

```
ChangelogURI: http://changelogs.ubuntu.com/changel...s_%s/changelog

Suite: precise
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 12.04 'Precise Pangolin'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: precise
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 12.04 'Precise Pangolin'

Suite: precise
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*12.04
MatchURI: cdrom:\[Ubuntu.*12.04
Description: Cdrom with Ubuntu 12.04 'Precise Pangolin'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: precise
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: precise
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: precise-security
ParentSuite: precise
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: precise-security
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: precise-updates
ParentSuite: precise
RepositoryType: deb
Description: Recommended updates

Suite: precise-updates
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: precise-proposed
ParentSuite: precise
RepositoryType: deb
Description: Pre-released updates

Suite: precise-proposed
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: precise-backports
ParentSuite: precise
RepositoryType: deb
Description: Unsupported updates

Suite: precise-backports
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

Suite: oneiric
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 11.10 'Oneiric Ocelot'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: oneiric
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 11.10 'Oneiric Ocelot'

Suite: oneiric
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*11.10
MatchURI: cdrom:\[Ubuntu.*11.10
Description: Cdrom with Ubuntu 11.10 'Oneiric Ocelot'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: oneiric
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: oneiric
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: oneiric-security
ParentSuite: oneiric
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: oneiric-security
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: oneiric-updates
ParentSuite: oneiric
RepositoryType: deb
Description: Recommended updates

Suite: oneiric-updates
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: oneiric-proposed
ParentSuite: oneiric
RepositoryType: deb
Description: Pre-released updates

Suite: oneiric-proposed
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: oneiric-backports
ParentSuite: oneiric
RepositoryType: deb
Description: Unsupported updates

Suite: oneiric-backports
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: natty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 11.04 'Natty Narwhal'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: natty
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 11.04 'Natty Narwhal'

Suite: natty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*11.04
MatchURI: cdrom:\[Ubuntu.*11.04
Description: Cdrom with Ubuntu 11.04 'Natty Narwhal'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: natty
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: natty
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: natty-security
ParentSuite: natty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: natty-security
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: natty-updates
ParentSuite: natty
RepositoryType: deb
Description: Recommended updates

Suite: natty-updates
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: natty-proposed
ParentSuite: natty
RepositoryType: deb
Description: Pre-released updates

Suite: natty-proposed
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: natty-backports
ParentSuite: natty
RepositoryType: deb
Description: Unsupported updates

Suite: natty-backports
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

Suite: maverick
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 10.10 'Maverick Meerkat'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: maverick
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*10.10
MatchURI: cdrom:\[Ubuntu.*10.10
Description: Cdrom with Ubuntu 10.10 'Maverick Meerkat'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: maverick
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: maverick
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: maverick-security
ParentSuite: maverick
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: maverick-updates
ParentSuite: maverick
RepositoryType: deb
Description: Recommended updates

Suite: maverick-proposed
ParentSuite: maverick
RepositoryType: deb
Description: Pre-released updates

Suite: maverick-backports
ParentSuite: maverick
RepositoryType: deb
Description: Unsupported updates

Suite: lucid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 10.04 'Lucid Lynx'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: lucid
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*10.04
MatchURI: cdrom:\[Ubuntu.*10.04
Description: Cdrom with Ubuntu 10.04 'Lucid Lynx'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: lucid-security
ParentSuite: lucid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: lucid-updates
ParentSuite: lucid
RepositoryType: deb
Description: Recommended updates

Suite: lucid-proposed
ParentSuite: lucid
RepositoryType: deb
Description: Pre-released updates

Suite: lucid-backports
ParentSuite: lucid
RepositoryType: deb
Description: Unsupported updates

Suite: karmic
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 9.10 'Karmic Koala'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: karmic
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*9.10
MatchURI: cdrom:\[Ubuntu.*9.10
Description: Cdrom with Ubuntu 9.10 'Karmic Koala'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: karmic-security
ParentSuite: karmic
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: karmic-updates
ParentSuite: karmic
RepositoryType: deb
Description: Recommended updates

Suite: karmic-proposed
ParentSuite: karmic
RepositoryType: deb
Description: Pre-released updates

Suite: karmic-backports
ParentSuite: karmic
RepositoryType: deb
Description: Unsupported updates

Suite: jaunty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 9.04 'Jaunty Jackalope'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: jaunty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*9.04
MatchURI: cdrom:\[Ubuntu.*9.04
Description: Cdrom with Ubuntu 9.04 'Jaunty Jackalope'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: jaunty-security
ParentSuite: jaunty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: jaunty-updates
ParentSuite: jaunty
RepositoryType: deb
Description: Recommended updates

Suite: jaunty-proposed
ParentSuite: jaunty
RepositoryType: deb
Description: Pre-released updates

Suite: jaunty-backports
ParentSuite: jaunty
RepositoryType: deb
Description: Unsupported updates

Suite: intrepid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 8.10 'Intrepid Ibex'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: intrepid
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*8.10
MatchURI: cdrom:\[Ubuntu.*8.10
Description: Cdrom with Ubuntu 8.10 'Intrepid Ibex'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: intrepid-security
ParentSuite: intrepid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: intrepid-updates
ParentSuite: intrepid
RepositoryType: deb
Description: Recommended updates

Suite: intrepid-proposed
ParentSuite: intrepid
RepositoryType: deb
Description: Pre-released updates

Suite: intrepid-backports
ParentSuite: intrepid
RepositoryType: deb
Description: Unsupported updates


Suite: hardy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 8.04 'Hardy Heron'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: hardy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*8.04
MatchURI: cdrom:\[Ubuntu.*8.04
Description: Cdrom with Ubuntu 8.04 'Hardy Heron'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: hardy-security
ParentSuite: hardy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: hardy-updates
ParentSuite: hardy
RepositoryType: deb
Description: Recommended updates

Suite: hardy-proposed
ParentSuite: hardy
RepositoryType: deb
Description: Pre-released updates

Suite: hardy-backports
ParentSuite: hardy
RepositoryType: deb
Description: Unsupported updates


Suite: gutsy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
BaseURI-sparc: http://archive.ubuntu.com/ubuntu/
MatchURI-sparc: archive.ubuntu.com/ubuntu
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 7.10 'Gutsy Gibbon'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: gutsy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*7.10
MatchURI: cdrom:\[Ubuntu.*7.10
Description: Cdrom with Ubuntu 7.10 'Gutsy Gibbon'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: gutsy-security
ParentSuite: gutsy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-sparc: http://security.ubuntu.com/ubuntu/
MatchURI-sparc: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: gutsy-updates
ParentSuite: gutsy
RepositoryType: deb
Description: Recommended updates

Suite: gutsy-proposed
ParentSuite: gutsy
RepositoryType: deb
Description: Pre-released updates

Suite: gutsy-backports
ParentSuite: gutsy
RepositoryType: deb
Description: Unsupported updates


Suite: feisty
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 7.04 'Feisty Fawn'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: feisty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*7.04
MatchURI: cdrom:\[Ubuntu.*7.04
Description: Cdrom with Ubuntu 7.04 'Feisty Fawn'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: feisty-security
ParentSuite: feisty
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Important security updates

Suite: feisty-updates
ParentSuite: feisty
RepositoryType: deb
Description: Recommended updates

Suite: feisty-proposed
ParentSuite: feisty
RepositoryType: deb
Description: Pre-released updates

Suite: feisty-backports
ParentSuite: feisty
RepositoryType: deb
Description: Unsupported updates

Suite: edgy
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 6.10 'Edgy Eft'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: edgy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*6.10
MatchURI: cdrom:\[Ubuntu.*6.10
Description: Cdrom with Ubuntu 6.10 'Edgy Eft'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: edgy-security
ParentSuite: edgy
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Important security updates

Suite: edgy-updates
ParentSuite: edgy
RepositoryType: deb
Description: Recommended updates

Suite: edgy-proposed
ParentSuite: edgy
RepositoryType: deb
Description: Pre-released updates

Suite: edgy-backports
ParentSuite: edgy
RepositoryType: deb
Description: Unsupported updates

Suite: dapper
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 6.06 LTS 'Dapper Drake'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained (universe)
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software (Multiverse)
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: dapper
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*6.06
MatchURI: cdrom:\[Ubuntu.*6.06
Description: Cdrom with Ubuntu 6.06 LTS 'Dapper Drake'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: dapper-security
ParentSuite: dapper
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Important security updates

Suite: dapper-updates
ParentSuite: dapper
RepositoryType: deb
Description: Recommended updates

Suite: dapper-proposed
ParentSuite: dapper
RepositoryType: deb
Description: Pre-released updates

Suite: dapper-backports
ParentSuite: dapper
RepositoryType: deb
Description: Unsupported updates

Suite: breezy
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: Ubuntu.mirrors
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 5.10 'Breezy Badger'
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: breezy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*5.10
MatchURI: cdrom:\[Ubuntu.*5.10
Description: Cdrom with Ubuntu 5.10 'Breezy Badger'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: breezy-security
ParentSuite: breezy
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 5.10 Security Updates

Suite: breezy-updates
ParentSuite: breezy
RepositoryType: deb
Description: Ubuntu 5.10 Updates

Suite: breezy-backports
ParentSuite: breezy
RepositoryType: deb
Description: Ubuntu 5.10 Backports

Suite: hoary
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 5.04 'Hoary Hedgehog'
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: hoary
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*5.04
MatchURI: cdrom:\[Ubuntu.*5.04
Description: Cdrom with Ubuntu 5.04 'Hoary Hedgehog'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: hoary-security
ParentSuite: hoary
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 5.04 Security Updates

Suite: hoary-updates
ParentSuite: hoary
RepositoryType: deb
Description: Ubuntu 5.04 Updates

Suite: hoary-backports
ParentSuite: hoary
RepositoryType: deb
Description: Ubuntu 5.04 Backports

Suite: warty
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
Description: Ubuntu 4.10 'Warty Warthog'
Component: main
CompDescription: No longer officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: warty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*4.10
MatchURI: cdrom:\[Ubuntu.*4.10
Description: Cdrom with Ubuntu 4.10 'Warty Warthog'
Available: False
Component: main
CompDescription: No longer officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: warty-security
ParentSuite: warty
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Ubuntu 4.10 Security Updates

Suite: warty-updates
ParentSuite: warty
RepositoryType: deb
Description: Ubuntu 4.10 Updates

Suite: warty-backports
ParentSuite: warty
RepositoryType: deb
Description: Ubuntu 4.10 Backports
```

```
aramil@ubuntu:~$ sudo apt-get update && sudo apt-get upgrade && sudo do-release upgrade
Hit http://dl.google.com stable Release.gpg
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Hit http://repo.steampowered.com precise Release.gpg                           
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://dl.google.com stable Release                                        
Hit http://us.archive.ubuntu.com precise Release                               
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://repo.steampowered.com precise Release                               
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://deb.playonlinux.com precise Release.gpg                             
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://us.archive.ubuntu.com precise-updates Release                       
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://deb.playonlinux.com precise Release                                 
Hit http://files.warspear-online.com ubuntu Release.gpg                        
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise Release                               
Hit http://files.warspear-online.com ubuntu Release                            
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://alam.srb2.org lenny Release.gpg                                     
Hit http://ppa.launchpad.net precise Release                                   
Hit http://alam.srb2.org lenny Release                                         
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                          
Hit http://ppa.launchpad.net precise Release                          
Hit http://ppa.launchpad.net precise Release                          
Hit http://ppa.launchpad.net precise Release                          
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://repo.steampowered.com precise/steam Sources                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com precise-updates/main Sources                  
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://us.archive.ubuntu.com precise-updates/universe Sources              
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://security.ubuntu.com precise-security Release                        
Hit http://repo.steampowered.com precise/steam amd64 Packages         
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://deb.playonlinux.com precise/main i386 Packages                      
Hit http://archive.canonical.com precise/partner Sources                       
Ign http://repo.steampowered.com precise/steam TranslationIndex       
Ign http://deb.playonlinux.com precise/main TranslationIndex          
Hit http://archive.canonical.com precise/partner i386 Packages        
Ign http://archive.canonical.com precise/partner TranslationIndex    
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://files.warspear-online.com ubuntu/non-free i386 Packages             
Ign http://files.warspear-online.com ubuntu/non-free TranslationIndex          
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://deb.playonlinux.com precise/main Translation-en_US                  
Ign http://archive.canonical.com precise/partner Translation-en_US             
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://deb.playonlinux.com precise/main Translation-en                     
Ign http://archive.canonical.com precise/partner Translation-en                
Hit http://ppa.launchpad.net precise/main Sources                              
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Ign http://archive.canonical.com precise/partner Translation-en                
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://files.warspear-online.com ubuntu/non-free Translation-en_US         
Ign http://repo.steampowered.com precise/steam Translation-en                  
Ign http://files.warspear-online.com ubuntu/non-free Translation-en   
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Hit http://alam.srb2.org lenny/contrib Sources                        
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://alam.srb2.org lenny/contrib i386 Packages                  
Ign http://alam.srb2.org lenny/contrib TranslationIndex               
Ign http://alam.srb2.org lenny/contrib Translation-en_US              
Ign http://ppa.launchpad.net precise/main Translation-en_US           
Ign http://ppa.launchpad.net precise/main Translation-en
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://alam.srb2.org lenny/contrib Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Translation-en_US
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Hit http://security.ubuntu.com precise-security/main Sources
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit https://private-ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit https://private-ppa.launchpad.net precise Release
Hit http://ppa.launchpad.net precise/main i386 Packages               
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Translation-en_US
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit https://private-ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main Translation-en
Get:1 https://private-ppa.launchpad.net precise/main TranslationIndex [367 B]
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Hit http://security.ubuntu.com precise-security/restricted Sources
Ign http://ppa.launchpad.net precise/main Translation-en_US               
Ign http://ppa.launchpad.net precise/main Translation-en                  
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign https://private-ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Hit http://security.ubuntu.com precise-security/universe Sources
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sudo: do-release: command not found
aramil@ubuntu:~$ 


```

---

### Post by dannyboy79 on 2014-06-02
there should be a space between update-manager and the -d

---

### Post by aramil248 on 2014-06-02
it shows nothing to update

---

### Post by dannyboy79 on 2014-06-02
you'll have to wait for slickymaster as this is over my head. some config file somewhere thinks you're all updated but i can tell by your kernel that you're not running 14.04. sorry, can't help any further

---

### Post by slickymaster on 2014-06-03
So first step here, **_do a backup of all your important data_**.

Upgrades between LTS releases are not enabled by default until the first point release, 14.04.1, scheduled for July. If one chooses to upgrade before then, he can pass the -d option to the upgrade tool, running **do-release-upgrade -d**, which you already done without success. But that was probably caused by the value of the Prompt parameter in your **/etc/update-manager/release-upgrades** file.

That said, let's edit that value, changing that value so it reads _**normal**_ instead of lts. Open a terminal window and run```
gksudo geany /etc/update-manager/release-upgrades
```and change the last line from Prompt=lts to _Prompt=normal_. Save the file and close it.
Your file's content should end up like this```
# Default behavior for the release upgrader.

[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
Prompt=normal

```
Once that done, run the follwoing:```
sudo apt-get update && sudo apt-get dist-upgrade && sudo do-release-upgrade -d
```

---

### Post by aramil248 on 2014-06-03
```
aramil@ubuntu:~$ sudo do-release-upgrade -d
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                           
Get:2 Upgrade tool [1,141 kB]                                                  
Fetched 1,141 kB in 0s (0 B/s)                                                 
authenticate 'utopic.tar.gz' against 'utopic.tar.gz.gpg' 
extracting 'utopic.tar.gz'
Traceback (most recent call last):
  File "/tmp/update-manager-tSE5rF/utopic", line 3, in <module>
    from DistUpgrade.DistUpgradeMain import main
  File "/tmp/update-manager-tSE5rF/DistUpgrade/DistUpgradeMain.py", line 22, in <module>
    import apt
ImportError: No module named apt
aramil@ubuntu:~$ 


```

---

### Post by slickymaster on 2014-06-03
> **aramil248 said:**
> ```
aramil@ubuntu:~$ sudo do-release-upgrade -d
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                           
Get:2 Upgrade tool [1,141 kB]                                                  
Fetched 1,141 kB in 0s (0 B/s)                                                 
authenticate 'utopic.tar.gz' against 'utopic.tar.gz.gpg' 
extracting 'utopic.tar.gz'
Traceback (most recent call last):
  File "/tmp/update-manager-tSE5rF/utopic", line 3, in <module>
    from DistUpgrade.DistUpgradeMain import main
  File "/tmp/update-manager-tSE5rF/DistUpgrade/DistUpgradeMain.py", line 22, in <module>
    import apt
ImportError: No module named apt
aramil@ubuntu:~$ 


```

Apparently your **ubuntu-release-upgrader** package is missing the python-apt dependency. Please try the following in a terminal:```
sudo apt-get --reinstall install python-apt
```and afterwords run again```
sudo do-release-upgrade -d
```Again please post back the output you get on both commands.

---

### Post by aramil248 on 2014-06-03
ok i did both and get the same error

---

### Post by slickymaster on 2014-06-03
> **aramil248 said:**
> ok i did both and get the same error

Are you getting the exact same output? Can you please post it back here in the thread?

---

### Post by aramil248 on 2014-06-03
```
aramil@ubuntu:~$ sudo apt-get --reinstall install python-apt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/184 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 352707 files and directories currently installed.)
Preparing to replace python-apt 0.8.3ubuntu7.2 (using .../python-apt_0.8.3ubuntu7.2_i386.deb) ...
Unpacking replacement python-apt ...
Setting up python-apt (0.8.3ubuntu7.2) ...
aramil@ubuntu:~$ sudo do-release-upgrade -d
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                           
Get:2 Upgrade tool [1,141 kB]                                                  
Fetched 1,141 kB in 0s (0 B/s)                                                 
authenticate 'utopic.tar.gz' against 'utopic.tar.gz.gpg' 
extracting 'utopic.tar.gz'
Traceback (most recent call last):
  File "/tmp/update-manager-WiwMcr/utopic", line 3, in <module>
    from DistUpgrade.DistUpgradeMain import main
  File "/tmp/update-manager-WiwMcr/DistUpgrade/DistUpgradeMain.py", line 22, in <module>
    import apt
ImportError: No module named apt


```

---

### Post by slickymaster on 2014-06-03
I am not sure if it will be easy to repair the situation. I see two possible reasons for this, either your file system has errors or some update was interrupted and left a broken system.

Can you please provide the output of:```
ls -l /usr/bin/python
```

---

### Post by aramil248 on 2014-06-03
lrwxrwxrwx 1 root root 9 Jun 18  2013 /usr/bin/python -> python2.7

---

### Post by slickymaster on 2014-06-03
> **aramil248 said:**
> lrwxrwxrwx 1 root root 9 Jun 18  2013 /usr/bin/python -> python2.7

That seems to be ok.

The last thing I can think of is to try to force the upgrade using a LiveUSB. Basically all you have to do is to boot from the LiveUSB to start installing it will give a option of upgrading to 14.04, but _**you must have a functional Internet connection to do it**_. It will automatically detect installed applications and install the updated version of your applications also.

Please **DON'T FORGET TO BACKUP ALL YOUR IMPORTANT DATA BEFORE YOU DO IT**.

See [this]("http://askubuntu.com/questions/110477/how-do-i-upgrade-to-a-newer-version-of-ubuntu") if you have doubts on how to do it.

---

### Post by aramil248 on 2014-06-03
i cant boot into a liveusb on my pc

---

### Post by slickymaster on 2014-06-03
> **aramil248 said:**
> i cant boot into a liveusb on my pc

Can you be more specific on the why? No USB ports? You don't know how to change your computer BIOS settings to change the boot priority?

---

### Post by aramil248 on 2014-06-03
my bios does not support boot from usb
edit: i can use this [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) to do the upgrade

---

### Post by slickymaster on 2014-06-03
Well, that's not a major issue if you have a DVD drive. The process I mentioned in the post #37 can either be performed with a USB or with a DVD.

---

### Post by aramil248 on 2014-06-03
so im using unetbootin to reinstall ubuntu because i cant do a usb install or dvd live cd but its bin on "getting the time from a network time server" for over a hour its connected to the net and when i click on the little arrow just before it its showing "Cron[8669]: (root) CMD (  cd / && run-parts --report /etc/cron.hourly)"

---

### Post by aramil248 on 2014-06-03
ok to reinstall 14.04 what i did was use unetbootin to install ubuntu on my 2nd hd then booted that up to use unetbootin again so i can install ubuntu on my main hd wich i have not done yet because its late so tomorrow im going to do it

---

### Post by aramil248 on 2014-06-04
so after about over 4 hours i finaly got 14.04 fresh installed so im marking this as solved thanks for all of the help

---

### Post by slickymaster on 2014-06-05
Glad you got it fixed. Happy *buntuing.

---

