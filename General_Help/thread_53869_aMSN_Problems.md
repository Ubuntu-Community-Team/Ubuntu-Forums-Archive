---
title: "aMSN Problems"
date: 2005-08-02
forum: General Help
---

### Post by AliazaR on 2005-08-02
Normally aMSN presents any problems under Ubuntu using tk8.4.
 I found the solution....  

 First:  Do   #sudo apt-get remove tk8.4 tcl8.4 ( and dev packages)

  Download tk8.5.2a  and tcl8.5.2a or newer

  Follow this steps


   I love aMSN and its simplicity but I hate tcl/tk apps, generally because the versions of tcl and tk that are in apt don't build support for nice anti-aliased fonts. Hence, they look ugly and clunky.

 First: #tar xvzf tcl-<date> && tar xvzf tk-<date>

  then  $ cd tcl/unix 

            $ ./configure  --prefix=/usr

            $ make  

            #make install

then  $ cd tk/unix

           $ ./configure --prefix=/usr --enable-xft

           $ make 

          # make install 


          Make a few symbolic links: (become root, using SUDO )

         cd /usr/bin
ln -s wish8.5 wish
ln -s tclsh8.5 tclsh
cd /usr/lib
ln -s tcl8.5 tcl
ln -s tk8.5 tk
ln -s libtk8.5.so libtk.so
ln -s libtcl8.5.so libtcl.so
ln -s libtclstub8.5.a libtclstub.a
ln -s libtkstub8.5.a libtkstub.a
ldconfig

          That's it

    Your tk will run good.

   Download amsn_cvs and compile it... don't remember to install imlib1-dev

   Greets... any question

 Please send me a mail

---

### Post by ubuntu_demon on 2005-08-03
what kind of problems did you have with amsn previously ?
I believe there's a newer amsn in backports did you try that ? (that provides an easy upgrade path)

---

### Post by AliazaR on 2005-08-03
aMSN gets freezed.... It's just for an tk8.4 bug under Linux 2.6 

  I don't use amsn debian package not even Ubuntu, I just compile aMSN_cvs

---

