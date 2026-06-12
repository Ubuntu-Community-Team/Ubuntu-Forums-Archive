---
title: "obsolete and buggy version of gpa (GNU privacy assistant)"
date: 2007-11-10
forum: General Help
---

### Post by meurrens on 2007-11-10
gpa

This is our tomboy note on gpa provided 'as is' 
and published at [http://www.cgsa.net/tomboy/gpa.html](http://www.cgsa.net/tomboy/gpa.html)
It is the synthesis of a discussion on the list Gpa-dev mailing list in november 2007:
[email]Gpa-dev@gnupg.org[/email]
[http://lists.gnupg.org/mailman/listinfo/gpa-dev](http://lists.gnupg.org/mailman/listinfo/gpa-dev)

Frontends for GNUPG

[http://www.gnupg.org/(fr)/related_software/frontends.html](http://www.gnupg.org/(fr)/related_software/frontends.html)

• We use the enigmail extension for the mail client Thunderbird.

4 stand alone applications are distributed with Ubuntu :

• GnomePGP  [http://www.geocities.com/SiliconValley/Chip/3708/gpgp/gpgp.html](http://www.geocities.com/SiliconValley/Chip/3708/gpgp/gpgp.html) (broken link!) we were not able to run this application (?)

• KGpg , a GNUPG front end for KDE, well integrated with Konqueror

• Seahorse , a Gnome frontend for GNUPG that integrates with nautilus (you may encrypt, decrypt or sign a file by a right click on the file name) [http://www.gnome.org/projects/seahorse/](http://www.gnome.org/projects/seahorse/) We use the version 2.20 provided with Ubuntu. In november 2007, the last stable is 2.20.1

• GPA (Gnu Privacy Assistant) is a graphical user interface for the GNU Privacy Guard (GnuPG). It integrates a file manager convenient to manage your crypted files, signatures, etc. The obsolete and buggy version 0.7.0 comes with Ubuntu. We use version 0.7.6 (last stable in november 2007). This very note tells why and how. 

GNU Privacy Assistant (gpa) , a frontend to GNUPG

[http://www.gnupg.org/(fr)/related_software/gpa/index.html](http://www.gnupg.org/(fr)/related_software/gpa/index.html)

Buggy version of gpa delivered with Ubuntu

The last version of GNU/Linux Ubuntu 7.10 (gutsy, The Gutsy Gibbon, october 2007)
still comes with gpa 0.7.0. (which is 4 years old!)

We know there is bug in this version : gpa freezes when trying
to encrypt to several keys. This bug was fixed in version 0.7.5 of 2007-02-26

This is a severe bug as we often need to encrypt to several keys (generaly the key of a colleague and our own key)

On [http://www.gnupg.org/](http://www.gnupg.org/) in the french version, the page
[http://www.gnupg.org/(fr)/related_software/gpa/index.html](http://www.gnupg.org/(fr)/related_software/gpa/index.html)
is partially obsolete as it suggests the download from
[ftp://ftp.gnupg.org/gcrypt/alpha/gpa](ftp://ftp.gnupg.org/gcrypt/alpha/gpa) 
of a so-called last gpa source beeing 0.7.5 of 2007-02-26

However, the english version
[http://www.gnupg.org/(en)/related_software/gpa/index.html](http://www.gnupg.org/(en)/related_software/gpa/index.html)
properly recommands the development site
[http://wald.intevation.org/projects/gpa/](http://wald.intevation.org/projects/gpa/)
where the source of version 0.7.6 is effectively available. 


Installation of gpa on Ubuntu 7.10 (gutsy )

Download gpa-0.7.6.tar.bz2 from [http://wald.intevation.org/projects/gpa/](http://wald.intevation.org/projects/gpa/)
Unpack in a directory gpa-0.7.6 (supposed to be on your Desktop in our example)

An install file explains how to configure, compile and install
gpa but, of course, does not provide specific explanations
(which dependencies ?) for Ubuntu. Here they are.

Dependencies

To compile the gpa source on Ubuntu (Desktop edition)
some installations must first be done thru the synaptic tool
(in the System/Administration menu) or by a few
$ apt-get install 

The following packages are needed (their dependencies will be loaded automatically)

As for most of the compiles, you need :
• the make utility (probably already installed)
• the compilers gcc (probably already installed) and g++ 
• the library libc6-dev (otherwise you get the famous "C compiler cannot create executables" message)
Regarding more specifically gpa, you need :
• zlib1g-dev (zlib library used by gpa)
• libgtk2.0-dev (GTK+ used by gpa)
• libgpgme11-dev (GPGME used by gpa)
• and, of course, gnupg (already installed if you installed gpa 0.7.0 and/or thunderbird-enigmail)

If you fail to install these packages, the "./configure" will provide error messages. 
It's however more confortable to install the dependencies listed here before trying the "./configure".

You can install all these dependencies (and their own dependencies) in one step by :
$ sudo apt-get install make gcc g++ libc6-dev zlib1g-dev libgtk2.0-dev libgpgme11-dev gnupg
or, using the easy way :
$ sudo apt-get build-dep gpa

Configure, compile, install

By default, gpa (0.7.6) installs it self in /usr/local/bin/gpa while the initial application (0.7.0)  installed by Ubuntu was in /usr/bin/gpa . So, in this case, don't forget to update the path of the application in the definition of the main menu (System/Preferences)
To simply replace the program in /usr/bin , use the --prefix=/usr option as shown below.
 
Finally, the compilation, install and test of gpa 0.7.6 is relatively simple.
Supposing gpa-0.7.6 is the directory where you unpacked gpa,
the following steps will probably do :

$ sudo apt-get build-dep gpa
$ cd gpa-0.7.6
$ ./configure --prefix=/usr
$ make
$ sudo make install

Btw, the good news is that the bug related to the encryption to several keys is effectively fixed in version 0.7.6

Here is a different suggestion by Marcus :

$ apt-get install dpkg-dev
$ apt-get source gpa
$ tar xjf gpa-0.7.6.tar.bz2
$ cp -r gpa-0.7.0/debian gpa-0.7.6
$ cd gpa-0.7.6
$ emacs debian/changelog  # Optional, see below for an example entry
$ dpkg-buildpackage -b -uc -rfakeroot  # Or -rsudo
$ dpkg -i ../gpa_0.7.6-0.0.deb

Example entry for debian/changelog (the version 0.0 makes sure that
official packages will replace this one).

gpa (0.7.6-0.0) feisty; urgency=low

  * Local update to 0.7.6.

 -- Your Name <your_user@localhost>  Tue, 06 Nov 2007 15:16:00 +0200


Installation of gpa on Ubuntu 7.04 (feisty)

Regarding Ubuntu 7.04 (feisty, The Feisty Fawn, the previous version of Ubuntu), 
the installation of gpa is a little bit more complicate than on Ubuntu 7.10
The reason is that gpa 0.7.6 (as well as gpa 0.7.5) relies on version 1.1.5 of gpgme,
while only the version 1.1.2 of gpgme is provided with Ubuntu 7.04.
(Ubuntu 7.10 already comes with version 1.1.5)
So you first need to install a recent version of gpgme (GPGME "Gnupg made easy")
[http://www.gnupg.org/related_software/gpgme/](http://www.gnupg.org/related_software/gpgme/)
Furthermore, to install gpgme 1.1.5 , you need to previously install gpgsm.
[http://www.gnupg.org/(en)/documentation/manuals/gnupg/GPGSM-Protocol.html](http://www.gnupg.org/(en)/documentation/manuals/gnupg/GPGSM-Protocol.html)
Finally, here are the steps needed to install gpa 0.7.6 on Ubuntu 7.04

Step by step :

Download gpa-0.7.6.tar.bz2 from [http://wald.intevation.org/projects/gpa/](http://wald.intevation.org/projects/gpa/)
Unpack in a directory gpa-0.7.6 (supposed to be on your Desktop in our example)
Download gpgme-1.1.5.tar.gz from [ftp://ftp.gnupg.org/gcrypt/gpgme/](ftp://ftp.gnupg.org/gcrypt/gpgme/)
Unpack in a directory gpgme-1.1.5

$ sudo apt-get build-dep gpa
$ sudo apt-get install gpgsm
$ cd Desktop/gpgme-1.1.5
$ ./configure --prefix=/usr
$ make
$ sudo make install
$ cd ../gpa-0.7.6
$ ./configure --prefix=/usr
$ make
$ sudo make install

The gpa entry will appear in your main menu (under "accessories"); the program is at /usr/bin/gpa

Remark

The 2 first apt-get entries can eventually be replaced by the explicit :
$ sudo apt-get install make gcc g++ libc6-dev zlib1g-dev libgtk2.0-dev libgpgme11-dev gnupg gpgsm
but be carefull for typo's...
See above section on Ubuntu 7.10 to read more about each of these dependencies.

Misc links
 
[http://doc.ubuntu-fr.org/gnupg](http://doc.ubuntu-fr.org/gnupg)

---

### Post by meurrens on 2007-11-11
_I have been asked why I haved installed **both** seahorse and gpa._

Both softwares provide **GnuPG keys** management.
*Seahorse* also allows management of [B]SSH keys.
[/B]
*Seahorse* probably provides a more convenient way to manage GnuPG keys management.
E.g. you are able to **retrieve keys** from servers by searching on a name.:)
*Gpa* is limited to searching by key ID.:(

*Seahorse* integrates well with **nautilus**. So that you can encrypt, decrypt or sign
a file by a simple right click within nautilus.:)
However, these operations are not very precise (see below the 'sign' example):(

*Gpa* allows file encryption, decryption or signing thru an internal **file manager**.
These operations are precise.
E.g. when you decide to sign a file, you are able to decide the type of signature :)
(my choice is generally an external armoured file), while you are not able to
reach this precision with *seahorse* :(.

---

### Post by meurrens on 2007-11-11
[B]Additionaly, regarding .asc (and evenually .zip) files
[/B]
With **seahorse**, 
you can backup your 2 key rings into a single zip file
you can export a set of public keys into an .asc file
you can NOT export your private key(s) into an .asc file (use gpa to do this):(
of course, you can import from an .asc file

With **gpa**, 
you can NOT backup your 2 key rings into a single tar.gz or other file (use seahorse to do this):(
you can export one public key into an .asc file
you should be able to export a set of public keys but currently there is a BUG (thus, use seahorse to do this):(
you can export (backup) one private key into an .asc file
if you have multiple private keys, you can NOT export them all into a single .asc file (wait for a next version of gpa or seahorse ?):(
of course, you can import from an .asc file

With **KGpg**,
you can NOT backup your 2 key rings into a single tar.gz or other file (use seahorse to do this):(
you can export a set of public keys into an .asc file
you can NOT export your private key(s) into an .asc file (use gpa to do this):(
of course, you can import from an .asc file

---

### Post by meurrens on 2007-11-12
About the comparison between seahorse and gpa,
and the reason to install both.

With **seahorse**, you can (easely by a right click) sign a file
(signature will be a separate binary file)
but there is NO tool to verify a signature.:(

With **gpa**, you can also sign a file (you need to open gpa and then its file manager, etc)
(signature may be what you decide)
AND there is also a tool (in the file manager) to verify a signature.

---

### Post by meurrens on 2007-11-13
Sorry:confused:.

In my previous messages regarding the comparison between **gpa** and **seahorse**, there are two errors :

Yes:), in seahorse, you CAN export a private key to an ascii file.
On the "My Personal Keys" tab, double click on the key you want to export, select the details tab, click the export button.

Yes:), in seahorse, you CAN verify a signature.
Doubleclick on the .sig file.
This works in Ubuntu 7.04.
Seems there is a problem in Ubuntu 7.10

Details at URL [http://www.cgsa.net/tomboy/gpa-v-seahorse.html](http://www.cgsa.net/tomboy/gpa-v-seahorse.html)

---

