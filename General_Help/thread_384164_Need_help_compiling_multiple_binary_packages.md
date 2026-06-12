---
title: "Need help compiling multiple binary packages"
date: 2007-03-14
forum: General Help
---

### Post by armalite on 2007-03-14
I'm trying to compile a multiple binary package, namely banshee, for Feisty. I did a 

```
$ apt-get source banshee
```

and found that the same source is used by 2 subpackages: banshee and banshee-daap, as written in debian/control. 

I have read and i have followed the Ubuntu Packaging Guide, I added a patch found on gnome bugzilla, modified changelog accordingly and I compiled Banshee using debuild. All things went fine.

Anyway, there are some things i don't understand. Before posting here i googled/forumed around and found nothing useful, even on Debian documentation.

The first thing i noticed is: the banshee deb i built has already daap built-in, so there's no need of a banshee-daap package. To install my custom banshee I have to remove completely the old one, and make sure that also banshee-daap is uninstalled (ok, there's a correct dependency here so no worries).

But, what if i want to build my custom banshee .deb without daap support, and then build my banshee-daap plugin? How can i do that? Ubuntu Packaging Guide don't tell how to manage multiple binary packages.

I think things should be quite easy and straightforward, maybe an option to tell to debuild or dpkg-buildpkg, or something like that since the package is already debianized and already included in Edgy/Feisty. But i have no clue on how to do this, and i don't know how to force debuild or other tools to build banshee-daap. I already read the man pages of the tools above and found nothing interesting about that issue. 

A workaround should be "compile as I already did and forget banshee-daap", but i don't want that, since banshee isn't the only one multiple binary package (among others, maybe also network-manager if i remember right), and i would like to be able to manage such packages.

I think that Ubuntu Packaging Guide is missing some information about how to let pbuilder/fakeroot meet the build dependencies for a given package. It only tells how to setup a minimal installation, but no help is given in order to install build dependencies on fakeroot. After googling a bit i found this command:

```
$ sudo /usr/lib/pbuilder/pbuilder-satisfydepends
```

but i'm unsure if it is the correct one, since it is an executable found in /usr/lib, and maybe it can be called from pbuilder with some option, but i don't know which one.
 
Another thing i would like to find in Ubuntu Packaging Guide should be a chapter on how to upgrade a package to a new upstream release. There's a little chapter on how to use dpatch to apply patches written by me to a given package version, but don't fit too well for upstream releases (obviously).  I found on Debian docs the tool uupdate, maybe some examples on uupdate could fit good in Ubuntu docs too.

As you see i'm not an expert in building packages, but i'd like to learn something more, since i don't want to use the old plain 

```
./configure --prefix=/usr
make
sudo make install
```

to try new versions or new software on my pc. I'd like to go to a more Debian (and Ubuntu, too!) way.
Any help is appreciated.

---

### Post by ihavenoname on 2007-03-25
I'm bumping this because I too am interested in learning about this.

Edit: I think a very long method (very hackish too) might be to build the program twice, once with daap support and another time without. Make a patch of the differances, and make a deb that extracts the contents of that patch into the proper directories. I'm not sure if that works, or how well it works or even if it's a good practice but it's worth a try. You could also get the source debs of packages that fit the bill and see how it's done. I don't think it's a command I think it's something in the debian rules file or something (though I might be wrong).

---

### Post by armalite on 2007-03-29
Seems that the only way to build multiple packages is using pbuilder, provided that you have already builded the source package (either downloaded or debianized a source tarball).

The guideline is as follow:

[LIST]
[*]debianize the source tarball with dh_make (if not already debianized) and modify the needed files in debian/source (i still don't know how to create a multiple binary package from scratch);
[*]build the source package with debuild -S;
[*]compile the binary package(s) with

```
# sudo pbuilder build *.dsc
```

[/LIST]

This will compile every binary package in the source package, setting up fakeroot by automagically installing build-time dependencies (provided debian/control is correct), and will cleanup once building is finished.

The resulting .debs will be in **/var/cache/pbuilder/result** directory.

I can't build multi-binary packages with debuild -B. As far as I know it builds only the main package (modifying directory name to change this behaviour doesn't help).

---

