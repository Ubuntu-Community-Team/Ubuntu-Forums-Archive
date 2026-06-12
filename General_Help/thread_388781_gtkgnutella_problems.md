---
title: "gtkgnutella problems"
date: 2007-03-19
forum: General Help
---

### Post by hendoc on 2007-03-19
Gnutella just stopped opening. I installed it on my 2nd Ubuntu machine, and neither will it open on that machine. You think maybe I got a bad update?

---

### Post by lloyd_b on 2007-03-20
Could you run the "gtk-gnutella" command from a terminal window, and post the output here?  Also, could you specify which version of Gtk-Gnutella that you're running?

With various versions, there have been a number of bugs that could cause this type of problems.  Knowing the version and seeing that output will make it a lot easier to diagnose what's going on.

Lloyd B.

---

### Post by hendoc on 2007-03-20
hendoc@Exena:~$ gtk-gnutella
07-03-20 05:42:25 (MESSAGE): language code: "en"
07-03-20 05:42:25 (MESSAGE): using locale character set "UTF-8"
07-03-20 05:42:25 (MESSAGE): primary filename character set "UTF-8"
07-03-20 05:42:25 (MESSAGE): gtk-gnutella/0.96.1 (2006-02-22; GTK2; Linux i686)
07-03-20 05:42:25 (MESSAGE): D-BUS set up and ready for use.
07-03-20 05:42:25 (MESSAGE): Sent D-BUS signal 'Events': started
07-03-20 05:42:25 (WARNING): [hosts] retrieving from "/home/hendoc/.gtk-gnutella/hosts.orig" instead
07-03-20 05:42:25 (WARNING): [hosts] retrieving from "/home/hendoc/.gtk-gnutella/ultras.orig" instead
07-03-20 05:42:25 (WARNING): [hostile IP addresses] unable to retrieve: no alternate locations known
07-03-20 05:42:25 (WARNING): [Bogus IP addresses] trying to load from alternate locations...
07-03-20 05:42:25 (WARNING): [Bogus IP addresses] retrieving from "/usr/share/gtk-gnutella/bogons.txt" instead
07-03-20 05:42:25 (WARNING): [Geographic IP mappings] trying to load from alternate locations...
07-03-20 05:42:25 (WARNING): [Geographic IP mappings] retrieving from "/usr/share/gtk-gnutella/geo-ip.txt" instead
07-03-20 05:42:25 (WARNING): [Favorite web icon] trying to load from alternate locations...
07-03-20 05:42:25 (WARNING): [Favorite web icon] retrieving from "/usr/share/gtk-gnutella/favicon.png" instead
07-03-20 05:42:25 (WARNING): [Robot exclusion] trying to load from alternate locations...
07-03-20 05:42:25 (WARNING): [Robot exclusion] retrieving from "/usr/share/gtk-gnutella/robots.txt" instead
07-03-20 05:42:25 (WARNING): [Host Whitelist] unable to retrieve: no alternate locations known
07-03-20 05:42:25 (WARNING): searches file does not exist: /home/hendoc/.gtk-gnutella/searches.xml
07-03-20 05:42:25 (WARNING): retrieving searches from /home/hendoc/.gtk-gnutella/searches.xml.orig instead

*** ANCIENT VERSION DETECTED! ***

Sorry, this program is too ancient to run without
an explicit user action: If it's not possible to upgrade
you may edit the file

        /home/hendoc/.gtk-gnutella/config_gnet

and set the variable "ancient_version_force" to
"gtk-gnutella/0.96.1 (2006-02-22; GTK2; Linux i686)".

You will then be able to run this version forever, but
please consider upgrading, as Gnutella is an evolving
network in which ancient software is less useful or even
harmful!

*** EXITING ***

07-03-20 05:42:26 (WARNING): trapped foreign exit(), cleaning up...
07-03-20 05:42:26 (WARNING): idtable_destroy: destroying table with 263 ids
07-03-20 05:42:26 (WARNING): cleanup all done.
07-03-20 05:42:25 (WARNING): adns_do_transfer: EOF (read)
hendoc@Exena:~$ 

I can update it from here. but the one one my celeron machine just came from the repository last night. Didn't think it could be that old.

---

### Post by lloyd_b on 2007-03-20
Well, at least it provides instructions on how to force it to work:
> Sorry, this program is too ancient to run without
an explicit user action: If it's not possible to upgrade
you may edit the file

/home/hendoc/.gtk-gnutella/config_gnet

and set the variable "ancient_version_force" to
"gtk-gnutella/0.96.1 (2006-02-22; GTK2; Linux i686)".

You will then be able to run this version forever, but
please consider upgrading, as Gnutella is an evolving
network in which ancient software is less useful or even
harmful!

0.96.1 is quite old (more than a year old, IIRC).  The current stable version (0.96.3) is about 4 months old.  I guess the folks that maintain the repos simply aren't keeping up with this project.

Here's a link:
_[COLOR="Blue"][SourceForge - Gtk-Gnutella]("http://sourceforge.net/project/showfiles.php?group_id=4467")[/COLOR]_

There's a .deb for 0.96.2, which is quite a bit newer than what's in the repos.  Unfortunately, there's no .deb for 0.96.3, which is the current version.  If you want to run that one, you'll need to compile it yourself.

So, there are three choices for you:
1.  Modify the config_gnet file, and force 0.96.1 to run for you.
2.  Download and install 0.96.2 from the SourceForge .deb
3.  Download and compile 0.96.3 from the SourceForge .tar.bz2

Actually, there's a fourth choice - download and compile 0.96.4u, which is the unstable development code, via Subversion.  This is what I do, but I'd recommend against it unless you want to help with the development - the unstable version does tend to develop bugs.

Lloyd B.

---

### Post by crusstt on 2007-03-21
The same thing happened to me last week where it stopped opening. I uninstalled my current gtk-gnutella via synaptic then reinstalled with a 0.96.3 deb I found. I don't remember where I got it but I found another link to one here 
[http://ftp.unixdev.net/pub/debian-udev/pool/main/g/gtk-gnutella/](http://ftp.unixdev.net/pub/debian-udev/pool/main/g/gtk-gnutella/)

It's the same file size as what I installed and I had no dependency issues and it works fine. You could give that a shot if you don't want to compile.

Please let me know if I'm doing anything wrong here. This is not only my first post in this forum, but my first post in any forum. Just thought it was about time I started helping out.

---

