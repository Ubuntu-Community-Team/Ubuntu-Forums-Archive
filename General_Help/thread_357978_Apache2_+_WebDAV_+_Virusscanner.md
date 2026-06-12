---
title: "Apache2 + WebDAV + Virusscanner"
date: 2007-02-10
forum: General Help
---

### Post by betatux on 2007-02-10
Hi People,

I'm looking for a good solution to secure the apache2 webserver so it can scan for virusses in files that are being downloaded and uploaded from/to a WebDAV directory.

So far i've tried these software packages:

1. mod_streamav ([http://streamav.sourceforge.net/](http://streamav.sourceforge.net/))
2. mod_clamav ([http://software.othello.ch/mod_clamav/](http://software.othello.ch/mod_clamav/))
3. mod_security ([http://www.modsecurity.org/](http://www.modsecurity.org/))
4. http antivirus proxy ([http://www.server-side.de/index.htm](http://www.server-side.de/index.htm))
5. dansguardian webfiltering ([http://dansguardian.org/](http://dansguardian.org/))

The only software package that does virusscanning for both download and upload through WebDAV is mod_streamav but this module is not quite good enough. 
The other packages work only though a webbrowser connection.

My Question: Does anyone know of other software packages that can be used to scan files for virusses for WebDAV ?

---

