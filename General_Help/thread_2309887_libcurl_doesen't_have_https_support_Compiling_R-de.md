---
title: "libcurl doesen't have https support? Compiling R-devel."
date: 2016-01-14
forum: General Help
---

### Post by ben_ward4 on 2016-01-14
Hi, 

I'm trying to compile R-devel on 14.04 LTS:

```
export RSOURCES=~/svn
export RDEVEL=~/R-devel

mkdir -p $RSOURCES
cd $RSOURCES
svn co https://svn.r-project.org/R/trunk R-devel
R-devel/tools/rsync-recommended

mkdir -p $RDEVEL
cd $RDEVEL
$RSOURCES/R-devel/configure && make -j  However, it stops at the configure stage:
  checking libcurl version ... 7.45.0
checking curl/curl.h usability... yes
checking curl/curl.h presence... yes
checking for curl/curl.h... yes
checking if libcurl is version 7 and >= 7.28.0... yes
checking if libcurl supports https... no
configure: error: libcurl >= 7.28.0 library and headers are required with support for https
```

Unfortunately the config fails due to libcurl. I had a look at the versions of libcurl I have installed:

```
bward@n78620:~/R-devel$ dpkg -l '*libcurl*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                   Version                  Architecture             Description
+++-======================================-========================-========================-=================================================================================
un  libcurl-dev                            <none>                   <none>                   (no description available)
un  libcurl-ssl-dev                        <none>                   <none>                   (no description available)
ii  libcurl3:amd64                         7.35.0-1ubuntu2.5        amd64                    easy-to-use client-side URL transfer library (OpenSSL flavour)
un  libcurl3-dbg                           <none>                   <none>                   (no description available)
un  libcurl3-dev                           <none>                   <none>                   (no description available)
ii  libcurl3-gnutls:amd64                  7.35.0-1ubuntu2.5        amd64                    easy-to-use client-side URL transfer library (GnuTLS flavour)
un  libcurl3-openssl-dev                   <none>                   <none>                   (no description available)
un  libcurl4-dev                           <none>                   <none>                   (no description available)
un  libcurl4-doc                           <none>                   <none>                   (no description available)
un  libcurl4-gnutls-dev                    <none>                   <none>                   (no description available)
un  libcurl4-nss-dev                       <none>                   <none>                   (no description available)
ii  libcurl4-openssl-dev:amd64             7.35.0-1ubuntu2.5        amd64                    development files and documentation for libcurl (OpenSSL flavour)
```

Why is there no https support, what do I need to do to resolve this?

Thanks,
Ben.

---

### Post by steeldriver on 2016-01-14
You probably need to install one of the 'flavours' of the libcurl4 development package

```

libcurl4-gnutls-dev - development files and documentation for libcurl (GnuTLS flavour)
libcurl4-nss-dev - development files and documentation for libcurl (NSS flavour)
libcurl4-openssl-dev - development files and documentation for libcurl (OpenSSL flavour)

```

Not sure which one is required/preferred - it seems to work with libcurl4-openssl-dev, and this page seems to imply it as well 
[https://cran.r-project.org/web/packages/curl/index.html](https://cran.r-project.org/web/packages/curl/index.html)

---

