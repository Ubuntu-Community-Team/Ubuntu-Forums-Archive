---
title: "Please assist me"
date: 2007-11-01
forum: General Help
---

### Post by yongkailoon on 2007-11-01
Hi there to all seniors, today is my first day using Ubuntu 7.04 and I need some help. How do you guys uninstall a certain program ? I went to Synaptic and the Add/Remove application but it seems that the function to remove Exaile is not available. Is there a rule that Exaile set that it can't be removed ? :confused:

---

### Post by danpre on 2007-11-01
> **yongkailoon said:**
> Hi there to all seniors, today is my first day using Ubuntu 7.04 and I need some help. How do you guys uninstall a certain program ? I went to Synaptic and the Add/Remove application but it seems that the function to remove Exaile is not available. Is there a rule that Exaile set that it can't be removed ? :confused:

In SYNAPTIC
right click on a program - choose from the list

DANIeL

---

### Post by thirunavukkarasu on 2007-11-01
Hi and welcome to Ubuntu forums!

aptitute remove package-name;

 will remove the package.

Regds,
Thiru.S

---

### Post by mikewhatever on 2007-11-01
Can you not uncheck Exaile in Add/Remove?

---

### Post by Maestro23 on 2007-11-01
Future Reference: Installing Software in Ubuntu
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

How did you install the program?

---

### Post by yongkailoon on 2007-11-01
Alright after giving a try I can tick the Remove option but even after I select Remove completely and apply, Exaile is still there and not removed.

By the way, how do I aptitute remove package-name; ?

---

### Post by yongkailoon on 2007-11-01
> **Maestro23 said:**
> Future Reference: Installing Software in Ubuntu
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

How did you install the program?

I downloaded the source file and then using the ./configure command.

---

### Post by laytek on 2007-11-01
yongkailoon  

Welcome to Ubuntu.

It sounds like you have done things correctly. The program should be gone from your system, if you are the administrator. The listing about Exaile will still be in Synaptic Package Manager so that you could reinstall it in the future if desired. Does this help?

LayTek

---

### Post by HermanAB on 2007-11-01
Note that removing schtuff is even more dangerous to the system health than installing schtuff.

So, I recommend that you forget about removing whateveritis - just ignore it.  Linux programs are typically very small and don't take up much space (well, an exception would be OpenOffice.org!).

Cheers,

H.

---

### Post by yongkailoon on 2007-11-01
> **laytek said:**
> yongkailoon  

Welcome to Ubuntu.

It sounds like you have done things correctly. The program should be gone from your system, if you are the administrator. The listing about Exaile will still be in Synaptic Package Manager so that you could reinstall it in the future if desired. Does this help?

LayTek

Hi there, I think this must be it though. If I remove the whole package meaning I delete the files, is it possible ?

Yea I agree it is small but somehow I still prefer a neat system and to remove programs that are not in use. :)

---

### Post by yongkailoon on 2007-11-01
Just another question, I have already set in Power Management to never Put Display To Sleep but it will still sleep after it is idle for some time. :(

---

### Post by erginemr on 2007-11-01
> **yongkailoon said:**
> I downloaded the source file and then using the ./configure command.

If you installed exaile from the source (I wonder how you did it as a newbie, by the way. Installing programs from the source code is a fairly complex task, that involves installation of extra development packages manually.)

Anyway, if you installed Exaile from the source, the installation is done this way:
1) You open the archive with:
tar xzvf package_name.tar.gz 
or
tar xjvf package_name.tar.bz2

2) You change into the opened archive directory:
cd package_name

3) Once there, you should read the README and INSTALL files to learn the installation method. But generally, the installation is done by issuing the folloeing commands:
./configure
make
sudo make install

4) At this stage, there should be a Makefile created, which you can use to uninstall the same program with
sudo make uninstall

So, if you deleted the installation directory, I suggest you to reinstall Exaile the same way as you did before. But this time, when you are in the installation directory, use the command "sudo make uninstall" to uninstall it.

You cannot uninstall programs that you installed from source by using apt-get, aptitude, dpkg, add/remove or synaptic. These utensils work only for the programs installed from a Debian installation package.

---

### Post by Maestro23 on 2007-11-01
> **erginemr said:**
> If you installed exaile from the source (I wonder how you did it as a newbie, by the way. Installing programs from the source code is a fairly complex task, that involves installation of extra development packages manually.)

Anyway, if you installed Exaile from the source, the installation is done this way:
1) You open the archive with:
tar xzvf package_name.tar.gz 
or
tar xjvf package_name.tar.bz2

2) You change into the opened archive directory:
cd package_name

3) Once there, you should read the README and INSTALL files to learn the installation method. But generally, the installation is done by issuing the folloeing commands:
./configure
make
sudo make install

4) At this stage, there should be a Makefile created, which you can use to uninstall the same program with
sudo make uninstall

So, if you deleted the installation directory, I suggest you to reinstall Exaile the same way as you did before. But this time, when you are in the installation directory, use the command "sudo make uninstall" to uninstall it.

You cannot uninstall programs that you installed from source by using apt-get, aptitude, dpkg, add/remove or synaptic. These utensils work only for the programs installed from a Debian installation package.

Good post. Getting ready to post something just like this.  Dang, too slow.:)

---

### Post by erginemr on 2007-11-01
By the same token, although installation from source traditionally is a very good way to learn the basics of Linux, I would still suggest you to install /uninstall programs with Add/Remove or Synaptic, or better by using the console command "aptitude". It is much easier this way.

Automatic installation techniques have evolved very much lately and there are tons of packages in the Debian universe, that you may easily surf through and try out easily.

---

### Post by erginemr on 2007-11-01
> **Maestro23 said:**
> Good post. Getting ready to post something just like this.  Dang, too slow.:)

:) next time bro...

---

### Post by yongkailoon on 2007-11-01
Well, I am a newbie in Linux but I have an interest for computers so I actually will learn quite fast if someone teaches me. :)

By the way,  thanks for the guide, I will try it now !

---

### Post by mikewhatever on 2007-11-01
> **yongkailoon said:**
> Well, I am a newbie in Linux but I have an interest for computers so I actually will learn quite fast if someone teaches me. :)

By the way,  thanks for the guide, I will try it now !

You could have saved yourself all these troubles by installing from the repositories and not from source file.

---

### Post by yongkailoon on 2007-11-01
> **mikewhatever said:**
> You could have saved yourself all these troubles by installing from the repositories and not from source file.

So actually even if it says it is for 7.10, the 7.04 will work too right ?

---

### Post by erginemr on 2007-11-02
> **yongkailoon said:**
> So actually even if it says it is for 7.10, the 7.04 will work too right ?

Unfortunately no, a package designed for a later distribution usually does not work under a former distribution. I came across this issue under Edgy (6.10). I was still using Edgy well after the release of Feisty (7.04), because I was happy with it and did not want to upgrade. However, in time, for the programs I used new versions have been issued, and not surprisingly, they were usually packaged for Feisty only. 

(I think this is the worst part of Xbuntu systems, you install a version and are stuck with a set of obsolete packages if you decide to stick to it for more than 6 months. Sure Ubuntu developers issue updates to your packages from time to time, but those are mainly security updates only, not an update to a new version excluding the backports. I don’t know if this is the same for other distros or not. I considered for some time to try PC Linux OS, in the faint hope that they might be issuing upgrades to the programs in their repositories. But it was based on KDE and moreover its package management system was on RPM, and by that time, I was already attached to the Gnome desktop and Debian packaging system.)

Anyway, back to our topic, if you try to install a Gutsy (7.10) package to a Feisty (7.04) system, you will most likely get errors / objections from the package manager that it cannot be installed because of such and such conflicts. This is actually quite different than having missing packages, in which case, the package manager would automatically fetch them from the web and install them along with the main program. The libraries that the package manager (be it Synaptic, GDebi, dpkg, apt-get or aptitude) complains is actually existing as part of your system, but is of a lower version than required. And since those libraries are integrated to the existing system tightly, it is almost guaranteed to break it trying to update those libraries as well.

I am not sure if it is the same story when one tries to install the new program from a source package, but quite possibly you would get the same library conflict errors in the “./configure” phase of installation.

---

### Post by erginemr on 2007-11-02
As a case study &#61514;, I had such a problem in the past under Edgy: Fileroller, the default archive manager of Gnome was buggy in that it could not open Rar files and 7-zip files (both should be installed separately first). An exhaustive web search revealed that the errors was originated because of my system&#8217;s language (Turkish, by the way) and the developers had resolved both issues at later versions of Fireroller.

The problem is; those later versions were built for Feisty in mind, and I really did not want to upgrade my highly customize Edgy system to my tastes. I had attempted a few times to upgrade it to Feisty but had several showstopper issues, so had to return back to Edgy in the end, thanks to my previous backups. (Speaking of backups by the way, it seems you are also like me who likes to tinker with his system by installing / removing packages on a daily basis ;P, then I&#8217;d recommend you to back up your system periodically with the method described in the following thread:
[http://ubuntuforums.org/showthread.php?t=591073](http://ubuntuforums.org/showthread.php?t=591073) and originally in
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087))

Anyway, I did not feel like playing with the source package, because that would mean fetching and installing probably a multitude of graphical development packages, gtk-dev, gnome-dev, and what not. So, I downloaded the Feisty version of Fileroller, crossed my fingers and double-clicked it to see that it cannot be installed because it conflicted with a library package A installed in my system. Determined as I was, I downloaded that one as well, just to see that it conflicted with packages B & C. Downloading B & C led me to quest for E & F, and then G, H & I. Soon, I was in what is known along Linux enthusiasts as a &#8220;Dependency Hell&#8221;.

After all that struggle, with the final package being a font-handling library, libfont-blah blah, I was greeted by a desktop where all fonts were gone and there were rectangles in their stead!! Luckily, I had backed up my system as explained above, it was easy to return back to my working system.

In a nutshell, if you are lucky, the Gutsy package you are trying to install (by double-clicking on it or by issuing &#8220;dpkg -- install package_name.deb&#8221; from the console) will not require any conflicting package and you are good to go. It may as well protest with a list of conflicting packages. In that case, I suggest you to stop there and not force the situation any more.

---

