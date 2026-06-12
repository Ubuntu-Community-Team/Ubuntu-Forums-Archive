---
title: "dpkg errors"
date: 2013-04-29
forum: General Help
---

### Post by Sourmiloko on 2013-04-29
Okay so, if I try to install anything i get this dpkg error; 

dpkg: error processing sgml-data (--configure):
 package sgml-data is not ready for configuration
 cannot configure (current status `half-installed')
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of docbook-xml:
 docbook-xml depends on sgml-data (>= 2.0.2); however:
  Package sgml-data is not installed.


dpkg: error processing docbook-xml (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdoctools:
 kdoctools depends on docbook-xml; however:
  Package docbook-xml is not configured yet.


dpkg: error processing kdoctools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs5-plugins:
 kdelibs5-plugins depends on kdoctools (= 4:4.10.2-0ubuntu2); however:
  Package kdoctools is not configured yet.


dpkg: error processing kdelibs5-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-runtime:
 kde-runtime depends on kdelibs5-plugins (>= 4:4.10.2); however:
  Package kdelibs5-plugins is not configured yet.


dpkg: error processing kde-runtime (--confiNo apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already
       No apport report written because MaxReports is reached already
                                                                     No apport report written because MaxReports is reached already
                                                   No apport report written because MaxReports is reached already
                                 No apport report written because MaxReports is reached already
               No apport report written because MaxReports is reached already
                                                                             No apport report written because MaxReports is reached already
                                                           No apport report written because MaxReports is reached already
                                         gure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of k3b:
 k3b depends on kde-runtime; however:
  Package kde-runtime is not configured yet.


dpkg: error processing k3b (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of k3b-i18n:
 k3b-i18n depends on k3b; however:
  Package k3b is not configured yet.


dpkg: error processing k3b-i18n (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-kde-en:
 language-pack-kde-en depends on k3b-i18n; however:
  Package k3b-i18n is not configured yet.


dpkg: error processing language-pack-kde-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qapt-batch:
 qapt-batch depends on kde-runtime; however:
  Package kde-runtime is not configured yet.


dpkg: error processing qapt-batch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-debug-installer:
 kubuntu-debug-installer depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kubuntu-debug-installer depends on qapt-batch; however:
  Package qapt-batch is not configured yet.


dpkg: error processing kubuntu-debug-installer (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sgml-data
 docbook-xml
 kdoctools
 kdelibs5-plugins
 kde-runtime
 k3b
 k3b-i18n
 language-pack-kde-en
 qapt-batch
 kubuntu-debug-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

Whats weird is that it looks like its having issues with Kubuntu files? I'm running the latest Ubuntu 13.04?

---

### Post by Sourmiloko on 2013-04-29
bump

---

### Post by diesch on 2013-04-29
What does
```
sudo dpkg --configure --pending
```
print?

---

### Post by Sourmiloko on 2013-04-29
Okay here is what is printed. 

```
dpkg: dependency problems prevent configuration of docbook-xml:
 docbook-xml depends on sgml-data (>= 2.0.2); however:
  Package sgml-data is not installed.


dpkg: error processing docbook-xml (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdoctools:
 kdoctools depends on docbook-xml; however:
  Package docbook-xml is not configured yet.


dpkg: error processing kdoctools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs5-plugins:
 kdelibs5-plugins depends on kdoctools (= 4:4.10.2-0ubuntu2); however:
  Package kdoctools is not configured yet.


dpkg: error processing kdelibs5-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-runtime:
 kde-runtime depends on kdelibs5-plugins (>= 4:4.10.2); however:
  Package kdelibs5-plugins is not configured yet.


dpkg: error processing kde-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-debug-installer:
 kubuntu-debug-installer depends on kde-runtime; however:
  Package kde-runtime is not configured yet.


dpkg: error processing kubuntu-debug-installer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of k3b:
 k3b depends on kde-runtime; however:
  Package kde-runtime is not configured yet.


dpkg: error processing k3b (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qapt-batch:
 qapt-batch depends on kde-runtime; however:
  Package kde-runtime is not configured yet.


dpkg: error processing qapt-batch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of k3b-i18n:
 k3b-i18n depends on k3b; however:
  Package k3b is not configured yet.


dpkg: error processing k3b-i18n (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-kde-en:
 language-pack-kde-en depends on k3b-i18n; however:
  Package k3b-i18n is not configured yet.


dpkg: error processing language-pack-kde-en (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 docbook-xml
 kdoctools
 kdelibs5-plugins
 kde-runtime
 kubuntu-debug-installer
 k3b
 qapt-batch
 k3b-i18n
 language-pack-kde-en




```

---

### Post by Sourmiloko on 2013-05-02
bump again

---

### Post by majorbullet on 2013-05-02
Have you made any changes to repositories recently.  I triggered a bunch of dependency problems when I deactivated an ubuntu repository, and tried to revert to a previous version of an installed program.

---

### Post by schragge on 2013-05-02
Try to re-install *sgml-data*:
```

sudo apt-get --reinstall install sgml-data
```

---

### Post by Sourmiloko on 2013-05-05
OMG IT WORKED! S[COLOR=#000000]chragge your a genius! Thanks so much! [/COLOR]

---

