---
title: "installing adobe air on 13.10"
date: 2013-10-18
forum: General Help
---

### Post by darquan0 on 2013-10-18
I *am* an _absolute beginner_. Never worked with linux before this week. So maybe this has to be posted in "absolute beginner" forums.
But I did search for answers to my question (how to install **adobe air**). None work in _13.10_ now.
Think I made a mistake upgrading (already had to rollback kernel to make wifi card work again and repair damaged boot after upgrade... but that happeded to be easy), but anyway.
I installed _**kubuntu 13.04 x64**_ on brand new asus x502ca just two days ago, and I never worked with linux before. So I only began to set up working enviroinment, and everything was fine. Untill **13.10** just started to update without any questions and it was too late to scream "hey, what's the big deal? how about **asking ME **first?". Reboot.
Notebook refused to find bootable hard drive. Okay, dealt with that. Wifi card (ralink ra5390) does not work on 3.11 kernel. Reinstal kernel on a system which I never seen two days ago? Solved.

Now. Problems begin here. In our work we I need a tool that requires adobe air. Actually, it's an ".air" application.
google "adobe air ubuntu", find .deb package [here]("http://ubuntuforums.org/showthread.php?t=1929046").
```
_root#dpkg -i adobeair_2*_
dpkg: dependency problems prevent configuration of adobeair:
 adobeair depends on ia32-libs-gtk; however:
  Package ia32-libs-gtk is not installed.

dpkg: error processing adobeair (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 adobeair
```
Okay, so we need ia32-libs-gtk...
```
_root# apt-get install ia32-libs-gtk_
Package ia32-libs-gtk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'ia32-libs-gtk' has no installation candidate
```

Okay... google again. "install ia32-libs". Wow, **they are deprecated too.** And developers say we don't need those now, period.

Going to adobe site, [finding *their* instructions]("http://helpx.adobe.com/air/kb/install-air-2-64-bit.html#main_Install_AIR_2_on_64_bit_Ubuntu_9_04"). For Ubuntu 9.04 x64... oh well.
Install getlibs-all.deb. Installed.
Next.
```
_root#getlibs -l libhal-storage.so.1_
E: Package 'ia32-libs' has no installation candidate
No match for libhal-storage.so.1
No packages to install
```Guess somebody forgot to tell theese libs that we don't need ia32-libs now...
```
[U]root#getlibs -l libgnome-keyring.so.0.1.1
[/U]E: Package 'ia32-libs' has no installation candidate
No match for libgnome-keyring.so.0.1.1
No packages to install
```Does not work either.

Now... > Download the 32-bit versions of libnss and libnspr from the following locations. Both links are broken.
Guess guide is unusable now.

Register on forum... let's [search the forum]("http://ubuntuforums.org/search.php?searchid=1222795")! Maybe someone already encountered this.
Some topics are about wine. Guess that'll be my last resort.
Some even say there's a version of adobe air in software center... Well, there is none in my "muon discover" (*who replaced fine, elegant "muon software center" from 13.04 with that flashy bling-bling "muon discover" anyway and how to roll back that, anyway?...*).
Others are about "you need to install ia32-libs". Those are deprecated now...

So. I went and ran ./AdobeAIRInstaller.bin on my own risk.
It displayed a nice popup window with link to adobe help. That is broken and outdated, as I already discovered.
And then nothing.
But, I now have "Adobe AIR application installer" in my "start menu" (I don't know how it's called in KDE yet...).
Which simply does not start. I opens up a window on taskbar, does something for a short while then disappears.
".air" applications produce same effect.

Finally.

If anyone already installed adobe air 2.6 on fresh ubuntu 13.10 and has a working solution, please advise.
If anyone has a suggestion on how to see what happens when "air app installer" tries to start but fails, please point me. Logs maybe. I don't even know where those linux apps store their logs yet...

UPDATE:
found "/opt/Adobe AIR/Versions/1.0/Adobe AIR Application Installer"
On trying to ```
_root#"./Adobe AIR Application Installer"_
Error loading the runtime (libnss3.so: cannot open shared object file: No such file or directory)
```
But...
```
_root#apt-get install libnss3_
libnss3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
What can I do with *this*?

---

### Post by dane2 on 2013-10-19
I followed these instructions: 

[http://www.thepowerbase.com/2013/06/how-to-install-adobe-air-in-ubuntu-13-04/](http://www.thepowerbase.com/2013/06/how-to-install-adobe-air-in-ubuntu-13-04/)
 
And to get ia-32 libs, I did this: 
[http://wiki.phoenixviewer.com/ia32-libs-in-ubuntu-13-10](http://wiki.phoenixviewer.com/ia32-libs-in-ubuntu-13-10)

Also, there is a line about linking gnome-keyring.  The location is different so I had to do this before air would install:
# ln -s /usr/lib32/i386-linux-gnu/libgnome-keyring.so.0 /usr/lib/libgnome-keyring.so.0

EDIT: forgot to give credit.  I found this solution cuz of this post: [http://community.secondlife.com/t5/Second-Life-Viewer/Ubuntu-13-10-and-the-death-of-ia32-libs/m-p/2269003](http://community.secondlife.com/t5/Second-Life-Viewer/Ubuntu-13-10-and-the-death-of-ia32-libs/m-p/2269003)

Hope this helps! 
-d

---

### Post by salai2 on 2013-10-22
Have you tried installing the 32bit version of the libnss3 packages from the saucy repos?

I had the same problem with an Adobe Air application which did not want to start because libnss3.so was missing (as you have), and installing libnss3-1d:i386 fixed this issue for me.

All I did was a:
sudo apt-get install libnss3-1d:i386

This pulled some more 32bit packages, and Adobe Air started working again. I am not sure that this will get Adobe Air working for you, since I had it already installed and working in raring, before I upgraded to saucy.

---

