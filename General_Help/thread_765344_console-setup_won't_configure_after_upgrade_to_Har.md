---
title: "console-setup won't configure after upgrade to Hardy"
date: 2008-04-24
forum: General Help
---

### Post by Ivo Moelans on 2008-04-24
I upgraded from Gutsy to Hardy today and everything seems to be fine except that console-setup won't configure and as a result ubuntu-minimal won't configure either.
After *sudo dpkg --configure -a* I get this output:

   [INDENT][I] Setting up console-setup ( 1.21ubuntu8 ) ...
    /var/lib/dpkg/info/console-setup.config: eval: line 1158: unexpected EOF while looking for matching `"'
    dpkg: error processing console-setup (--configure):
    subprocess post-installation script returned error exit status 2
    dpkg: dependency problems prevent configuration of ubuntu-minimal:
    ubuntu-minimal depends on console-setup; however:
    Package console-setup is not configured yet.
    dpkg: error processing ubuntu-minimal (--configure):
    dependency problems - leaving unconfigured
    Errors were encountered while processing:
    console-setup
    ubuntu-minimal

[/I][/INDENT]

Anybody suggestions? It doesn't seem to be a major problem but it seems to prevent e.g. emerald settings and it is annoying.

---

### Post by cgalpin on 2009-05-28
This should do it

sudo dpkg --purge ubuntu-minimal
sudo dpkg --purge console-setup

hth
charles

---

