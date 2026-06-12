---
title: "dpkg was interrupted you must manually run sudo dpkg --configure -a"
date: 2017-06-23
forum: General Help
---

### Post by kadalyst on 2017-06-23
Hi All,

I need some assistance if possible, I have a pcduino running ubuntu 12 and I was trying to install python 3.5 in order to be able to run some discord boots off the duino. I didn't realise that the duino had booted to the 2GB internal flash storage instead of my 256gb SD card and partway through the install I got an error message that I was out of storage.

I rebooted into the SD card and made sure it's what I'm using now, but I'm stuck getting this dpkg error and I can't get around it in order to continue to install and/or reinstall python 3.5. I've tried using 

```
sudo apt-get install -f
``` and I've tried using ```
sudo dpkg --configure -a
``` but they don't seem to work, I can't stop it from throwing an error at dpkg and not going further.

I've attached the output, any help on fixing this so that I can get python 3.5 installed would be greatly appreciated!

```
: Sub-process /usr/bin/dpkg returned an error code (1)ubuntu@ubuntu:~$ sudo dpkg --configure -a
Setting up ghc (7.4.1-1ubuntu2) ...
ghc-pkg: /var/lib/ghc/package.conf.d/mtl-2.0.1.0.conf: hGetContents: invalid argument (invalid byte sequence)
dpkg: error processing ghc (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libghc-hunit-dev:
 libghc-hunit-dev depends on libghc-base-dev-4.5.0.0-e98ea; however:
  Package libghc-base-dev-4.5.0.0-e98ea is not installed.
  Package ghc which provides libghc-base-dev-4.5.0.0-e98ea is not configured yet.
dpkg: error processing libghc-hunit-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libghc-hunit-prof:
 libghc-hunit-prof depends on libghc-hunit-dev (= 1.2.4.2-2build1); however:
  Package libghc-hunit-dev is not configured yet.
dpkg: error processing libghc-hunit-prof (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libghc-text-dev:
 libghc-text-dev depends on libghc-array-dev-0.4.0.0-3cf1b; however:
  Package libghc-array-dev-0.4.0.0-3cf1b is not installed.
  Package ghc which provides libghc-array-dev-0.4.0.0-3cf1b is not configured yet.
 libghc-text-dev depends on libghc-base-dev-4.5.0.0-e98ea; however:
  Package libghc-base-dev-4.5.0.0-e98ea is not installed.
  Package ghc which provides libghc-base-dev-4.5.0.0-e98ea is not configured yet.
 libghc-text-dev depends on libghc-bytestring-dev-0.9.2.1-e17f0; however:
  Package libghc-bytestring-dev-0.9.2.1-e17f0 is not installed.
  Package ghc which provides libghc-bytestring-dev-0.9.2.1-e17f0 is not configured yet.
 libghc-text-dev depends on libghc-deepseq-dev-1.3.0.0-6c19e; however:
  Package libghc-deepseq-dev-1.3.0.0-6c19e is not installed.
  Package ghc which provides libghc-deepseq-dev-1.3.0.0-6c19e is not configured yet.
 libghc-text-dev depends on libghc-ghc-prim-dev-0.2.0.0-bd29c; however:
  Package libghc-ghc-prim-dev-0.2.0.0-bd29c is not installed.
  Package ghc which provides libghc-ghc-prim-dev-0.2.0.0-bd29c is not configured yet.
 libghc-text-dev depends on libghc-integer-gmp-dev-0.4.0.0-ec87c; however:
  Package libghc-integer-gmp-dev-0.4.0.0-ec87c is not installed.
  Package ghc which provides libghc-integer-gmp-dev-0.4.0.0-ec87c is not configured yet.
dpkg: error processing libghc-text-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libghc-bytestring-show-dev:
 libghc-bytestring-show-dev depends on libghc-array-dev-0.4.0.0-3cf1b; however:
  Package libghc-array-dev-0.4.0.0-3cf1b is not installed.
  Package ghc which provides libghc-array-dev-0.4.0.0-3cf1b is not configured yet.
 libghc-bytestring-show-dev depends on libghc-base-dev-4.5.0.0-e98ea; however:
  Package libghc-base-dev-4.5.0.0-e98ea is not installed.
  Package ghc which provides libghc-base-dev-4.5.0.0-e98ea is not configured yet.
 libghc-bytestring-show-dev depends on libghc-binary-dev-0.5.1.0-d353b; however:
  Package libghc-binary-dev-0.5.1.0-d353b is not installed.
  Package ghc which provides libghc-binary-dev-0.5.1.0-d353b is not configured yet.
 libghc-bytestring-show-dev depends on libghc-bytestring-dev-0.9.2.1-e17f0; however:
  Package libghc-bytestring-dev-0.9.2.1-e17f0 is not installed.
  Package ghc which provides libghc-bytestring-dev-0.9.2.1-e17f0 is not configured yet.
 libghc-bytestring-show-dev depends on libghc-containers-dev-0.4.2.1-7c545; however:
  Package libghc-containers-dev-0.4.2.1-7c545 is not installed.
  Package ghc which provides libghc-containers-dev-0.4.2.1-7c545 is not configured yet.
 libghc-bytestring-show-dev depends on libghc-integer-gmp-dev-0.4.0.0-ec87c; however:
  Package libghc-integer-gmp-dev-0.4.0.0-ec87c is not installed.
  Package ghc which provides libghc-integer-gmp-dev-0.4.0.0-ec87c is not configured yet.
dpkg: error processing libghc-bytestring-show-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libghc-bytestring-nums-dev:
 libghc-bytestring-nums-dev depends on libghc-base-dev-4.5.0.0-e98ea; however:
  Package libghc-base-dev-4.5.0.0-e98ea is not installed.
  Package ghc which provides libghc-base-dev-4.5.0.0-e98ea is not configured yet.
 libghc-bytestring-nums-dev depends on libghc-bytestring-dev-0.9.2.1-e17f0; however:
  Package libghc-bytestring-dev-0.9.2.1-e17f0 is not installed.
  Package ghc which provides libghc-bytestring-dev-0.9.2.1-e17f0 is not configured yet.
 libghc-bytestring-nums-dev depends on libghc-containers-dev-0.4.2.1-7c545; however:
  Package libghc-containers-dev-0.4.2.1-7c545 is not installed.
  Package ghc which provides libghc-containers-dev-0.4.2.1-7c545 is not configured yet.
dpkg: error processing libghc-bytestring-nums-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libghc-polyparse-dev:
 libghc-polyparse-dev depends on libghc-base-dev-4.5.0.0-e98ea; however:
  Package libghc-base-dev-4.5.0.0-e98ea is not installed.
  Package ghc which provides libghc-base-dev-4.5.0.0-e98ea is not configured yet.
 libghc-polyparse-dev depends on libghc-bytestring-dev-0.9.2.1-e17f0; however:
  Package libghc-bytestring-dev-0.9.2.1-e17f0 is not installed.
  Package ghc which provides libghc-bytestring-dev-0.9.2.1-e17f0 is not configured yet.
 libghc-polyparse-dev depends on libghc-text-dev-0.11.1.13-0fafa; however:
  Package libghc-text-dev-0.11.1.13-0fafa is not installed.
  Package libghc-text-dev which provides libghc-text-dev-0.11.1.13-0fafa is not configured yet.
dpkg: error processing libghc-polyparse-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libghc-cereal-dev:
 libghc-cereal-dev depends on libghc-array-dev-0.4.0.0-3cf1b; however:
  Package libghc-array-dev-0.4.0.0-3cf1b is not installed.
  Package ghc which provides libghc-array-dev-0.4.0.0-3cf1b is not configured yet.
 libghc-cereal-dev depends on libghc-base-dev-4.5.0.0-e98ea; however:
  Package libghc-base-dev-4.5.0.0-e98ea is not installed.
  Package ghc which provides libghc-base-dev-4.5.0.0-e98ea is not configured yet.
 libghc-cereal-dev depends on libghc-bytestring-dev-0.9.2.1-e17f0; however:
  Package libghc-bytestring-dev-0.9.2.1-e17f0 is not installed.
  Package ghc which provides libghc-bytestring-dev-0.9.2.1-e17f0 is not configured yet.
 libghc-cereal-dev depends on libghc-containers-dev-0.4.2.1-7c545; however:
  Package libghc-containers-dev-0.4.2.1-7c545 is not installed.
  Package ghc which provides libghc-containers-dev-0.4.2.1-7c545 is not configured yet.
 libghc-cereal-dev depends on libghc-ghc-prim-dev-0.2.0.0-bd29c; however:
  Package libghc-ghc-prim-dev-0.2.0.0-bd29c is not installed.
  Package ghc which provides libghc-ghc-prim-dev-0.2.0.0-bd29c is not configured yet.
dpkg: error processing libghc-cereal-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libghc-bytestring-show-prof:
 libghc-bytestring-show-prof depends on libghc-bytestring-show-dev (= 0.3.5.1-1); however:
  Package libghc-bytestring-show-dev is not configured yet.
dpkg: error processing libghc-bytestring-show-prof (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libghc-polyparse-prof:
 libghc-polyparse-prof depends on libghc-polyparse-dev (= 1.7-1); however:
  Package libghc-polyparse-dev is not configured yet.
dpkg: error processing libghc-polyparse-prof (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libghc-dlist-dev:
 libghc-dlist-dev depends on libghc-base-dev-4.5.0.0-e98ea; however:
  Package libghc-base-dev-4.5.0.0-e98ea is not installed.
  Package ghc which provides libghc-base-dev-4.5.0.0-e98ea is not configured yet.
dpkg: error processing libghc-dlist-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ghc-prof:
 ghc-prof depends on ghc (= 7.4.1-1ubuntu2); however:
  Package ghc is not configured yet.
dpkg: error processing ghc-prof (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libghc-dlist-prof:
 libghc-dlist-prof depends on libghc-dlist-dev (= 0.5-3); however:
  Package libghc-dlist-dev is not configured yet.
 libghc-dlist-prof depends on libghc-base-prof-4.5.0.0-e98ea; however:
  Package libghc-base-prof-4.5.0.0-e98ea is not installed.
  Package ghc-prof which provides libghc-base-prof-4.5.0.0-e98ea is not configured yet.
dpkg: error processing libghc-dlist-prof (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libghc-cereal-prof:
 libghc-cereal-prof depends on libghc-cereal-dev (= 0.3.5.1-1); however:
  Package libghc-cereal-dev is not configured yet.
 libghc-cereal-prof depends on libghc-array-prof-0.4.0.0-3cf1b; however:
  Package libghc-array-prof-0.4.0.0-3cf1b is not installed.
  Package ghc-prof which provides libghc-array-prof-0.4.0.0-3cf1b is not configured yet.
 libghc-cereal-prof depends on libghc-base-prof-4.5.0.0-e98ea; however:
  Package libghc-base-prof-4.5.0.0-e98ea is not installed.
  Package ghc-prof which provides libghc-base-prof-4.5.0.0-e98ea is not configured yet.
 libghc-cereal-prof depends on libghc-bytestring-prof-0.9.2.1-e17f0; however:
  Package libghc-bytestring-prof-0.9.2.1-e17f0 is not installed.
  Package ghc-prof which provides libghc-bytestring-prof-0.9.2.1-e17f0 is not configured yet.
 libghc-cereal-prof depends on libghc-containers-prof-0.4.2.1-7c545; however:
  Package libghc-containers-prof-0.4.2.1-7c545 is not installed.
  Package ghc-prof which provides libghc-containers-prof-0.4.2.1-7c545 is not configured yet.
 libghc-cereal-prof depends on libghc-ghc-prim-prof-0.2.0.0-bd29c; however:
  Package libghc-ghc-prim-prof-0.2.0.0-bd29c is not installed.
  Package ghc-prof which provides libghc-ghc-prim-prof-0.2.0.0-bd29c is not configured yet.
dpkg: error processing libghc-cereal-prof (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libghc-bytestring-nums-prof:
 libghc-bytestring-nums-prof depends on libghc-bytestring-nums-dev (= 0.3.5-2); however:
  Package libghc-bytestring-nums-dev is not configured yet.
 libghc-bytestring-nums-prof depends on libghc-base-prof-4.5.0.0-e98ea; however:
  Package libghc-base-prof-4.5.0.0-e98ea is not installed.
  Package ghc-prof which provides libghc-base-prof-4.5.0.0-e98ea is not configured yet.
 libghc-bytestring-nums-prof depends on libghc-bytestring-prof-0.9.2.1-e17f0; however:
  Package libghc-bytestring-prof-0.9.2.1-e17f0 is not installed.
  Package ghc-prof which provides libghc-bytestring-prof-0.9.2.1-e17f0 is not configured yet.
 libghc-bytestring-nums-prof depends on libghc-containers-prof-0.4.2.1-7c545; however:
  Package libghc-containers-prof-0.4.2.1-7c545 is not installed.
  Package ghc-prof which provides libghc-containers-prof-0.4.2.1-7c545 is not configured yet.
dpkg: error processing libghc-bytestring-nums-prof (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libghc-text-prof:
 libghc-text-prof depends on libghc-text-dev (= 0.11.1.13-1build1); however:
  Package libghc-text-dev is not configured yet.
 libghc-text-prof depends on libghc-array-prof-0.4.0.0-3cf1b; however:
  Package libghc-array-prof-0.4.0.0-3cf1b is not installed.
  Package ghc-prof which provides libghc-array-prof-0.4.0.0-3cf1b is not configured yet.
 libghc-text-prof depends on libghc-base-prof-4.5.0.0-e98ea; however:
  Package libghc-base-prof-4.5.0.0-e98ea is not installed.
  Package ghc-prof which provides libghc-base-prof-4.5.0.0-e98ea is not configured yet.
 libghc-text-prof depends on libghc-bytestring-prof-0.9.2.1-e17f0; however:
  Package libghc-bytestring-prof-0.9.2.1-e17f0 is not installed.
  Package ghc-prof which provides libghc-bytestring-prof-0.9.2.1-e17f0 is not configured yet.
 libghc-text-prof depends on libghc-deepseq-prof-1.3.0.0-6c19e; however:
  Package libghc-deepseq-prof-1.3.0.0-6c19e is not installed.
  Package ghc-prof which provides libghc-deepseq-prof-1.3.0.0-6c19e is not configured yet.
 libghc-text-prof depends on libghc-ghc-prim-prof-0.2.0.0-bd29c; however:
  Package libghc-ghc-prim-prof-0.2.0.0-bd29c is not installed.
  Package ghc-prof which provides libghc-ghc-prim-prof-0.2.0.0-bd29c is not configured yet.
 libghc-text-prof depends on libghc-integer-gmp-prof-0.4.0.0-ec87c; however:
  Package libghc-integer-gmp-prof-0.4.0.0-ec87c is not installed.
  Package ghc-prof which provides libghc-integer-gmp-prof-0.4.0.0-ec87c is not configured yet.
dpkg: error processing libghc-text-prof (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ghc
 libghc-hunit-dev
 libghc-hunit-prof
 libghc-text-dev
 libghc-bytestring-show-dev
 libghc-bytestring-nums-dev
 libghc-polyparse-dev
 libghc-cereal-dev
 libghc-bytestring-show-prof
 libghc-polyparse-prof
 libghc-dlist-dev
 ghc-prof
 libghc-dlist-prof
 libghc-cereal-prof
 libghc-bytestring-nums-prof
 libghc-text-prof


```

---

### Post by howefield on 2017-06-23
Moved to the "*General Help*" forum.

---

### Post by Bashing-om on 2017-06-23
kadalyst; Hello; Welcome to the forum .

Sad news perhaps, that :
> 
running ubuntu 12 and I was trying to install python 3.5 

release 12.04 is End_Of_Life . And has no community support .
IF you want to continue to use a ubuntu 12.04 base ;
Then you will have to arrange with :
  "Canonical offers paid extended security support for 12.04 through the Ubuntu Advantage program. For more 
                information, see [https://ubuntu.com/esm](https://ubuntu.com/esm) . ESM is not an Ubuntu community offering; please direct questions about 
                it to Canonical directly. "

[INDENT][INDENT]nothing else to be said
[/INDENT][/INDENT]

---

