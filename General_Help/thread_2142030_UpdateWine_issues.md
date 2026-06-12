---
title: "Update/Wine issues"
date: 2013-05-04
forum: General Help
---

### Post by HughPR on 2013-05-04
Hi,

I'm trying to install Wine 1.4 but for some reason I get the following error when I try (I have gone to add software etc following the info on this link [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu))

Requires installation of untrusted packages 

Details: binfmt-support cabextract fonts-droid fonts-horai-umefont fonts-unfonts-core icoutils libcapi20-3 libcdt4 libencode-locale-perl libfile-listing-perl libfont-afm-perl libgettextpo0 libgif4 libgraph4 libgvc5 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libilmbase6 libio-socket-inet6-perl libio-socket-ssl-perl liblqr-1-0 liblwp-mediatypes-perl liblwp-protocol-https-perl libmailtools-perl libmpg123-0 libnet-http-perl libnet-ssleay-perl libnetpbm10 libodbc1 libopenal-data libopenal1 libopenexr6 libpathplan4 libsocket6-perl libtimedate-perl libunistring0 liburi-perl libwww-perl libwww-robotrules-perl netpbm odbcinst odbcinst1debian2 ttf-droid ttf-mscorefonts-installer ttf-umefont ttf-unfonts-core unixodbc unrar wine-gecko1.4

I then click repair and it pops up again a few seconds later.

I've looked around a bit on the net and people have suggested using terminal commands like:

sudo apt-get update

but these haven't worked and I get the following error.

W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

What do I do???

Hugh :)

---

### Post by grahammechanical on 2013-05-04
Have you tried installing through the Ubuntu Software Centre instead of adding a PPA?

---

### Post by HughPR on 2013-05-06
> **grahammechanical said:**
> Have you tried installing through the Ubuntu Software Centre instead of adding a PPA?

They say to do the PPA AND go through software centre...

---

