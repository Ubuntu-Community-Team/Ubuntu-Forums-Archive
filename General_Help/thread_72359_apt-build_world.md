---
title: "apt-build world"
date: 2005-10-06
forum: General Help
---

### Post by Ryujin on 2005-10-06
I have been trying to use apt-build world, yes I know it is experimental and dangerous, but being an old Gentoo guy I have to try it.  I have been using the howto here: [http://julien.danjou.info/article-apt-build.html](http://julien.danjou.info/article-apt-build.html) 
but I can't find the mandatory README.Debian file it wants me to read, does anyone know more about this?

---

### Post by Ryujin on 2005-10-06
"bump"

I know this is a vauge question so I will be patient, I still have't found the solution myself, thanks!!!

---

### Post by Kyral on 2005-10-06
do a locate apt-build. Should show up somewhere in the output.

This seems sketchy....

---

### Post by az on 2005-10-06
[QUOTE=Ryujin]I have been trying to use apt-build world, yes I know it is experimental and dangerous, but being an old Gentoo guy I have to try it.  I have been using the howto here: [http://julien.danjou.info/article-apt-build.html](http://julien.danjou.info/article-apt-build.html) 
but I can't find the mandatory README.Debian file it wants me to read, does anyone know more about this?[/QUOTE]

Look at the contents of the package
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=apt-build&version=hoary&arch=all](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=apt-build&version=hoary&arch=all)

You can also do 

dpkg -L apt-build


Ususally documentation is in /usr/share/doc/(package)

---

### Post by jimcooncat on 2005-10-06
omg, *funroll-loops *is back! Oh yes, I gotta remember I switched to Ubuntu to be more productive. :-\" 
Actually, this helps to answer a question I was looking for this morning -- if I make a change to the source code of a program, can I easily recompile and repackage it to be easily distributable. 
Looks like I found a motherload on info, the Debian Reference:
[http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-source](http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-source)
> 
2.2.13 Building binary packages from a source package
For a package foo, you will need all of foo_*.dsc, foo_*.tar.gz, and foo_*.diff.gz to compile the source (note: there is no .diff.gz for a Debian native package).
Once you have them, if you have the dpkg-dev package installed, the command
$ dpkg-source -x foo_version-revision.dsc
will extract the package into a directory called foo-version.
Issue the following command to build the binary package:
$ cd foo-version
$ su -c "apt-get update ; apt-get install fakeroot"
$ dpkg-buildpackage -rfakeroot -us -uc
Then,
# su -c "dpkg -i ../foo_version-revision_arch.deb"
to install the newly built package

---

### Post by Ryujin on 2005-10-06
Thanks!!  I am embarased that I overlooked those search meathods, I will put a howto in tips and tricks once I work out any more issues

---

