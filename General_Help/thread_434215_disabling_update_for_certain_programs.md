---
title: "disabling update for certain programs"
date: 2007-05-05
forum: General Help
---

### Post by ry4nolson on 2007-05-05
i recently applied a patch to the tilda 0.9.4 source to allow real transparency for use with beryl and installed it.

now Update Manager always tells me that there is a new version of tilda but its the same version 0.9.4.

i tried doing the force version in synaptic and it still shows the update

i also tried the aptitude hold command but update manager still keeps showing there to be an upgrade for it but i don't want it.

what can i do to keep it from showing in update manager.

---

### Post by afoglia on 2007-05-05
I think this a job for apt-pinning.  I've never needed it myself, but check section 3.10 of the Apt-HowTo at [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html").

---

### Post by Thingymebob on 2007-05-05
**man apt_preferences**
> You may have occasion to modify something in a package and don't have time or don't want to port those changes to a new version of the program. Or, for instance, you may have just upgraded your Debian distribution to 3.0, but want to continue with the version of a certain package from Debian 2.2. You can "pin" the version you have installed so that it will not be upgraded.

Using this resource is simple. You just need to edit the file /etc/apt/preferences.

The format is simple:

     Package: <package>
     Pin: <pin definition>
     Pin-Priority: <pin's priority>

Each entry must be separated from any other entries by a blank line. For example, to keep package sylpheed that I have modified to use "reply-to-list" at version 0.4.99, I add:

     Package: sylpheed
     Pin: version 0.4.99*

Note that I used an * (asterisk). This is a "wildcard"; it say that I want that this "pin" to be valid for all versions beginning with 0.4.99. This is because Debian versions its packages with a "Debian revision" and I don't want to avoid the installation of these revisions. So, for instance, versions 0.4.99-1 and 0.4.99-10 will be installed as soon as they are made available. Note that if you modified the package you won't want to do things this way.

The pin priority helps determine whether a package matching the "Packages:" and "Pin:" lines will be installed, with higher priorities making it more likely that a matching package will be installed. You can read apt_preferences(7) for a thorough discussion of priorities, but a few examples should give the basic idea. The following describes the effect of setting the priority field to different values in the sylpheed example above.

1001
    Sylpheed version 0.4.99 will never be replaced by apt. If available, apt will install version 0.4.99 even if it would replace an installed package with a higher version. Only packages of priority greater than 1000 will ever downgrade an existing package. 

1000
    The effect is the same as priority 1001, except that apt will refuse to downgrade an installed version to 0.4.99 

990
    Version 0.4.99 will be replaced only by a higher version available from a release designated as preferred using the "APT:: Default-Release" variable (see How to keep a mixed system, Section 3.8, above). 

500
    Any version higher than 0.4.99 of sylpheed which is available from any release will take preference over version 0.4.99, but 0.4.99 will still be preferred to a lower version. 

100
    Higher versions of sylpheed available from any release will take preference over version 0.4.99, as will any installed higher version of slypheed; so 0.4.99 will be installed only if no version is installed already. This is the priority of installed packages. 

-1
    Negative priorities are allowed as well, and prevent 0.4.99 from ever being installed. 

A pin can be specified on a package's version, release or origin.

Pinning on a version, as we have seen, supports literal version numbers as well as wildcards to specify several versions at one time.

Option release depends on the Release file from an APT repository or from a CD. This option may be of no use at all if you're using package repositories that don't provide this file. You may see the contents of the Release files that you have on /var/lib/apt/lists/. The parameters for a release are: a (archive), c (components), v (version), o (origin) and l (label).

An example:

     Package: *
     Pin: release v=2.2*,a=stable,c=main,o=Debian,l=Debian
     Pin-Priority: 1001

In this example, we chose version 2.2* of Debian (which can be 2.2r2, 2.2r3 -- this accommodates "point releases" that typically include security fixes and other very important updates), the stable repository, section main (as opposed to contrib or non-free) and origin and label Debian. Origin (o=) defines who produced that Release file, the label (l=) defines the name of the distribution: Debian for Debian itself and Progeny for Progeny, for example. A sample Release file:

     $ cat /var/lib/apt/lists/ftp.debian.org.br_debian_dists_potato_main_binary-i386_Release
     Archive: stable
     Version: 2.2r3
     Component: main
     Origin: Debian
     Label: Debian
     Architecture: i386


---

### Post by dcstar on 2007-05-05
> **ry4nolson said:**
> i recently applied a patch to the tilda 0.9.4 source to allow real transparency for use with beryl and installed it.

now Update Manager always tells me that there is a new version of tilda but its the same version 0.9.4.

i tried doing the force version in synaptic and it still shows the update
.........
what can i do to keep it from showing in update manager.

Use the "Lock version" feature in Synaptic.

---

