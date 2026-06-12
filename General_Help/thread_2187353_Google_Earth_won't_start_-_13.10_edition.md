---
title: "Google Earth won't start - 13.10 edition"
date: 2013-11-11
forum: General Help
---

### Post by scottbomb on 2013-11-11
There are some old threads with this issue related to some much older versions of Ubuntu so, here we are again with Google Earth refusing to start. It's the usual splash screen and a very brief picture of planet Earth and then - poof! - it's gone.

It ran fine on this same installation yesterday. Also works on a Xubuntu 13.10 partition on the same machine. They are both using the Nvidia drivers.

I tried it in a terminal and got this, if it helps anyone see what's going on:

```
[1111/184114:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184114:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184115:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184115:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184115:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184115:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184115:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184115:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184115:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184115:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184115:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[1111/184115:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184115:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184115:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1111/184115:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.


Another crash happened while handling crash!

```

---

### Post by scottbomb on 2013-11-12
Oddly enough, and don't ask me me why (although I am VERY curious as to why) I have been able to fix this in a couple of instances by doing this: Install the x64 version. It crashes. Purge it. Install 386 version. It doesn't work (bad graphics). Purge again. Re-install x64 version. For some reason, it works again. At least for a couple of weeks or so it seems, and therein lies the problem.

---

### Post by scottbomb on 2013-11-15
I thought all was well as it was working until today. Now it's just doing the same as before. Interestingly, I've never had this problem under xfce or Windows.

---

### Post by scottbomb on 2013-11-18
Due to other issues, I had to reinstall Xubuntu. Now Google Earth won't even install, complaining about dependencies that cannot be met. What a piece of garbage. I'm amazed that a company as wealthy as Google puts out such buggy software.

---

### Post by Newbunto on 2013-12-03
Has there been any progress on the issue originally reported in this thread? Google Earth seems to die very quickly most of the time under Ubuntu 13.10. However some of the time it will start and when it does start it seems to be stable. (It was OK under Ubuntu 12.04 LTS.)

When started from the shell prompt I get:

[FONT=courier new][1203/214651:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[1203/214651:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for [www.google.com]("http://www.google.com") failed err=-8181
[1203/214651:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1203/214651:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for accounts.google.com failed err=-8181
[1203/214652:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for support.google.com failed err=-8181
[1203/214652:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1203/214652:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[1203/214652:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for ssl.gstatic.com failed err=-8181
[1203/214652:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.

Another crash happened while handling crash!
[/FONT]
where the OCSP error is actually repeated lots of times.

@scottbomb, the issue about dependencies requires you to pull apart the installation package, remove the dependencies line, and then recreate the package. I found instructions in here and they worked for me.

---

### Post by scottbomb on 2013-12-11
I switched over to Kubuntu and still can't get it to work. It won't even launch, just draws its intro screen then disappears without a trace. I gave up on it and am happily using their flash-based street view on maps.google.com. Taking apart a .deb is nothing I've ever tried to do before so it might make for an interesting learning experience.

---

### Post by echotech2 on 2013-12-12
Ubuntu 13.10...Google Earth v7.1.1.1888  Quite often when starting GE I get the splash screen then it disappears.  Starting GE again it works OK.  Not reproducible, it happens intermittently.

---

### Post by Newbunto on 2013-12-12
@scottbomb Taking apart a .deb is nothing I've ever tried to do before either. But it worked for me. I had to do that even to get Google Earth to install under Ubuntu 13.10. However getting it to install correctly is only half the battle. See next.

@echotech2 "Google Earth dies immediately and window disappears" is highly reproducible for me. It happens *most* of the time e.g. 10 times in a row. But if starting it is tried *enough* times, it seems to be possible to get it not to die.

---

### Post by Jim_Granite on 2013-12-28
All I can say is that Google Earth, which I had working on Ubuntu 13.10 a  month or three ago, now crashes as described in the OP.
It comes up, and then dies. 

> 
$ google-earth
[1228/133238:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[1228/133239:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1228/133239:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
... lots and lots of similar messages ... 
[1228/213240:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
Another crash happened while handling crash!
$ 


and ... 
> 
$ google-earth
[1228/133359:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[1228/133359:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
... lots of similar messages ... 
[1228/133400:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1228/133400:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
Segmentation fault (core dumped)
$ 
[ATTACH=CONFIG]248980[/ATTACH]

---

### Post by Jim_Granite on 2013-12-28
Googling, I find, apparently, the problem is that Canonical killed Google Earth, apparently on purpose.
That makes no sense, to me, but that's how I read this article:
- [Say Goodbye to Google Earth on Ubuntu 13.10]("http://news.softpedia.com/news/Say-Goodbye-to-Google-Earth-on-Ubuntu-13-10-396451.shtml")

Since it's an off-topic question, I posted a separate thread asking WHY Canonical would kill Google Earth on purpose over here:
- [Why would Canonical kill Google Earth on purpose?]("http://ubuntuforums.org/showthread.php?t=2196304")

---

### Post by Jim_Granite on 2013-12-28
I've been trying web-solutions for an hour (including trying the 32-bit Google-Earth Deb file); and all are failing miserably. 
There is not a single howto on the net that actually works. You have to  know something that is not in the instructions to make it work.

This sequence of cryptic steps came the closest to working, but still failed miserably:
[http://linuxg.net/quicktip-how-to-pr...cy-salamander/]("http://linuxg.net/quicktip-how-to-properly-install-google-earth-6-on-ubuntu-13-10-saucy-salamander/")

Here's a history log of the commands that I ran, but, there were far too many dependencies for me to resolve:
$ wget [https://dl.dropboxusercontent.com/u/..._1.1.0_all.deb]("https://dl.dropboxusercontent.com/u/209784349/mix/googleearth-package_1.1.0_all.deb")
$ sudo dpkg -i googleearth-package_1.1.0_all.deb 
$ sudo apt-get install -f
$ make-googleearth-package
$ sudo dpkg -i googleearth_6.0.3.2197+1.1.0-1_amd64.deb 
$ sudo apt-get install libfreeimage3 lsb-core libcurl3 libsm6  libfontconfig1 libxt6 libxrender1 libxext6 libgl1-mesa-glx  libgl1-mesa-dri
(this fails, due to numerous dependencies)
$ sudo apt-get install -f
$ which google-earth
=> ./google-earth
$ google-earth
=> ./googleearth-bin: error while loading shared libraries:  libGLU.so.1: cannot open shared object file: No such file or directory

---

### Post by alexsmith on 2014-01-31
I got Google Earth working by strictly following what's suggested here:

[http://askubuntu.com/a/366439/109449](http://askubuntu.com/a/366439/109449)

Here's what's suggested, for commodity:

---8<---
This is only a workaround until Google Earth is repackaged.

Google Earth Build Package

    Download Google Earth x64 .DEB

    Open Terminal, Copy & Paste Following Command And Press Enter

    sudo apt-get install libc6:i386 lsb-core

    Open Downloads Folder
    Right Click On Google Earth .deb package & Select Extract Here
    Open the folder where files are extracted.
    Open the DEBIAN Folder
    Open the control file with gedit
    Remove this whole Line: Depends: lsb-core (>= 3.2), ia32-libs
    Now Click Save, & Exit Control File

    Now Delete The Original Google Earth .DEB Package You Downloaded

    Create A Folder called getfix, Now Move The Extracted Google Earth Folder Into The getfix Folder

Now we Are Going To Rebuild The Google Earth .deb Package:

    Open Terminal, copy/paste the following command then press Enter:

    dpkg -b ~/Downloads/getfix/google-earth-stable_current_amd64

    Copy/paste the following command (this will install the repackaged .deb)

    sudo dpkg -i ~/Downloads/getfix/google-earth-stable_current_amd64.deb
---8<---

**Important note 1:** When I first run Google Earth, it crashed, generating a bug report. Then I fired it up again and it worked just fine.
**Important note 2:** After closing and reopening Google Earth, it crashes sometimes. Randomly. Sometimes it works, sometimes it doesn't. I keep trying until a get a "stable session".

---

### Post by geoaraujo on 2014-01-31
I've uninstalled the 64-bit version and downloaded and installed the 32-bit one. It runs flawlessly.

---

### Post by jlguru on 2014-02-03
I've noticed the same behavior and it appears to me that Google Earth fails while refreshing it's cache using my home network connection to my ISP. I've blamed the problem on a flakey internet connection. If I restart Google Earth several times, the cache finally gets refreshed completely and Google Earth runs fine. I suspect the people reporting that Google Earth flawlessly have solid internet connections and those who have some problems (like me) have less solid/reliable) connections.

Try starting Google Earth several times and watch for the refreshing link symbols in the application. When Google Earth finally gets everything refreshed you should be OK.

Hope it helps

Live long, and prosper

---

