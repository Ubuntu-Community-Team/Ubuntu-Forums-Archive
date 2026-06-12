---
title: "Can anyone explain what's wrong with Bundle::CPAN?"
date: 2008-05-29
forum: General Help
---

### Post by Cronjob on 2008-05-29
So, first thing I did after a new xubuntu install is run cpan and then do a 'install Bundle::CPAN'. However, at the end, it complains as follows:

**Can't call method "value" on an undefined value at /usr/share/perl5/IO/Uncompress/RawInflate.pm line 64.**

The very little I could find regarding this is a bug in **libio-compress-zlib-perl 2.010-1** (bug [#482056]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=482056")).

While it is the SAME error message, you'll note that bug is for the apt-get package named libio-compress-zlib-perl. That should have NOTHING to do with what is retrieved by the cpan utility. Besides, the bug is regarding 2.010-1 which is in testing or unstable and obviously shouldn't be part of xubuntu by default (presumign we were even dealinb with libio-compress-zlib-perl, which we aren't since we're using the cpan utility).

However, since the current version of libio-compress-zlib-perl in the repository is 2.08, I installed that and then ran cpan. And it complained that it needed to be 2.011 -- which, of course, fails when it tries to install that from CPAN.

The debian bug says it is going to be fixed in 2.011 but the problem is in 2.010. So presuming that the same bug was actually in the perl module itself, then why would it still exist in 2.011, if that's the version it's fixed in?!

So maybe I misunderstand that bug? The bug report looks very clearly to me to be against the debian package and NOT against the actual perl module. So why is the perl module not working? I can't seem to find a way to get an earlier version of Bundle::CPAN to install. I just want to get this garbage installed so I can have a fresh working dev environment again.

Any thoughts? Going nuts here.

---

### Post by garyo on 2008-05-30
Having same problem here, Ubuntu 8.04 server, everything up to date, but CPAN shell no longer works, same error.

---

### Post by garyo on 2008-05-30
I installed some upstream Debian updates and that fixes the bug.  Here are the steps.  Add to your /etc/apt/sources.list:

```
  deb http://http.us.debian.org/debian sid main
```

Then do the following as root:
```
  apt-get update
  apt-get install libio-compress-zlib-perl_2.011

```

That updates that lib and its dependencies to 2.011, after which CPAN works fine.  After it's finished installing, you probably want to remove the sid line from sources.list to avoid picking up anything else from there.

---

### Post by garyo on 2008-05-30
Actually, this turned out NOT to be a good idea -- it upgraded my perl to 5.10, which causes other problems.  So do not do this.  A better solution is to install the perl modules with CPAN instead, following this:

[http://nxadm.wordpress.com/2008/05/30/cpan-on-ubuntu-fails-on-bug-iouncompressrawinflatepm-solution/#more-51](http://nxadm.wordpress.com/2008/05/30/cpan-on-ubuntu-fails-on-bug-iouncompressrawinflatepm-solution/#more-51)

---

### Post by ibuclaw on 2008-05-30
> **garyo said:**
> Actually, this turned out NOT to be a good idea -- it upgraded my perl to 5.10, which causes other problems.  So do not do this.  A better solution is to install the perl modules with CPAN instead, following this:

[http://nxadm.wordpress.com/2008/05/30/cpan-on-ubuntu-fails-on-bug-iouncompressrawinflatepm-solution/#more-51](http://nxadm.wordpress.com/2008/05/30/cpan-on-ubuntu-fails-on-bug-iouncompressrawinflatepm-solution/#more-51)

Read this page about [Pinning in Apt]("http://wiki.debian.org/AptPinning").

To setup the preferences file for both synaptic and apt-get, type in this:
```

sudo touch /var/lib/synaptic/preferences
sudo ln -s /var/lib/synaptic/preferences /etc/apt/preferences

```
Then type in:
```
sudo gedit /etc/apt/preferences
```
And putting something like this in the file
```

Package: perl
Pin: version 5.8.8-12
Pin Priority: 1001

```
will prevent perl from being upgraded at all (and will force downgrade the version if it is of a higher number).

It will save you alot of headaches in the future if you decide to mix stable with unstable repositories again

Regards
Iain

---

### Post by Cronjob on 2008-05-30
I can sort of understand why the apt-get version fails (well, not really since the version which fails isn't the current version that is installed - the failed version never made it out of unstable as far as I know). What I still don't understand is why the latest version that cpan itself downloads fails as well. Also unsure why there doesn't seem to be much (if any) discussion about this anywhere since this has been going on for a couple of weeks or more.

---

### Post by MSBF on 2008-06-02
I'm having heaps of problems as well. Followed the above  instructions and I still have the error appear. Any other theories? Thanks for the time.

---

### Post by Cronjob on 2008-06-02
I'm not exactly sure how the sources work in Ubuntu, so I went back to a Debian dev environment. The zlib library was just moved into the testing branch (Lenny) as of a couple days ago, so it can now be used. Unfortunately, 5.10 is the default Perl in Lenny, so I'm not sure what kind of consequences I might suffer because of that.

I still do not understand why the apt-get version of the package is necessary since as far as I can tell, it is included IN Bundle::CPAN and so should be downloaded and installed BY CPAN rather than by apt-get. Unless I misunderstand and the zlib library we're installing in the OS has NOTHING to do with perl packages (but in my life, I've never installed it manually before - I just fired up CPAN, installed Bundle::CPAN and went off on my merry way).

So... I guess the only answer I can offer right now is to use Debian. Use the testing (Lenny) branch and accept Perl 5.10 -- though I guess you might be able to keep it at Perl 5.8, but I'm not sure if other things will break due to some sort of dependence on 5.10 (I would presume not, but have not tried).

---

### Post by discorsage on 2008-06-28
I had similar problems, but they were all solved after I installed build-essential.

---

