---
title: "Perl CPAN installation error"
date: 2006-11-26
forum: General Help
---

### Post by ramshorn on 2006-11-26
I want to install AudioFile::Identify::MusicBrainz::Query, which
is evidently not available via the synaptic package manager in Dapper
Drake. So I tried,

sudo perl -MCPAN -e 'install AudioFile::Identify::MusicBrainz::Query'

This initally failed due to various dependencies, which I was able
to resolve with the Synaptic Package Manager.

Now the installation fails with the rather unhelpful statement: 

CPAN.pm: Going to build   T/TO/TOMI/AudioFile-Identify-MusicBrainz-0.4.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for AudioFile::Identify::MusicBrainz
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible


Obviously, if the makefile is no good, then there is a problem.
But the error message gives me no hint whatsoever as to what I need
to do to resolve the problem. Any ideas?

---

### Post by ramshorn on 2006-12-02
I am still attempting to install some perl modules that are evidently
not available from the Synaptic Package Manager. This has
led me to direct use of CPAN. Initial attempts using CPAN returned
the suggestion that I install Bundle::CPAN. So I tried

       sudo perl -MCPAN -e shell

and then,

       cpan> install Bundle::CPAN

and this retuned the error, 

Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running make for P/PM/PMQS/Compress-Zlib-2.001.tar.gz
  Is already unwrapped into directory /home/cpease/.cpan/build/Compress-Zlib-2.001

  CPAN.pm: Going to build P/PM/PMQS/Compress-Zlib-2.001.tar.gz

    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible


I have also tried to install other perl modules using a
similar method, and I have yet to install a single module successfully
with this method. Installation via the Synaptic Package Manager
works fine, but my ultimate goal is to install some perl modules
containing TRM support, and this evidently requires a mp3 decoder,
which I gather has been disabled in the trm modules available from the
Synaptic Package Manager. 

I initially I thought that the problem was specific to the particular TRM support modules
I was attempting to install. But now with the failure of the
Bundle::CPAN module, it appears that the problem is more general.

I'd really appreciate any hints as to what I need to do to. I understand
that I need somehow to do a successful make. But the error message
provides not the slightest hint of what I need to do to accomplish
this.

---

### Post by hmaldonado on 2007-03-23
It seems that some Perl modules need to be compiled requiring some C header files.

I experienced the same problems you had described and after installing the libc6-dev package every new module could be installed smoothly.

sudo apt-get install libc6-dev

Good luck

---

### Post by yurtboy on 2007-11-13
this helped me too
sudo apt-get install libssl-dev

---

### Post by tr333 on 2007-11-14
It looks like you might not have GNU Make installed.
```
sudo apt-get install build-essential
```
After installing this, you will need to configure the CPAN shell to find 'make'.
You can either remove the ~/.cpan directory or run "o conf init" and then "o conf commit" from the CPAN shell to redo the configuration.

---

