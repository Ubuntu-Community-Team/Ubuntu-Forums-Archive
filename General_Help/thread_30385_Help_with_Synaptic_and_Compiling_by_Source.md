---
title: "Help with Synaptic and Compiling by Source"
date: 2005-04-28
forum: General Help
---

### Post by coolbreeze on 2005-04-28
When I need a package and it's not listed in Synaptic and I can't find a .deb, I install by source (Configure, Make , Make Install) after locating a tar ball. 

 I've noticed that these packages don't appear in Synaptic after a successful install by source.  Is there a way to make Synaptic aware that the packages are now installed?

Also I've noticed that a source install doesn't see a binary install.  For example, a source install needs another package and aborts saying the package isn't installed.  Well the needed package was installed by Synaptic and works!

Any suggestions?

---

### Post by nad on 2005-04-28
A note to those of you new to compiling software from source code: The scripts referenced should read; ./configure (because your current working directory is the source directory you are working with and you wish to use this configure script), make and make install, all lowercase.

The packages don't appear in synaptic because dselect did not handle them and they do not have the structure of a deb package.

"Also I've noticed that a source install doesn't see a binary install". Once you've compiled your program you have a binary. make install is apparently throwing dependency issues.
Do you have the correct versions of the packages necessary to satisfy dependencies? Did configure and make complete without errors?

---

### Post by az on 2005-04-28
"I've noticed that these packages don't appear in Synaptic after a successful install by source. Is there a way to make Synaptic aware that the packages are now installed?"

Make them into debian packages and then build the packages.  Install those packages.  Tis is not an easy thing, but would be the only way to make synaptic see them.  Perhaps someone already made a deb package out of the software?


"Also I've noticed that a source install doesn't see a binary install. For example, a source install needs another package and aborts saying the package isn't installed. Well the needed package was installed by Synaptic and works!"

Binary packages contain only the binaries.  To compile stuff along with them, you need the -dev package that corresponds to the binary package.

For example, althoug you may have kdelibs installed, to compile something which requires kdelibs, you need kdelibs-dev.


"Any suggestions?"

Yes, enable the universe repository and then look to see if you can find a binary package of what you want.  There are 13000 packages!

---

### Post by tread on 2005-04-28
Also, if you can find an rpm package of the same application, you can convert it to deb using alien, then install it using dpkg -i filename.deb.

It also shows up as installed in synaptic then.

---

### Post by coolbreeze on 2005-04-28
Thanks nad, azz, and tread.

azz you are correct...I just used synaptic to install liblame-dev and now ./configure recognizes lame when compiling another program from source that needs lame. When only lame was installed by synaptic it wouldn't work.

---

