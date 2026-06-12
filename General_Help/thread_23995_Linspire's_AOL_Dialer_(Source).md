---
title: "Linspire's AOL Dialer (Source)"
date: 2005-04-04
forum: General Help
---

### Post by CRCampbell on 2005-04-04
Can anyone tell me how I'm supposed to get this installed?

[http://software.linspire.com/pool-src/los/los-aol/](http://software.linspire.com/pool-src/los/los-aol/)

  I have no clue.  There are no instructions on how to install this.  Thanks.

---

### Post by Equalizer on 2005-05-22
have you figured out how to get this to work I too would like to use this as aol is the only isp i have access to right now

---

### Post by ewoodruf on 2005-06-11
Here's how I made this work:

Open a terminal as the super-user (sudo su)

Create a work area:
[INDENT]  Make a new directory and enter it[/INDENT]

Install dependencies manually:
   [INDENT]Install the pre-release version of python2.4-kde3:
   This link [http://linux.blogweb.de/archives/27-python-kde3.html](http://linux.blogweb.de/archives/27-python-kde3.html) explains that there   
   is a python2.4-kde package available if you add a new line to your   
   /etc/apt/sources.list.

   [INDENT]deb [http://archive.linux-server.org](http://archive.linux-server.org) hoary/$(ARCH)/[/INDENT]

   Run:
   [INDENT]apt-get update
   apt-get install python2.4-kde python2.4-dev python-qt3 penggy[/INDENT][/INDENT]

Download the source files:
  [INDENT] from [http://software.linspire.com/pool-src/los/los-dialer-aol/](http://software.linspire.com/pool-src/los/los-dialer-aol/)[/INDENT]
  [INDENT] wget [http://software.linspire.com/pool-src/los/los-dialer-aol/los-dialer-aol_0.0.6.2-0.0.0.50.linspire0.1.dsc](http://software.linspire.com/pool-src/los/los-dialer-aol/los-dialer-aol_0.0.6.2-0.0.0.50.linspire0.1.dsc)
   wget [http://software.linspire.com/pool-src/los/los-dialer-aol/los-dialer-aol_0.0.6.2-0.0.0.50.linspire0.1.tar.gz](http://software.linspire.com/pool-src/los/los-dialer-aol/los-dialer-aol_0.0.6.2-0.0.0.50.linspire0.1.tar.gz)[/INDENT]

Extract the package:
   [INDENT]dpkg-source -x los-dialer-aol_*.dsc[/INDENT]

Enter the extracted directory:
   [INDENT]cd los-dialer-aol-0.0.6.2/[/INDENT]

Edit the debian control file and change python2.3 to python2.4.
[INDENT]   The debian control file for specifying the install and build depdencies is in the
   rules directory. Edit rules/control and replace python2.3 with python2.4.[/INDENT]

Build the package:
[INDENT]dpkg-buildpackage[/INDENT]

Install the package:
[INDENT]   cd ..
   dpkg -i los-dialer-aol*.deb[/INDENT]


Run it!
[INDENT]   losaol.[/INDENT]

Some of the images are missing, probably from some linspire package or something.

---

