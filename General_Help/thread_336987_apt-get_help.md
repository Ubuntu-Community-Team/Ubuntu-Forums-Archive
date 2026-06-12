---
title: "apt-get help"
date: 2007-01-12
forum: General Help
---

### Post by pak33m on 2007-01-12
Hello,

There is a certain package that I don't want to upgrade among other packages that I do want to upgrade when I run apt-get upgrade.  This certain package is the Opera browser that I upgrade manaully with dpkg through weekly builds, but the canonical repository in from my sources.list contains a new release that I don't need.

Is there a switch with apt-get that will allow me to de-select the certain package, but still install the other packages? 

I've read through both the Ubuntu & Debian apt get How To, to no avail.

Amy help would be much appreciated.

---

### Post by ejjenkins on 2007-01-12
I got this from:

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

Looks like it will do the trick.

You may have occasion to modify something in a package and don't have time or don't want to port those changes to a new version of the program. Or, for instance, you may have just upgraded your Debian distribution to 3.0, but want to continue with the version of a certain package from Debian 2.2. You can "pin" the version you have installed so that it will not be upgraded. 

Using this resource is simple. You just need to edit the file /etc/apt/preferences. 

The format is simple: 

     Package: <package>
     Pin: <pin definition>
     Pin-Priority: <pin's priority>
Each entry must be separated from any other entries by a blank line. For example, to keep package sylpheed that I have modified to use "reply-to-list" at version 0.4.99, I add: 

     Package: sylpheed
     Pin: version 0.4.99*

---

### Post by mjm115 on 2007-01-12
You could try commenting out the repository in your sources.list or:

> echo packagename hold | dpkg --set-selections

Replace packagename with opera, and it will put a hold on the package and prevent it from changing.  To take the package off hold:

> echo packagename install | dpkg --set-selections

---

### Post by pak33m on 2007-01-12
Thank you both for your quick responses.

The latter suggestion worked better for me.

I was unable to correctly configure the preferences file.  I created the preferences file & then added the following lines:

Package: opera
Pin: 9.10

After that I ran apt-get upgrade, but the opera package was still displayed in the list of upgraded packages.

I'll have to read more into the apt get How To again.

Thank you again.

---

### Post by EnderTheThird on 2007-01-12
You might need the asterisk (*) after the version number like ejjenkins suggested.  A lot of times the versions that apt-get/Synaptic sees includes some other junk after the usual 9.10 jumble that *we* use when referring to the version.

---

