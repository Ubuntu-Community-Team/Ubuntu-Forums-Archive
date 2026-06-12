---
title: "GnuTLS linked programs don't work with HTTPS: git, apt"
date: 2020-05-08
forum: General Help
---

### Post by boekhold2 on 2020-05-08
Focal, running from Live CD:

**I have a log fragment here, but no matter what I do I can't seem to be able to post that here, whenever I include it I get an error from the Forum either about the post not being long enough, or about not having permissions to post.**

(git command that results in "gnutls_handshake() failed: Error in the pull function")

Another case that doesn't work: add "deb [https://download.mono-project.com/repo/ubuntu](https://download.mono-project.com/repo/ubuntu) stable-bionic main" as a repository and run "sudo apt update":


```

$ sudo apt update
Hit:1 https://download.docker.com/linux/ubuntu bionic InRelease
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                                                                           
Hit:3 http://ae.archive.ubuntu.com/ubuntu focal InRelease                                                                              
Get:4 http://ae.archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]                                                             
Get:5 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]                                                             
Hit:6 http://dl.google.com/linux/chrome/deb stable Release                                                                             
Get:8 http://ae.archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]                                                          
Ign:9 https://download.mono-project.com/repo/ubuntu stable-bionic InRelease                                                            
Err:10 https://download.mono-project.com/repo/ubuntu stable-bionic Release
  Could not wait for server fd - select (11: Resource temporarily unavailable) [IP: 152.199.19.161 443]

```


This is not a network issue: running the same 2 scenarios from a Linux Mint 19.2 machine on the same network works fine. Also, "curl -o output https://github/prominic/groovy-language-server.git" works fine. Chrome & Firefox have no issues with HTTPS either.


I suspect this is a generic GnuTLS issue, but have no idea how to go around fixing it. Googling for this error in combination with GIT comes up with lots of pages that recommend just recompiling GIT with OpenSSL, but that wouldn't help me with the APT issue.

[EDIT] More evidence that this is a GnuTLS issue:

```

$ gnutls-cli github.com
Processed 128 CA certificate(s).
Resolving 'github.com:443'...
Connecting to '140.82.118.4:443'...
*** Fatal error: The operation timed out


```

```

$ apt show libgnutls30
Package: libgnutls30
Version: 3.6.13-2ubuntu1

$ apt show gnutls-bin
Package: gnutls-bin
Version: 3.6.13-2ubuntu1


```

---

### Post by dino99 on 2020-05-08
As you says: "running from Live CD"  ;)

if you want custom/external source/app, then first do a real install ):P

---

### Post by boekhold2 on 2020-05-08
I've done a full install as well. I mentioned the Live CD because I wanted to make it clear that it's something that's happening out of the box for me, without me messing around with packages.

---

### Post by boekhold2 on 2020-05-08
I've posted about this on the GnuTLS issue tracker: [https://gitlab.com/gnutls/gnutls/-/issues/984](https://gitlab.com/gnutls/gnutls/-/issues/984), see the 3rd comment.

[EDIT] Opened a new issue with the GNuTLS project for this: [https://gitlab.com/gnutls/gnutls/-/issues/990](https://gitlab.com/gnutls/gnutls/-/issues/990)

---

### Post by boekhold2 on 2020-05-09
This seems to be something specific in my country/region. I fired up an Ubuntu Server 20.04 instance in AWS eur-west-1, and I don't have these issues. Then I set up a VPN connection from my workstation (from where I had the issue), and things are working now as well.

I suspect the Deep Packet Inspection/traffic shaping that the local telco operators are doing somehow changes the TLS handshake, and that GnuTLS is (excessively?) sensitive to this. Just to repeat: Chrome, Firefox and anything OpenSSL based (curl, wget,...) have no issue with this. Only GnuTLS based programs seem to be affected.

Will mark this thread as [SOLVED]

---

