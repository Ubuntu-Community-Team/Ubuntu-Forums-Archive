---
title: "Updating to Wine version 20050830"
date: 2005-09-01
forum: General Help
---

### Post by Whistlez2000 on 2005-09-01
I have an issue which only appears in Ubuntu (so far), which the helpers at WineHQ suggest might be rectified by upgrading from Wine version 20050725 to the latest.

Unfortunately, the only upgrade available is Wine-20050830.tar.gz which I cannot integrate into the Synaptic Package Manager. Is there a work around (or do I have to wait for a deb package to be written as suggested in WineHQ for Ubuntu)?

Thanks for the help.

BTW: I am new to Ubuntu (or Debian), so apologies if this question is self-evident.

Dennis Mercier (Cambridge, Ontario)

---

### Post by evilghost on 2005-09-01
Don't see any deb's at [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) even Debian ones.  Looks like you'll have to wait until the .deb is built, or build one from the tgz (personally I don't know how to do it, but I know it can be done with one or two commands).

---

### Post by kagashe on 2005-09-02
Hi,
Go to:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Scroll down to the following instructions:> Building the Wine Package from Source using APT:

APT also allows easy compilation from source of a package. This is useful if there is no binary package available for your architecture, or if you wish to create a fresh .deb file from scratch. To do this, first follow the instructions for installing from the console above, except instead of running apt-get install wine run 'apt-get build-dep wine'. This will download the needed development packages for your system to make the wine package. Then, run 'apt-get --build source wine', have a snack, and wait for the compiling to finish.

To install your newly created package (which should be in whatever directory you were in when you ran apt-get --build source), run 'dpkg -i wine*.deb' as root.kagashe

---

### Post by Whistlez2000 on 2005-09-02
[QUOTE=kagashe]Hi,
Go to:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Scroll down to the following instructions:kagashe[/QUOTE]

Thank you for your prompt replies...

I have followed kagashe's advice and completed the "update" by using the identical commands in Root Console. Here's part of what I observe...

(Reading database ... 76871 files and directories currently installed.)
Preparing to replace wine 0.0.20050725-winehq-1 (using wine_0.0.20050725-winehq-1_i386.deb) ...
Unpacking replacement wine ...
Selecting previously deselected package wine-dev.
Unpacking wine-dev (from wine-dev_0.0.20050725-winehq-1_i386.deb) ...
Setting up wine (0.0.20050725-winehq-1) ...

This action has simply rebuilt the existing version of Wine, rather than the most recent release. As I originally indicated in this thread, I have downloaded the tarball (Wine-20050830.tar.gz) and am looking for help in installing it in Ubuntu 5.04. Maybe evilghost is correct, and I am at the mercy of anyone who knows how to prepare a new deb...

If anyone has any wisdom on this subject, I would be greatly indebted.

---

### Post by Havoc on 2005-09-02
Ok, here goes.

You need some development files in order to compile wine correctly.
You need the files: 

1) x-dev + dependancies (Just type "sudo apt-get install x-dev")
2) bison (sudo apt-get install bison)
3) flex (sudo apt-get install flex)

then, extract the wine source code (Wine-20050830.tar.gz) into a folder (Any folder), open that folder, and either:

1) run (in a terminal pointing into the wine folder) "./configure", then "make", then "sudo make install" in the wine folder, or

2) go into the "tools" folder located in the wine folder, open a terminal and write "wineinstall".Follow any prompt given.

Well, that's it.Both are the same, but wineinstall does configure + make + make install instaid of you.So, even if you do the second one (I recomend it), you're not missing out on a lot of stuff.

That's it!  :^o

---

### Post by Havoc on 2005-09-02
[QUOTE=Havoc]Ok, here goes.

You need some development files in order to compile wine correctly.
You need the files: 

1) x-dev + dependancies (Just type "sudo apt-get install x-dev")
2) bison (sudo apt-get install bison)
3) flex (sudo apt-get install flex)

then, extract the wine source code (Wine-20050830.tar.gz) into a folder (Any folder), open that folder, and either:

1) run (in a terminal pointing into the wine folder) "./configure", then "make", then "sudo make install" in the wine folder, or

2) go into the "tools" folder located in the wine folder, open a terminal and write "wineinstall".Follow any prompt given.

Well, that's it.Both are the same, but wineinstall does configure + make + make install instaid of you.So, even if you do the second one (I recomend it), you're not missing out on a lot of stuff.

That's it!  :^o[/QUOTE]
 Or maybe that isn't what you wanted?

---

### Post by Whistlez2000 on 2005-09-04
[QUOTE=Havoc]Or maybe that isn't what you wanted?[/QUOTE]
 Thanks Havoc,

I was successful in the first part, but after a long period (2 hrs.) the Terminal suddenly closed without completing the installation.

When I tried again, most of the process had already been completed, but I could not catch the error that was generated.

I suppose I have to wait for the deb package to be composed since I have exhausted my potential to solve this issue.

Is there anybody out there up to this?

---

### Post by Lollipop on 2005-09-04
[QUOTE=Whistlez2000]Thanks Havoc,
Is there anybody out there up to this?[/QUOTE]

Most likely it's either a missing xml package or the  ldap package is missing. I don't remember the former, but installing libldap2 and libldap2-dev might solve the problem.
  Lollipop

---

