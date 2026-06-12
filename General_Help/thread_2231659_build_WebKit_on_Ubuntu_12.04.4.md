---
title: "build WebKit on Ubuntu 12.04.4"
date: 2014-06-27
forum: General Help
---

### Post by Deropty on 2014-06-27
i suppose there is someone have built it successfully ! can you help me ! 

as far as i know , the procedure is : install sedkit-env-qtwebkit for all the dependencies > install qt > set the environmental variables > build-webkit --qt > run-launcher --qt for test , i don't know whether the procedure is correct, because there is always errors make me upset !

i followed this guide : [http://trac.webkit.org/wiki/QtWebKitGardening](http://trac.webkit.org/wiki/QtWebKitGardening)

/***************************************************************************************************************************************************************

[LIST]
[*]Get Ubuntu 12.04 and install it  * sudo apt-get install python-software-properties
 * sudo add-apt-repository ppa:u-szeged/sedkit
 * sudo apt-get update
 * sudo apt-get install sedkit-env-qtwebkit
[/LIST]

[LIST]
[*]Install GStreamer 1.0 * sudo add-apt-repository ppa:gstreamer-developers/ppa
 * sudo apt-get update
 * sudo apt-get install gstreamer1.0 libgstreamer-plugins-base1.0-dev
[/LIST]

[LIST]
[*]Build the actual Qt 5 for the WebKit trunk with this builder script:  * git clone git://github.com/ossy-szeged/qt5-tools.git
 * ./build-qt5.sh
[*]Download testfonts, set environment variables
 * git clone git://gitorious.org/qtwebkit/testfonts.git
 * export WEBKIT_TESTFONTS=/home/webkit/testfonts
 * export TZ=America/Los_Angeles
 * export QTDIR=/usr/local/Trolltech/Qt5/Qt-5.2.0
 * export PATH=/usr/local/Trolltech/Qt5/Qt-5.2.0/bin:$PATH

    // >>>>>  i added this >>>>>
     * export QT_WEEKLY_REV=Qt-5.2.0
     * export WEEKLY_QT5_HASH="v5.2.0"
     * export QT5_MODULES="qtxmlpatterns qtdeclarative"
[/LIST]

[LIST]
[*]Download WebKit, configure git svn, build WebKit.  * git clone git://git.webkit.org/WebKit.git WebKit
 * cd WebKit
 * git svn init --prefix=origin/ -T trunk [http://svn.webkit.org/repository/webkit](http://svn.webkit.org/repository/webkit)
 * git config --replace svn-remote.svn.fetch trunk:refs/remotes/origin/master
 * git svn fetch

******************************************************************************************/

```

deropty@deropty-XPS2720:~/WebKit$ Tools/Scripts/build-webkit --qt --debug


======================================================================
Webkit is now built (00m:01s).
======================================================================
deropty@deropty-XPS2720:~/WebKit$
deropty@deropty-XPS2720:~/WebKit$ Tools/Scripts/run-launcher --qt --debug
Unsupported platform, can't determine built library locations.
Try 'build-webkit --help' for more information.


```

why does it take only 01s to build? where is the problem? please help!
[/LIST]

---

### Post by Deropty on 2014-06-27
there is some information about the method i have tried
1. install the sedkit-env-qtwebkit, for all the dependencies
2. install the GStreamer 1.0, which function i still don't know, in ubuntu 14.04, it is the dependency of sedkit-env-qtwebkit, but i did not install it successfully at last
3. install the qt
          ------a. ```
./qt-opensource-linux-x64-5.3.1.run
``` 
------------it is not a good attempt, i can not determine the install directory, thought i choose it /home/deropty/Qt-5.3.0
          ------b. build the source file: qt-everywhere-opensource-src-5.1.1.tar.gz
                                   ```
cd /home/deropty/qt-everywhere-opensource-src-5.1.1
./configure -prefix $PWD/qtbase -opensource -nomake tests
make -j 4
```
4.set the environmental virables
                ```
export QTDIR=/home/deropty/qt-everywhere-opensource-src-5.1.1
export PATH=$QTDIR/bin:$PATH
```
5. build-webkit --qt
           ------i failed here
                       ------------a. in the source file, there is qtwebkit, i entrance these directory, and build-webkit --qt , and a lot of error happened
            ------------b. [http://trac.webkit.org/wiki/QtWebKitContrib](http://trac.webkit.org/wiki/QtWebKitContrib) , i got the webkit and build it, like the a method, lots of error
                       ------------c. download the nightly builds here [http://www.webkit.org](http://www.webkit.org), and it told me
                                                          ```
======================================================================
Webkit is now built (00m:01s).
======================================================================
```
                       ------------d. the first floor is my lastest try

is there anybody can help me, i'm very grateful for that !

---

