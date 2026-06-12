---
title: "Installing LibSSL-Dev.. Package Manager Error!"
date: 2007-02-19
forum: General Help
---

### Post by Nectron on 2007-02-19
I've been trying to install the development libraries of libssl, they're shown in the synaptic package manager. But I get this error which is driving me crazy.. 

Why wouldn't libssl-dev install since libssl0.9.8a-7ubuntu0.3 is already installed and working with other programs?

```

libssl-dev:
  Depends: libssl0.9.8 (=0.9.8a-7build1) but 0.9.8a-7ubuntu0.3 is to be installed

```

Any reply is highly appreciated guys,

---

### Post by llamakc on 2007-02-19
Are you on Edgy? Have you done an update&upgrade recently? My `apt-cache show libssl-dev` shows:

```
 
apt-cache show libssl-dev
Package: libssl-dev
Priority: optional
Section: libdevel
Installed-Size: 5640
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Original-Maintainer: Debian OpenSSL Team <pkg-openssl-devel@lists.alioth.debian.org>
Architecture: i386
Source: openssl
Version: 0.9.8b-2ubuntu2
Depends: libssl0.9.8 (= 0.9.8b-2ubuntu2), zlib1g-dev

```


This is on Edgy with the standard repositories.

---

### Post by Nectron on 2007-02-19
I'm using Ubuntu Dapper-Drake 6.06LTS

Any instructions ?

---

### Post by llamakc on 2007-02-19
Make sure you have done an `sudo apt-get update && apt-get upgrade` (or whatever the equivalent in Synaptic is) for starters. Try again. If that doesn't work, check launchpad. Here's a similar bug:

[https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/78138](https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/78138)

So, are your /etc/apt/sources.list ONLY Dapper-related, or are you running mixed? Post your /etc/apt/sources.list if you're uncertain.

---

### Post by Nectron on 2007-02-20
I've updated the repositories through Synamptic Package Manager as you instructed..

I've checked the packages I needed and everything worked perfectly..

Thanks for your time and effort mate, I appreciate your help.

[RESOLVED]

---

