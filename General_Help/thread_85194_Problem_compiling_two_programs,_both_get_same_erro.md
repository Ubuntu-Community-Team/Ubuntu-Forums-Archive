---
title: "Problem compiling two programs, both get same error"
date: 2005-11-02
forum: General Help
---

### Post by kittcankitt on 2005-11-02
I was trying to install kiso-0.8.2 and cdbakeoven-2.0beta however after installing what seemed like tons of dependancies I get this error about cdio/mmc.h

...Making all in src
make[2]: Entering directory `/home/kck/misc/kiso-0.8.2/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT kiso.o -MD -MP -MF ".deps/kiso.Tpo" -c -o kiso.o kiso.cpp; \
then mv -f ".deps/kiso.Tpo" ".deps/kiso.Po"; else rm -f ".deps/kiso.Tpo"; exit 1; fi
kiso.cpp:15:22: error: cdio/mmc.h: No such file or directory
/usr/share/qt3/include/qtooltip.h:86: warning: &#8216;class QToolTip&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/kfiletreeview.h:41: warning: &#8216;class KFileTreeViewToolTip&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/keditlistbox.h:59: warning: &#8216;class KEditListBox::CustomEditor&#8217; has virtual functions but non-virtual destructor
kiso.cpp: In member function &#8216;virtual void Mainform::showdrive()&#8217;:
kiso.cpp:3602: error: &#8216;scsi_mmc_cdb_t&#8217; was not declared in this scope
kiso.cpp:3602: error: expected `;' before &#8216;cdb&#8217;
kiso.cpp:3604: error: &#8216;cdb&#8217; was not declared in this scope
kiso.cpp:3604: error: &#8216;CDIO_MMC_GPCMD_GET_CONFIGURATION&#8217; was not declared in this scope
kiso.cpp:3604: error: &#8216;CDIO_MMC_SET_COMMAND&#8217; was not declared in this scope
kiso.cpp:3605: error: &#8216;CDIO_MMC_SET_READ_LENGTH8&#8217; was not declared in this scopekiso.cpp:3606: error: &#8216;CDIO_MMC_GET_CONF_ALL_FEATURES&#8217; was not declared in this scope
kiso.cpp:3609: error: &#8216;SCSI_MMC_DATA_READ&#8217; was not declared in this scope
kiso.cpp:3609: error: &#8216;scsi_mmc_run_cmd&#8217; was not declared in this scope
kiso.cpp:3615: error: &#8216;CDIO_MMC_GET_LEN32&#8217; was not declared in this scope
kiso.cpp:3621: error: &#8216;CDIO_MMC_GET_LEN16&#8217; was not declared in this scope
kiso.cpp:3625: error: &#8216;CDIO_MMC_FEATURE_CORE&#8217; was not declared in this scope
make[2]: *** [kiso.o] Error 1
make[2]: Leaving directory `/home/kck/misc/kiso-0.8.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kck/misc/kiso-0.8.2'
make: *** [all] Error 2

Now for as much googling I've done, I still have no idea what to do from here.  I have libcdio and the dev installed but that didn't seem to change anything.  In /usr/include/cdio I have a file called scsi_mmc.h but ??? I'm really lost.  Any help would be greatly appreciated.  By the way running Breezy/Gnome with most, if not all, kde installed.  And I have no problems with any other software regarding burning and/or reading from my dvd drive.  (except xcdroast says that I'd get better performance from using scsi emu but I have no idea about that either?)

Thanks again! kck

---

### Post by kittcankitt on 2005-11-02
I am now actually getting this error when trying to compile cdbakeoven

checking for Qt... configure: error: Qt (>= Qt 3.1 (20021021)) (headers and libraries) not found. Please check your installation!

But the thing is that when kiso checks for Qt it goes through without a problem?

I guess this is all just to make my life a little less complicated?? lol

The whole thing that started this little quest was the ability (gui) to extract an iso whether it be from a dvd or file, edit it and be able to burn the newer iso.  Yes, I read all the posts about creating a "custom" install disk but I wasn't sure I got my head wrapped around it so I ended up searching and came up with some alternatives.  If some could explain the steps for what I'm trying to do from a command line, I'd be more that happy to learn!

Thanks!

---

### Post by beefsprocket on 2005-11-02
Do you have the libqt-mt-dev package installed? What about libcdio-dev? Libcdio-dev should give you the mmc.h header that you need. I think that the qt-dev package should get rid of that configure error. Also, depending on the pakcage that you are trying to compile, it is sometimes necessary (I'm only familiar with KDE since I'm solely a Kubuntu user) to specify the path to your headers i.e. ./configure --prefix=`kde-config --prefix`

Kiso being a kde app, you may want to give this a try. Just a thought.

[B]EDIT!!!
[/B]So kiso looks interesting enough that I decided to give it a try. Turns out I had the same problem (even with libcdio and libcdio-dev installed). The mmc.h header is not seen for some reason. I checked the libcdio page here [http://ftp.gnu.org/gnu/libcdio/]("http://ftp.gnu.org/gnu/libcdio/") and downloaded, compiled, and checkinstalled the newest 0.76 version as opposed to the 0.72 that ubuntu installs. 

A ./configure, make, and checkinstall make install later, I am greeted with kiso. Let me know how it goes.

---

### Post by kittcankitt on 2005-11-02
Why yes, yes indeed it worked for the kiso!  Thanks, I think that was the only thing I hadn't tried.  

So, any clue about the error about:

checking for Qt... configure: error: Qt (>= Qt 3.1 (20021021)) (headers and libraries) not found. Please check your installation!

The thing that really gets me is that I know I have all the qt packages installed and up to date...As a matter of fact, the kiso depended on it as well and it found/checked it without any problems.  Why won't this one?

Thanks again for your help beefsprocket!  cheers kck

---

### Post by beefsprocket on 2005-11-02
When specifically do you get that error? Is it just with a single package or every time you attempt to compile an app that uses qt? Is is the cdbakeoven that gives you this error?

---

### Post by kittcankitt on 2005-11-03
I get the error only while I'm running ./configure for cdbakeoven.  It's the same Qt dependencies that were needed while compiling kiso and worked fine?  Thus the head-scratching on my part...

In the meantime I've tried different versions of cdbakeoven but keep getting the same error.  Even with an old .deb package of it I ran across. hmmm

Thanks.  KCK

---

### Post by claydoh on 2005-11-03
You just need to tell configure where your QT headers are (/usr/lib/qt3)
so try this:

> ./configure --prefix=`kde-config --prefix` --with-qt-includes=/usr/lib/qt3

running "./configure --help" will show you some info on what options are available

btw cdbakeoven hasn't been updated in almost 3 years :), running make produces even more QT errors :(

---

