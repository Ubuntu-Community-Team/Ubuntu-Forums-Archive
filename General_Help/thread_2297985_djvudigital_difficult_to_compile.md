---
title: "djvudigital: difficult to compile"
date: 2015-10-08
forum: General Help
---

### Post by ATSC on 2015-10-08
Hello there :-)


I'm trying to compile djvudigital as per [these]("http://ubuntuforums.org/showthread.php?t=1935973&p=11740664&viewfull=1#post11740664") instructions but I'm stuck at step 6 with this error:
```
can't find file to patch at input line 14
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|From cd317aa5d5040e212de676e93babe069a71bc6c0 Mon Sep 17 00:00:00 2001
|From: Timo Gurr <tgurr@exherbo.org>
|Date: Thu, 9 Feb 2012 00:35:49 +0100
|Subject: [PATCH] Upstream removed gserror.h in gs905 (commit 8f2ecf4).
|
|---
| gdevdjvu.c |    1 -
| 1 files changed, 0 insertions(+), 1 deletions(-)
|
|diff --git a/gdevdjvu.c b/gdevdjvu.c
|index d94f0d5..33dbed8 100644
|--- a/gdevdjvu.c
|+++ b/gdevdjvu.c
--------------------------
File to patch: 


```

It would be much appreciated, if someone could help me out here. :-)

---

### Post by steeldriver on 2015-10-08
Did you try building it without that step? The post you linked is over 3 years old - unless you are building a correspondingly old version of the software it's likely the patch is no longer relevant.

---

### Post by ATSC on 2015-10-13
**/edit: solved**


> **steeldriver said:**
> The post you linked is over 3 years old -  unless you are building a correspondingly old version of the software  it's likely the patch is no longer relevant.

Good call, I didn't notice that. In fact I mixed something different totally up, oh well... :oops:


I'm still having problems though, related to the usage of that "build-gsdjvu" script:

The readme says:

> 1) Download all necessary source files.

    - Create a directory 'BUILD'
    - Download the following files into this directory:
        
        ghostscript-8.64.tar.bz2
        [optional] ghostscript-fonts-std-8.11.tar.gz 
        [optional] jpegsrc.v6b.tar.gz 
        [optional] libpng-1.2.6.tar.gz
        [optional] openjpeg-2.0.0.tar.gz
        [optional] zlib-1.2.1.tar.gz
      
      These files can be found under 
        <http://ghostscript.com/releases/>

      If you do not provide the fonts file, ghostscript 
      tries to find the fonts in standard places on your system.
      Of course things will break badly if it does not find them.

      If you do not provide any of the last three files,
      jpegsrc, libpng , openjpeg, and zlib, the building script will
      attempt to use the system wide libraries.
      This only works if the corresponding development files
      are installed on your system. This usually is better 
      because the resulting program benefits from the latest 
      installed versions (including bug fix and security patches.)

      The ghostscript versions suggested above were current at
      the time gsdjvu was released. You can try to build gsdjvu 
      using newer versions, but do not take it for granted.
      
      Note that the file "ghostscript-fonts-std-8.11.tar.gz"
      is needed for versions of ghostscript earlier than 8.57.


2) Run the shell script 'build-gsdjvu'.
   Use the full pathname.
   Example:
...
..
.

I did not include ghostscript as it was already on my system with a  newer release, the same goes for libpng and zlib. I confirmed the  location of the required files and the terminal-window simply closed. I  tried it again, this time with all programs that were asked for but once again - no luck I  downloaded current releases of all programs. Perhaps I really need the  versions that the readme suggests?

---

