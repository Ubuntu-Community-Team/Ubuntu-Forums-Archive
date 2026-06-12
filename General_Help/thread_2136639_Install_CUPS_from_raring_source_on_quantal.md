---
title: "Install CUPS from raring source on quantal"
date: 2013-04-18
forum: General Help
---

### Post by Chowchilla on 2013-04-18
***IGNORE THIS AND SEE POST #5 FOR SOLUTION***

Hello!

Some of you may know there have been some issues with CUPS 1.6. Thankfully these have been resolved with 1.6.2 (see [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1069671](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1069671) for details).

Given this, I want to install 1.6.2 using the raring source (from here [http://packages.ubuntu.com/raring/cups](http://packages.ubuntu.com/raring/cups)) on my quantal Gnome install. I tried installing from source via the upstream source from cups.org (first configure/make/makeinstall, then using checkinstall) but no luck - first time seemed to install alright but lpstat was not working correctly, second time checkinstall threw an error.

Anyway, I was just hoping someone could quickly tell me the commands needed to install the raring package from the .dsc/.tar.bz2/.debian.tar.gz? I think that may install correctly given it includes ubuntu specific changes, no?

Thanks in advance.

---

### Post by Chowchilla on 2013-04-18
So I downloaded the .dsc/tar.bz2/.debian.tar.gz to a directory. Unpacked the tar.bz2 (creating folder cups-1.6.2 in same directory). Then:

```

sudo apt-get build-dep cups
dpkg-source -x cups_1.6.2-1ubuntu5.dsc
cd cups-1.6.2
dpkg-buildpackage -rfakeroot -b -d

```

Note that I added the "-d" flag for the last command in order to avoid an error about unmet dependencies, as they would be installed in this very process (cups-filters, libcupsfilters-dev I recall).

Regardless, the compilation failed:

```

make[2]: *** [check] Error 1
make[2]: Leaving directory `/home/sharifm/.builds/cups-1.6.2'
make[1]: *** [override_dh_auto_test] Error 2
make[1]: Leaving directory `/home/sharifm/.builds/cups-1.6.2'
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2

```

I had a quick gander at the error-log but it was huge and beyond my comprehension.

Anyone have any idea what's up? I know it can be done as the launchpad discussion I linked in the OP (see comment #39) indicates that the raring source can be built/installed for quantal.

---

### Post by Cheesemill on 2013-04-18
Instead of downloading the source and compiling have you tried just installing the .deb file?

There is a download link at the bottom of the page that you linked to, this should open up Software Center and use it to install the package.

---

### Post by Chowchilla on 2013-04-18
Well I had earlier tried installing the cups .deb but it has a whole host of dependencies which I'd also need to install. Which was why I though installing from source would be a better idea as it would install all the other packages too (e.g. cups-filters, libcups2,..). But I realised I only need libcups2 for my purposes (a simple ServerName entry in /etc/cups/client.conf). So I grabbed the raring deb for that, and after checking dependencies, grabbed another 5-6 debs (libgnutls26, libtasn1-3,...).

...And - success! I can now simply append "/version=1.1" to the ServerName string in the client.conf to be able to print.

---

### Post by Chowchilla on 2013-04-18
So to summarise...

Problem:

The version of libcups2 in 12.10 (1.6.1) is preventing you from accessing your print server via a simple /etc/cups/client.conf file such as this:

```

ServerName myprintserver

```

Solution:

This problem has been dealt with upstream in libcups2 (1.6.2) via a simple fix which allows you to simply append the version number to restore compatibility:

```

ServerName myprintserver/version=1.1

```

So to benefit from this we need to install the newer version which exists in raring. However due to dependency issues we will also need six other packages from raring. So grab the .deb for your architecture for all of the following and save to a directory (e.g. ~/Downloads/Debs/):

[http://packages.ubuntu.com/raring/libcups2](http://packages.ubuntu.com/raring/libcups2)
[http://packages.ubuntu.com/raring/libgnutls26](http://packages.ubuntu.com/raring/libgnutls26)
[http://packages.ubuntu.com/raring/libgnutls-dev](http://packages.ubuntu.com/raring/libgnutls-dev)
[http://packages.ubuntu.com/raring/libgnutls-openssl27](http://packages.ubuntu.com/raring/libgnutls-openssl27)
[http://packages.ubuntu.com/raring/libgnutlsxx27](http://packages.ubuntu.com/raring/libgnutlsxx27)
[http://packages.ubuntu.com/raring/libtasn1-3](http://packages.ubuntu.com/raring/libtasn1-3)
[http://packages.ubuntu.com/raring/libtasn1-3-dev](http://packages.ubuntu.com/raring/libtasn1-3-dev)

Then:

```

cd ~/Downloads/Debs/
sudo dpkg -i *.deb

```

It should install error free, resulting in no broken packages (confirm via apt-get, synaptic etc.)

Now create your client.conf as described above and confirm you can print!

---

