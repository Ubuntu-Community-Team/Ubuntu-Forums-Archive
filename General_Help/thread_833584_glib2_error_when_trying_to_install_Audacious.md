---
title: "glib2 error when trying to install Audacious"
date: 2008-06-18
forum: General Help
---

### Post by tsdemented on 2008-06-18
I just got Linux on Sunday, so I am very new to it. I am trying to install Audacious. I typed ./configure in the terminal, and it did a bunch of stuff and then gave me this message:

checking for GLIB... no
configure: error:
Cannot find Glib2! If you are using binary packages based system, check that you
have the corresponding -dev/devel packages installed.

I'm using the 2.6.24-18-generic kernel (I'm not sure if that is relevant).

I installed these already from synpatic: glibc-doc, libc6, libc6-pic, and libglib 1.2-dev. That's everyone that showed up with a search for "glib2".

Does anyone know what's up?

I tried the Audacious documentation but did not find anything.

Thank you,

Tom

---

### Post by ad_267 on 2008-06-18
Why are you trying to compile audacious?

It is far easier to just install the package from the Ubuntu repositories.

You can type "sudo apt-get install audacious" or install it from the synaptic package manager by going to System - Administration - Synaptic package manager or from Add/Remove Programs.

Read this for more info: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Or click on the help button and go to "Adding and Removing Software"

---

### Post by tsdemented on 2008-06-18
Thanks, that worked perfectly, and that's a really great link for newbies like me.

---

### Post by ad_267 on 2008-06-18
Cheers, installing stuff seems to be quite a problem for people new to Ubuntu and Linux as it is a lot different to in Windows. I find that once you understand the difference it's actually a lot easier to install stuff.

If you find something isn't available from the Ubuntu repositories or any other repository then you may be able to find a .deb file which is a debian package (similar to a .exe in Windows) at somewhere like [http://www.getdeb.net/](http://www.getdeb.net/). Only for very new or obscure software should you have to compile source code.

---

### Post by ad_267 on 2008-06-18
Also, if you want to play mp3s you might need to install the ubuntu-restricted-extras package. Not sure if this is needed for audacious but it is for rhythmbox. Read this: [http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats)

---

### Post by beerslayer on 2012-03-26
I realize this is an old thread, but it still seemed like the best place to add this comment:

Why install from source?  In this case, because the repository is SO out-of-date.  The version of Audacious in the Ubuntu repository is 2.5.3, but the latest release is 3.2.1.  There are many new features in the latest release.  I cannot install it from any third-party repository I've found (including webupd8).  The only way I can see to get the latest release onto my laptop (running Kubuntu 10.04 (lucid)) is to compile from source.

At which point, I run into the same problem as the OP.

---

