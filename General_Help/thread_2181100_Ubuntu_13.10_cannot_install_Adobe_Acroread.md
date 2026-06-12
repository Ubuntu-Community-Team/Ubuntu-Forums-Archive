---
title: "Ubuntu 13.10 cannot install Adobe Acroread"
date: 2013-10-16
forum: General Help
---

### Post by wmstrome on 2013-10-16
I have tried several different ways to install Acroread on Ubuntu 13.10 (Saucy Salamander) without success.I tried method given at
[http://www.liberiangeek.net/2013/03/how-to-install-adobe-reader-in-ubuntu-13-04-raring-ringtail/](http://www.liberiangeek.net/2013/03/how-to-install-adobe-reader-in-ubuntu-13-04-raring-ringtail/)

which gave errors related to libxml2.so.2 (I could not install that manually either).

I also tried donloading it and installing it with the Software Centre, and got the results:
The package is of bad quality
The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organization who provided this package file and include the details beneath.
Details:
Lintian check results for /tmp/AdbeRdr9.5.5-1_i386linux_enu.deb:
E: adobereader-enu: control-file-has-bad-permissions postinst 0555 != 0755
E: adobereader-enu: control-file-has-bad-owner postinst acrorel/named != root/root
E: adobereader-enu: control-file-has-bad-permissions prerm 0555 != 0755
E: adobereader-enu: control-file-has-bad-owner prerm acrorel/named != root/root
E: adobereader-enu: maintainer-address-missing Adobe Systems, Incorporated
E: adobereader-enu: wrong-file-owner-uid-or-gid etc/ 10490/25
E: adobereader-enu: wrong-file-owner-uid-or-gid etc/bash_completion.d/ 10490/25
E: adobereader-enu: wrong-file-owner-uid-or-gid etc/bash_completion.d/acroread.sh 10490/25
E: adobereader-enu: wrong-file-owner-uid-or-gid opt/ 10490/25
E: adobereader-enu: wrong-file-owner-uid-or-gid opt/Adobe/ 10490/25
E: adobereader-enu: wrong-file-owner-uid-or-gid opt/Adobe/Reader9/ 10490/25

    ......etc.

Has anyone found an easy way to install Acroread that works? None of the methods I found work.

---

### Post by sudodus on 2013-10-16
13.10 is not yet released. Often proprietary software or special versions will be available some time after the release.

Maybe you can get along using ***evince*** until there will be a version of acroread for 13.10.

---

### Post by benzarti on 2013-10-16
Try :
```
 sudo dpkg -i Adobe*
 sudo apt-get install -f
```

---

### Post by fantab on 2013-10-17
Instead of Acroread may I suggest [PDFXChange]("http://www.tracker-software.com/product/pdf-xchange-viewer") via Wine? Or if you want OpenSource then **Okular** (from the Ubuntu repo) is your best bet. The only reason I would use Acroread is because of 'Text Highlighting' and 'Commenting'... and these don't work most of the times because of document permissions on the given .pdf. I find both PDFXchange and Okular to do the job for me.

My two cents...

---

### Post by Nick Payne on 2013-10-18
Adobe reader is the only PDF reader that can open PDF portfolios. None of the 3rd party readers work with portfolios.

And to answer the original question, Adobe Reader downloaded from [ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.5.5/enu/AdbeRdr9.5.5-1_i386linux_enu.deb]("ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.5.5/enu/AdbeRdr9.5.5-1_i386linux_enu.deb") installs successfully with gdebi and runs correctly on 13.10.

---

### Post by TheGrep on 2013-10-18
I had to install the 32 bit version of libxml2 to get it to work on my 64 bit installation. Simply do this:

sudo apt-get install libxml2:i386

---

### Post by bagl0312 on 2013-10-21
I had no problem installing acroread from the Adobe download page, in Ubuntu 13.10 64-bits.
I just used the package:

AdbeRdr9.5.5-1_i486linux_enu.bin

I get some warning when I launch acroread, but then it seems to work correctly:

```

$ acroread
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"


(acroread:16150): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
....
Gtk-Message: Failed to load module "canberra-gtk-module"



```

---

### Post by henshu70 on 2013-10-23
I managed to install latest Adobe Reader both on Ubuntu 13.10 64-bit and after many hours of trial and error also on Kubuntu 13.10 64-bit

**For Ubuntu 13.10 Saucy Salamander 64-bit**

This was easy, the following method was working straight out of the box:

1. Download the DEB for Adobe Reader from Adobe website

[http://get.adobe.com/uk/reader/]("http://get.adobe.com/uk/reader/")

2. Install with following commands

sudo dpkg -i --force-architecture AdbeRdr9.5.5-1_i386linux_enu.deb && sudo apt-get -f install

To explain this, the switch **-i --force-architecture** installs 32-bit architecture and **-f install** installs missing libraries

**For Kubuntu 13.10 Saucy Salamander 64-bit**

3. Repeat the same steps as for Ubuntu plus run following command (installs missing libraries)

sudo apt-get install libxml2:i386 lib32stdc++6

4. Run Adobe Reader from you terminal first, just type

acroread

5. I got some errors there but after that Adobe Reader is running just fine.

Hope this helps. You may encounter another missing libraries that need to be installed but this method has been working for me.

---

### Post by kufischer on 2013-10-29
It would be great if this last comment would work. Unfortunately, although I am running kubuntu 13.10, I only read the second part after trying the first. When I do the commands for Ubuntu 13.10, I get the error message:

dpkg: Abhängigkeitsprobleme verhindern Konfiguration von adobereader-enu:
 adobereader-enu hängt ab von libgtk2.0-0 (>= 2.4).

Sorry, for the German in there, I have a German install.

When I tried the command in the second part, I get:

Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 adobereader-enu:i386 : Hängt ab von: libgtk2.0-0:i386 (>= 2.4) soll aber nicht installiert werden
 lib32stdc++6 : Hängt ab von: lib32gcc1 (>= 1:4.1.1) soll aber nicht installiert werden
                Hängt ab von: libc6-i386 (>= 2.17) soll aber nicht installiert werden

I would be still interested to use acroread although it did misbehave quite a bit under Kubuntu 13.04.

Thanks for your attention.

Klaus

---

### Post by henshu70 on 2013-10-29
Klaus,

After installation of Adobe Reader try running it from your terminal with the command

**acroread**

That should give you error messages showing you which dependencies are missing. That is the way I solved my installation.

---

### Post by jebradley on 2013-11-03
Thank you.
I had been unsuccessful with my attempts to install, but I was using the .bin file that Adobe's site gave me. 
Others had suggested using okular or evince, but for large pdf files, the page flow is much smoother with acroread. It is now working, and I am grateful.

---

### Post by ksraju007 on 2013-11-05
Here is what I did on my 64 Bit Ubuntu 13.10 install. I am able to run Adobe Reader now. Usually, the missing dependancies are i386 compatibility libraries.

[http://undan.co.in/2013/11/adobe-reader-on-ubuntu-13-10-saucy-salamander/](http://undan.co.in/2013/11/adobe-reader-on-ubuntu-13-10-saucy-salamander/)

If you are still facing problems, I am happy to help.

---

### Post by bugbear6502 on 2013-11-14
> **henshu70 said:**
> 
1. Download the DEB for Adobe Reader from Adobe website

[http://get.adobe.com/uk/reader/](http://get.adobe.com/uk/reader/)



I'm failing at the first hurdle of that - the download is a ".bin" with no other choices offered.

I chmod'd the file, and tried to install enough 32 bits libs to make the installer itself runnable.

 sudo apt-get install ia32-libs

That failed, but told me of a synonym

sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0
 

The installer then ran. But acroread didn't. I've now installed "a lot" of 32 bit
libs, but I still get:

 /opt/Adobe/Reader9/Reader/intellinux/bin/acroread: error while loading shared libraries: libxml2.so.2: cannot open shared object file: No such file or directory

When I try to run acroread.

 Bugbear

---

### Post by henshu70 on 2013-11-14
On the website of Adobe Reader click on

"Do you have a different language or operating system?"

That should give you some choices for what to download.

---

### Post by philinux on 2013-11-14
> **henshu70 said:**
> On the website of Adobe Reader click on

"Do you have a different language or operating system?"

That should give you some choices for what to download.

+1 I'm on 64 bit here. Got the .deb package [http://get.adobe.com/uk/reader/otherversions/](http://get.adobe.com/uk/reader/otherversions/)

Installed it with gdebi, all dependencies satisfied and it runs with no error.

Nothing else to install.

---

### Post by bugbear6502 on 2013-11-14
> **henshu70 said:**
> On the website of Adobe Reader click on

"Do you have a different language or operating system?"

That should give you some choices for what to download.

Thanks for the help, all.

But - Aagh! They've put the file-format options under a dropdown called "Version"!!

 BugBear

---

### Post by bugbear6502 on 2013-11-14
> **henshu70 said:**
> I managed to install latest Adobe Reader both on Ubuntu 13.10 64-bit and after many hours of trial and error also on Kubuntu 13.10 64-bit

**For Ubuntu 13.10 Saucy Salamander 64-bit**

This was easy, the following method was working straight out of the box:

1. Download the DEB for Adobe Reader from Adobe website

[http://get.adobe.com/uk/reader/](http://get.adobe.com/uk/reader/)

2. Install with following commands

sudo dpkg -i --force-architecture AdbeRdr9.5.5-1_i386linux_enu.deb && sudo apt-get -f install

To explain this, the switch **-i --force-architecture** installs 32-bit architecture and **-f install** installs missing libraries


I have now done this, but I still get

/opt/Adobe/Reader9/Reader/intellinux/bin/acroread: error while loading shared libraries: libxml2.so.2: cannot open shared object file: No such file or directory

Do I simply need a 32 bit libxml2? Anyone know the package name?

 BugBear

---

### Post by philinux on 2013-11-14
> **bugbear6502 said:**
> I have now done this, but I still get

/opt/Adobe/Reader9/Reader/intellinux/bin/acroread: error while loading shared libraries: libxml2.so.2: cannot open shared object file: No such file or directory

Do I simply need a 32 bit libxml2? Anyone know the package name?

 BugBear

You dont need any of that. Just get the deb file and install with gdebi. Install gdebi first. See post 15

---

### Post by bugbear6502 on 2013-11-14
> **philinux said:**
> You dont need any of that. Just get the deb file and install with gdebi. Install gdebi first. See post 15

Done that (although I'd already installed the deb with dpkg), which I suspect comes to much the same thing.

Still get the same error.

/opt/Adobe/Reader9/Reader/intellinux/bin/acroread: error while loading shared libraries: libxml2.so.2: cannot opened object file: No such file or directory
 
  BugBear

---

### Post by philinux on 2013-11-14
Uninstall the lot. Autoremove. Find and delete anything left. Then start again..

---

### Post by bugbear6502 on 2013-11-15
> **philinux said:**
> Uninstall the lot. Autoremove. Find and delete anything left. Then start again.

I did 
  sudo dpkg -P adobereader-enu
  sudo apt-get autoremove

and not much happened. In particular, 

  dpkg --get-selections | grep -i 386 

shows a large number of packages.

Is there a way in debian to find out "used by" (as opposed to "depends on") information for packages?

 BugBear

---

### Post by philinux on 2013-11-15
> **bugbear6502 said:**
> I did 
  sudo dpkg -P adobereader-enu
  sudo apt-get autoremove

and not much happened. In particular, 

  dpkg --get-selections | grep -i 386 

shows a large number of packages.

Is there a way in debian to find out "used by" (as opposed to "depends on") information for packages?

 BugBear

Easiest way i know is to open a package with gdebi. It shows all.

---

### Post by bugbear6502 on 2013-11-15
OK, I cleaned out each and every i386 package, ran autoremove, system showed clean, then I installed the AdbeRdr9.5.5-1_i386linux_enu.deb with gdebi, tried to run acroread and got...

/opt/Adobe/Reader9/Reader/intellinux/bin/acroread: error while loading shared libraries: libxml2.so.2: cannot open shared object file: No such file or directory

The same damn error.

Further, running "ldd /opt/Adobe/Reader9/Reader/intellinux/bin/acroread"
on that executable shows that rather a lot of libraries are missing;
    libBIB.so => not found
        libBIBUtils.so => not found
        libACE.so => not found
        libAGM.so => not found
        libCoolType.so => not found
        libAXE8SharedExpat.so => not found
        libJP2K.so => not found
        libAdobeXMP.so => not found
        libicuuc.so.36 => not found
        libssl.so.0.9.8 => not found
        libcrypto.so.0.9.8 => not found
        libxml2.so.2 => not found
        libstdc++.so.6 => not found
        libResAccess.so => not found


 BugBear

---

### Post by philinux on 2013-11-15
All those files on my system are in /opt/Adobe/Reader9/Reader/intellinux/lib/

Might be worth uninstall all again but this time before installing with gdebi use gksu nautilus to remove all from /opt

---

### Post by bugbear6502 on 2013-11-15
Adding in the library path this reduces to:

LD_LIBRARY_PATH=/opt/Adobe/Reader9/Reader/intellinux/lib ldd /opt/Adobe/Reader9/Reader/intellinux/bin/acroread

only libxml2 and libstdc++ are missing.

I manually installed libxml2:

sudo apt-get install -y libxml2:i386

which ran fine.

I was then left with only one missing dependancy;  libstdc++.so.6 => not found

I attempted:

sudo apt-get install -y libstdc++:i386

But got the following somewhat complex response:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libstdc++6-4.4-dev:i386 : Depends: g++-4.4:i386 (= 4.4.7-2ubuntu2) but it is not going to be installed
 libstdc++6-4.6-dbg:i386 : Conflicts: libstdc++6-4.4-dbg:i386 but 4.4.7-2ubuntu2 is to be installed
 libstdc++6-4.6-dev:i386 : Depends: g++-4.6:i386 (= 4.6.4-3ubuntu1) but it is not going to be installed
 libstdc++6-4.7-dbg:i386 : Conflicts: libstdc++6-4.4-dbg:i386 but 4.4.7-2ubuntu2 is to be installed
                           Conflicts: libstdc++6-4.6-dbg:i386 but 4.6.4-3ubuntu1 is to be installed
 libstdc++6-4.8-dbg:i386 : Conflicts: libstdc++6-4.4-dbg:i386 but 4.4.7-2ubuntu2 is to be installed
                           Conflicts: libstdc++6-4.6-dbg:i386 but 4.6.4-3ubuntu1 is to be installed
                           Conflicts: libstdc++6-4.7-dbg:i386 but 4.7.3-7ubuntu3 is to be installed
E: Unable to correct problems, you have held broken packages.

If anyone can advise, I'd be grateful.

 BugBear

---

### Post by philinux on 2013-11-15
Odd that package is here on my system.
```
locate libstdc++.so.6
/usr/lib/i386-linux-gnu/libstdc++.so.6
/usr/lib/x86_64-linux-gnu/libstdc++.so.6
```

---

### Post by bugbear6502 on 2013-11-15
Apologies - despite the "failure" with the complex message that I posted up-thread, enough got installed
that acroread now runs.


EDIT: no it doesn't. Amidst all the confusion, virtual boxes and ssh tunnels I've been running,
the "good" acroread was on another machine. The Ubuntu 13.10 machines continues
to exhibit the missing libstdc++.so.6 behaviour.

 BugBear

---

### Post by SheamusPatt on 2013-11-16
I found an easy and very satisfactory solution on the thread "(General Help) -> acroread":

please follow the instructions for installing Adobe Reader here: [[COLOR=Red]**Ask Ubuntu: Adobe Reader Installation**[/COLOR]]("http://askubuntu.com/questions/89127/how-do-i-install-adobe-acrobat-reader")

The short answer is, there's already a repository called Canonical Partners with the right bits. There's no need to mess around with Adobe's install script (which didn't work for me). Enable the repository (an upgrade disables it), then just install acroread.

---

### Post by bugbear6502 on 2013-11-18
> **bugbear6502 said:**
> Apologies - despite the "failure" with the complex message that I posted up-thread, enough got installed
that acroread now runs.


EDIT: no it doesn't. Amidst all the confusion, virtual boxes and ssh tunnels I've been running,
the "good" acroread was on another machine. The Ubuntu 13.10 machines continues
to exhibit the missing libstdc++.so.6 behaviour.

 BugBear

I have now fixed the final  "missing libstdc++.so.6" behavior as per this thread:

[http://askubuntu.com/questions/371564/adobe-reader-not-initializing](http://askubuntu.com/questions/371564/adobe-reader-not-initializing)

Solution:

Install lib32stdc++6 from software center.

If anyone can explain why that is different to other methods, I'm all ears.

 BugBear

---

### Post by coffeecat on 2013-11-18
> **SheamusPatt said:**
> I found an easy and very satisfactory solution on the thread "(General Help) -> acroread":

please follow the instructions for installing Adobe Reader here: [[COLOR=Red]**Ask Ubuntu: Adobe Reader Installation**[/COLOR]]("http://askubuntu.com/questions/89127/how-do-i-install-adobe-acrobat-reader")

The short answer is, there's already a repository called Canonical Partners with the right bits. There's no need to mess around with Adobe's install script (which didn't work for me). Enable the repository (an upgrade disables it), then just install acroread.

Are you using Ubuntu 13.10, the subject of this thread? At the time of writing, the acroread packages are not yet in the partner repository for 13.10/Saucy, only for earlier releases. There is usually a several week delay before the acroread packages for the current release of Ubuntu appear in the partner repository. And if you look at the Ask Ubuntu link you posted, you'll see that the posts are quite old.

I'll post the URL of the partner repository page for Acroread for reference. At the time of this post, the 13.10 packages are not there. Once packages for saucy appear in the link, people will be able to use the partner repository for installing Acroread.

[http://archive.canonical.com/ubuntu/pool/partner/a/acroread/](http://archive.canonical.com/ubuntu/pool/partner/a/acroread/)

---

### Post by philinux on 2013-11-18
@coffeecat I don't think it will ever hit the partner repo in future.

[https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/1176131](https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/1176131)

---

### Post by coffeecat on 2013-11-18
> **philinux said:**
> @coffeecat I don't think it will ever hit the partner repo in future.

[https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/1176131](https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/1176131)

@philinux, thanks for that. Yes, seems like acroread will be a thing of the past in Ubuntu. The directly downloaded AdbeRdr9.5.5-1_i386linux_enu.deb package gives a "The package is of bad quality" message if you try to install it with Software Centre. If anyone wants something more featured than the default Evince and doesn't want a dated version of Adobe reader, okular is worth a try.

---

### Post by mukeshhpatel on 2013-12-05
> **TheGrep said:**
> I had to install the 32 bit version of libxml2 to get it to work on my 64 bit installation. Simply do this:

sudo apt-get install libxml2:i386

Thank you save my time.

---

### Post by dominique-hausser on 2013-12-09
> **Nick Payne said:**
> Adobe reader is the only PDF reader that can open PDF portfolios. None of the 3rd party readers work with portfolios.

Hello,
In fact Okular is able to open portfolios. I agree that's a two step job, first saving each file and then read it.
Have a nice day.
Dominique

---

