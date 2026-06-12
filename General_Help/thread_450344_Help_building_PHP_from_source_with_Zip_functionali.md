---
title: "Help building PHP from source with Zip functionality"
date: 2007-05-21
forum: General Help
---

### Post by bluegecko73 on 2007-05-21
Does anyone know how to get PHP built with Zip support?

I'm running PHP 5.1.2 on Dapper Drake as a LAMP installation and I'm trying to use the Zip functionality on my website to make my downloads more portable, but it doen't seem to be built in.

On windows, you just enable the use of the dll library, but in Linux it seems to need a recompile and I don't seem to be making any sense of how to do this.

I came across a page that details how to add in [MSSQL Support]("http://pintmaster.com/20060530/how-to-compile-mssql-support-into-php-in-ubuntu-dapper-drake/"), so I tried to follow the relevant steps from that, which were:

- apt-get  install dpkg-dev
- apt-get source php5
- updating the debian/rules file with --enable-zip (as per the PHP zip documentation page)
- apt-get build-dep php5
- apt-get dpkg-buildpackage

It all built fine. I installed from the .deb files (well, the ones I deemed relevant), and copied over the libphp5.so into the apache modules directory. After a restart, it still didn't work.
My site just bombs whenever I try and create the ZipArchive class (a try/catch fails to prevent this too!).

I noticed that the php source directory didn't have an ext/zip directory so I tried to add it, taking teh code from the lastest source I found on the php website, but that fails when I try to build because it seems to realise it wasn't there before and can't do a diff. This must be part of the dpgk build process. No idea if this can be turned off either.

So I'm now stumped as to how I'm supposed to get this working.

There are references to the PECL zip extension, which I'm not sure if its an alternative or the same thing, but PEAR fails to find the package. There is however another PEAR zip archive extension, which I may have to revert to if I can't get this compiled.

Can anyone point me in the right direction with this?

---

### Post by KingJohn on 2007-09-07
Did you ever get this built?  Can anyone else give me a hand on how to get php-zip functionality enabled for Ubuntu 6.06 server?

---

### Post by bluegecko73 on 2007-09-07
I never did get it built unfortunately.
I switched over to using the PEAR Archive_Zip library instead which worked ok.

I had a HD failure at some point though so I took the opportunity to upgrade to feisty which seemed to come with the zip functionality built in and switched back, probably just to save me the effort of having to install the PEAR libs again, although they were quite easy to install and use (once I found the documentation).

If you want to give the PEAR lib a try, according to the notes I made at the time I just ran:

[INDENT]sudo apt-get install php-pear[/INDENT]

followed by

[INDENT]sudo pear install Archive_Zip-0.1.1[/INDENT]

The versions may have changed by now.
Can't remember fully, but you may need to add a path to the pear libs manually in your php.ini (unless the installer does it for you).

You just then need to add: 

[INDENT]require_once( 'Archive/Zip.php' );[/INDENT]

in your script to use the class, such as: 

[INDENT]$zip = new Archive_Zip( $archiveFN );[/INDENT]


Hope this helps in some way.

---

