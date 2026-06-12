---
title: "Unable to install NoMachine on Ubuntu 13.04"
date: 2013-09-26
forum: General Help
---

### Post by nbokare2 on 2013-09-26
I wanted to install NoMachine on my Ubuntu 13.04 but I'm unable to. Below are the complete output messages:

```
$ sudo /usr/NX/scripts/setup/nxnode --install
NX> 700 Starting: install node operation at: Thu Sep 26 12:47:00 2013.
NX> 700 Autodetected system 'debian'.
NX> 700 Install log is '/usr/NX/var/log/install'.
NX> 700 Creating configuration in /usr/NX/etc/node.cfg.
NX> 700 Inspecting local CUPS environment.
NX> 700 Generating CUPS entries in: /usr/NX/etc/node.cfg.
NX> 700 WARNING: Cannot find file: printers.conf.
NX> 700 WARNING: Please verify your CUPS configuration.
NX> 700 WARNING: Cannot validate license file.
NX> 700 Installation of NX node was completed with warnings..
NX> 700 Please review the install log '/usr/NX/var/log/install'.
NX> 700 for further details..
NX> 700 Showing file: /usr/NX/share/documents/node/cups-info

 CUPS Printing Backend

 The NX Node setup procedure could not detect your "CUPS"
 installation: either CUPS  is not installed on your system
 or it was installed in a non-standard path. CUPS is needed
 in order to enable printing support in your NX system.
 Please note that you can enable  printing support for your
 NX system at any time; to do this make sure  that you have
 CUPS installed then run:

   /usr/NX/scripts/setup/nxnode --nxprintsetup <pathname>

 to specify the location of the CUPS root path. 
NX> 700 Bye.

$ sudo /usr/NX/scripts/setup/nxserver --install
NX> 700 Installing: server at: Thu Sep 26 12:47:23 2013.
NX> 700 Autodetected system: debian.
NX> 700 Install log is: /usr/NX/var/log/install.
NX> 700 Creating configuration file: /usr/NX/etc/server.cfg.
NX> 700 WARNING: Cannot validate license file.
NX> 700 WARNING: Cannot validate node license file.
NX> 700 WARNING: Error when trying to connect to NX server, error is:
NX> 700 WARNING: /usr/NX/scripts/setup/nxserver: 1: /usr/NX/scripts/setup/nxserver: /usr/NX/bin/nxssh: not found.
NX> 700 WARNING: nxsetup cannot validate the sanity of the current installation:
NX> 700 WARNING: the current system or NX configuration could be broken.
NX> 700 WARNING: If difficulties arise (for example sessions cannot be started),
NX> 700 WARNING: it is advisable that you try to uninstall the NX server and the
NX> 700 WARNING: NX client packages then install them again.
NX> 700 WARNING: Search also the NoMachine Knowledge Base at the URL below:
NX> 700 WARNING: [http://www.nomachine.com/kb](http://www.nomachine.com/kb)
NX> 700 WARNING: for common errors encountered when performing a software update
NX> 700 WARNING: and the related hints on how to solve them..
NX> 700 Installation of NX server was completed with warnings.
NX> 700 Please review the install log '/usr/NX/var/log/install'
NX> 700 for further details.
NX> 700 Showing file: /usr/NX/share/documents/server/install-notices

<some 50 line text here about "Server keys" etc.>

$ ls -l /usr/NX/scripts/setup/nxserver /usr/NX/scripts/setup/nxserver /usr/NX/bin/nxssh
-rwxr-xr-x 1 root root 319460 Jun 17  2011 /usr/NX/bin/nxssh
-rwxr-xr-x 1 root root 109258 May 19  2012 /usr/NX/scripts/setup/nxserver
-rwxr-xr-x 1 root root 109258 May 19  2012 /usr/NX/scripts/setup/nxserver


```

While installing the server, it says "/usr/NX/bin/nxssh: not found". But as shown above, if I do an "ls -l" on that script I can see that script. Unable to identify what exavtly the issue is.

---

### Post by dshgna on 2013-09-29
Hi!
Are you installing the server as a normal user? It may be due to a permission issue of your [COLOR=#000000]/usr/NX/bin/nxssh file, as it has root privileges.[/COLOR]

---

