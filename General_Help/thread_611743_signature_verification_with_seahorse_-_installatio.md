---
title: "signature verification with seahorse - installation bug"
date: 2007-11-13
forum: General Help
---

### Post by meurrens on 2007-11-13
With Ubuntu 7.04 and seahorse installed,
you can verify a signature by a double-click on the .sig file.
No problem.

With **Ubuntu 7.10** and **seahorse** installed,
the installation 'forgot' to associate the Verification app to the .sig files.
So, you cannot usefully double-click on the file:(.

Did some of you already meet this problem ?
Please provide me with your experience so that we may transmit
eventually to the seahorse developers.

Btw, the by-pass is not too complicate:).
You need to manually associate to a .sig file the command :
**seahorse-tool --verify**

Hope that this trick may help you.
However my interest is to know if somebody already encountered the bug.

---

### Post by FuturePilot on 2007-11-13
oops. nevermind

---

### Post by meurrens on 2007-11-14
After intensive testing, the help of FuturePilot:) and the installation of the very last version 2.20.1 of seahorse,
it appears that there are 2 bugs in the installation of seahorse.
They are both related to the integration with nautilus.

Here is a complete bug report published at URL
[http://www.cgsa.net/tomboy/seahorse-bugs.html](http://www.cgsa.net/tomboy/seahorse-bugs.html)
and transmitted to the seahorse team.

You will find there and below the description of the bugs **and how to by-pass them**:).

===

There are two distinct bugs in the installation of seahorse on Ubuntu : let us call them the "asc" bug and the "sig" bug. Both are related to the integration of seahorse with nautilus. 

**Before describing the bugs, what works correctly ?** 

**the /usr/share/applications directory : **

in the /usr/share/applications , the list of desktop configuration files (they appear with a nice name, in french in my installation) include a.o. 
Decrypter un fichier (decrypt a file) : seahorse-tool --decrypt 
Importer une clef (Import a key) : seahorse-tool --import 
Verifier la signature (verify the signature) : seahorse-tool --verify 

these correspond to the files : 
seahorse-pgp-encrypted.desktop seahorse-pgp-keys.desktop seahorse-pgp-signature.desktop 

The mimeinfo.cache file includes a.o. 
application/pgp-encrypted=seahorse-pgp-encrypted.desktop application/pgp-keys=seahorse-pgp-keys.desktop application/pgp-signature=seahorse-pgp-signature.desktop 

[B]the nautilus actions that DO work : 
[/B]:)
double-click on a .pgp file : decrypt OK 
right-click on a file : you may encrypt and you may sign. 

**now, what does NOT work ? the nautilus actions that do NOT work ::(** 

double-click on an '.asc' file : the 'asc' BUG 
double-click on an '.sig' file : the 'sig' BUG 

[B]the 'asc' bug 
[/B]

appears with version 2.20 on Ubuntu 7.04 
appears with version 2.20 on Ubuntu 7.10 
appears with last version 2.20.1 on Ubuntu 7.10 

by double-clicking on the file, you get a security warning message. 
you are invited to change the extension by .pgp. 
even then, you are not able to process the file. 

opening the Properties/Open With of the file, 
you see the association with "Importer une clé (import a key)". 
You cannot add manually an association with **seahorse-tool --import** 
as this probably conflict with the existing entry. 

the by-pass is to import the key by launching seahorse. 

[B]the 'sig' bug
[/B]

does NOT appear with version 2.20 on Ubuntu 7.04 
appears with version 2.20 on Ubuntu 7.10 
appears with last version 2.20.1 on Ubuntu 7.10 
the bug is thus related to version 7.10 of Ubuntu 

the sig file is not associated with any application and you can thus not open it by a double-click. 
this make the by-pass quite easy as there is no conflict. 
Opening the Properties/Open With dialog for this file, 
we can add manually the command : **seahorse-tool --verify** 

with this by-pass, you can verify the signatures. 

**Thanks** 

thanks to Nick Bryda (aka FuturePilote on ubuntu forums) for confirming our tests on a fresh Ubuntu 7.10 installation. 
thanks to Adam Schreiber (seahorse developer) for his attention on the issue. 

**Links** 

[http://mail.gnome.org/mailman/listinfo/seahorse-list](http://mail.gnome.org/mailman/listinfo/seahorse-list) 
[http://live.gnome.org/Seahorse](http://live.gnome.org/Seahorse) 
[http://www.gnome.org/projects/seahorse/download.html](http://www.gnome.org/projects/seahorse/download.html)
[http://ftp.gnome.org/pub/GNOME/sources/seahorse/2.20/seahorse-2.20.1.tar.gz](http://ftp.gnome.org/pub/GNOME/sources/seahorse/2.20/seahorse-2.20.1.tar.gz) 

(to make sure, we have compiled and installed version 2.20.1 on Ubuntu 7.10)

---

### Post by meurrens on 2007-11-19
========================================================

**THE 'asc' BUG in seahorse**

appears with seahorse version 2.20 on Ubuntu 7.04
appears with version 2.20 on Ubuntu 7.10
appears with last version 2.20.1 on Ubuntu 7.10

This bug is partially described as :
[http://bugzilla.gnome.org/show_bug.cgi?id=458809](http://bugzilla.gnome.org/show_bug.cgi?id=458809)
and :
[https://bugs.freedesktop.org/show_bug.cgi?id=11680](https://bugs.freedesktop.org/show_bug.cgi?id=11680)
(our synthesis adds a.o. by-passes and fixes)

This report published at :
[http://ubuntuforums.org/showthread.php?t=611743&highlight=seahorse](http://ubuntuforums.org/showthread.php?t=611743&highlight=seahorse)
(in order to already make by-passes and fixes available for the Ubuntu communauty)
is discussed on the list [http://mail.gnome.org/mailman/listinfo/seahorse-list](http://mail.gnome.org/mailman/listinfo/seahorse-list)

By double-clicking on the file, you get a security warning message.
you are invited to change the extension by .pgp.
even then, you are not able to process the file.

Opening the Properties/Open With of the file,
you see the association with "Importer une clé (import a key)".
You cannot add manually an association with seahorse-tool --import
as this probably conflict with the existing entry.

Hopefully enough you can still import the key by launching seahorse.

=====

**BY-PASSING THE BUG**

rename .asc pgp key file into .pkr file
the double-click will import (silently!) the key to your key ring :)

=====

**FIXING THE BUG (for your self only : no need to be root)**

in your home directory (you must select to show hidden files),
there is a .local directory.
there you find a share directory.
within share there is a mime directory; else, create it
inside mime there is a packages directory, else create it
within packages, there is a file Override.xml (uppercase O)
If the file does not yet exist create it with the following content :

[COLOR="RoyalBlue"]<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
     <mime-type type="application/pgp-keys">
          <comment>ascii armoured pgp key</comment>
          <glob pattern="*.asc"/>
     </mime-type>
</mime-info>[/COLOR]

if the file already existed, simply add the mime-type :

     [COLOR="RoyalBlue"]<mime-type type="application/pgp-keys">
          <comment>ascii armoured pgp key</comment>
          <glob pattern="*.asc"/>
     </mime-type>[/COLOR]

in the console, do the following :
[COLOR="RoyalBlue"]$ update-mime-database ~/.local/share/mime/[/COLOR]

a lot of files are now created (or updated) in your ~/.local/share/mime/

double-click on asc file containing an ascii armoured pgp key :
seahorse will silently import the key.
the problem is solved :)

=====

**REMAINING MINOR PROBLEM :**

The key importation is completely silent. So you don't know if the importation was successfull or not.
However in the message
[http://mail.gnome.org/archives/seahorse-list/2007-September/msg00000.html](http://mail.gnome.org/archives/seahorse-list/2007-September/msg00000.html)
with subject ANNOUNCEMENT: Seahorse 2.20
the list of Changes between 1.0 and 2.20
announced a.o. "Give more detail for imported keys. [Adam Schreiber]"

=====

**REMAINING MAJOR PROBLEM**

The choice, for pgp keys, of the extensions .pkr and .skr instead of .asc is problematic.
.skr , as suggested by the name, was the extension for the secret key ring of the windows version of PGP.
.pkr was for public key ring.
(btw, these extensions are not used by gnupg)
.asc is for ascii armoured things. It is widely used to distribute pgp (or gpg) public keys or to backup
private keys.
The choices expressed in file /usr/share/mime/packages/seahorse.xml
also reflected in file usr/share/mime/packages/freedesktop.org.xml
are a really serious problem.
(btw, there is no file : /usr/share/mime-info/seahorse.mime or seahorse.keys )
Mind that, when exporting a key, seahorse still suggest the extension .asc (and is right to do so!)
We must find a definitive solution so that a 'normal' user may simply click on an .asc file
(e.g. freshly downloaded from the web) to import the key.
I suppose the seahorse developers will take the measures after the bug :
[https://bugs.freedesktop.org/show_bug.cgi?id=11680](https://bugs.freedesktop.org/show_bug.cgi?id=11680)
will be carried on by freedesktop.org

---

### Post by lee_connell on 2008-04-06
i don't see this as reported as a bug in launchpad, has anyone done this?

---

