---
title: "How do I install from git?"
date: 2013-10-03
forum: General Help
---

### Post by GRX13 on 2013-10-03
I want to install kid3-qt: [http://kid3.sourceforge.net/](http://kid3.sourceforge.net/)

> git clone git://git.code.sf.net/p/kid3/code kid3
mkdir build
cd build
cmake ../kid3
I've done that and the install file says:

> cmake . -DCMAKE_BUILD_TYPE=Release -DWITH_APPS=Qt
make
make install

Now when I get to make it says:

> [ 93%] Built target taglibmetadata
[ 93%] Built target oggflacmetadata
[ 93%] Built target kid3-gui
[ 93%] Built target desktop-file
[ 93%] Built target kid3-qt
[ 93%] Built target en-html-handbook
[ 93%] Generating kid3.1
Note: meta manvol : no refentry/refmeta/manvolnum                  
Note: meta manvol : see [http://docbook.sf.net/el/manvolnum](http://docbook.sf.net/el/manvolnum)         
Note: meta manvol : Setting man section to 3                       
Warn: AUTHOR sect.: no personblurb|contrib for Urs Fleisch         
Note: AUTHOR sect.: see see [http://docbook.sf.net/el/contrib](http://docbook.sf.net/el/contrib)       
Note: AUTHOR sect.: see see [http://docbook.sf.net/el/personblurb](http://docbook.sf.net/el/personblurb)   
Note: Writing .3
I/O error : Permission denied
I/O error : Permission denied
runtime error: file /usr/share/xml/docbook/stylesheet/nwalsh/html/chunker.xsl line 225 element document
xsltDocumentElem: unable to save to .3
no result for -
make[2]: *** [doc/en/kid3.1] Error 9
make[1]: *** [doc/en/CMakeFiles/en-man-handbook.dir/all] Error 2
make: *** [all] Error 2


The I/O errors do not appear with sudo but that's not an issue, everything else is. What does it want?

Reason for being marked solved: [https://sourceforge.net/p/kid3/bugs/75/](https://sourceforge.net/p/kid3/bugs/75/)

---

### Post by Kirboosy on 2013-10-03
I/O permission denied is for not running it as a priveledge user. What error does it give you when you do use ```
sudo make install
```


Also what version of Ubuntu are you running? They have prebuilt packages and PPAs on the website.

If you aren't using KDE and you don't have QT you may want to try running the following 

```
cmake . -DCMAKE_BUILD_TYPE=Release -DWITH_KDE=OFF
```

[The Kid3 Handbook - Compiling]("http://kid3.sourceforge.net/kid3_en.html#compilation")

Hope that helps!
~Caboose

---

### Post by GRX13 on 2013-10-03
The I/O is not a problem and sudo make install gives me the same  problem. I'm using 12.04 and I don't want to use ppas or anything  prebuilt as they are all out of date. The kid3 handbook that gives you  that command now tells me to use cmake . -DCMAKE_BUILD_TYPE=Release  -DWITH_APPS=Qt as -DWITH_KDE=OFF is deprecated. I know what i'm doing up  to when it tells me the problem with en-man-handbook. I do have QT.

---

### Post by Kirboosy on 2013-10-04
I successfully compiled it on my VM. (Lubuntu 13.04 32-Bit) I did the following:

```
sudo apt-get install build-essential kde-full kdelibs5-dev libphonon-dev libtag1-dev libid3-3.8.3-dev libchromaprint-dev vorbis-tools-dbg libvorbis-dev libflac++-dev
```

I then made sure to download and install the latest version of QT from the [homepage]("http://qt-project.org/downloads"). I selected to install all versions of QT but I don't think that is required.

After that it was as simple as changing into my directory and compiling. (No flags)
```
cmake .
make
sudo make install
```

Hope that helps!
~Caboose
P.S. I also installed kubuntu-desktop and kubuntu-restricted-extras but I don't think they are needed
P.S.S. I don't have kid3 listed in my applications menu for whatever reason so I have to run it from command line but it brings up the GUI.

---

