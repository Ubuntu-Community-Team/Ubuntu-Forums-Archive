---
title: "skype install 15.04 64-bit"
date: 2015-06-21
forum: General Help
---

### Post by dnamurphy on 2015-06-21
Hi all,

I've been going around in circles trying to install skype on my Xubuntu 15.04 64-bit platform. I'm shocked at how much trouble I've had with it :mad:

My problems are very similar to those echoed here:

[http://community.skype.com/t5/Linux/Installation-Fails-on-Debian-Stable-64-bit/td-p/3](http://community.skype.com/t5/Linux/Installation-Fails-on-Debian-Stable-64-bit/td-p/3)

...and seem to hinge on failed / unmet dependencies. After enabling 386 arch ```
sudo dpkg --add-architecture i386
```

I've tried:

1. Installing the official skype .deb:
```

**sudo dpkg -i skype-ubuntu-precise_4.3.0.37-1_i386.deb **
Selecting previously unselected package skype.
(Reading database ... 189879 files and directories currently installed.)
Preparing to unpack skype-ubuntu-precise_4.3.0.37-1_i386.deb ...
Unpacking skype (4.3.0.37-1) ...
dpkg: dependency problems prevent configuration of skype:
 **skype depends on libqtwebkit4 (>= 2.2~2011week36).**

dpkg: error processing package skype (--install):
 dependency problems - leaving unconfigured
Processing triggers for hicolor-icon-theme (0.14-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu5) ...
Processing triggers for dbus (1.8.12-1ubuntu5) ...
Errors were encountered while processing:
 skype

```

In common with [http://ubuntuforums.org/showthread.php?t=2249743](http://ubuntuforums.org/showthread.php?t=2249743) - attempts to install libqtwebkit4 result in apt-get (+ all other alternatives - aptitude etc) suggesting removal of (among many others) **xubuntu-core** and **xubuntu-desktop** :eek: no thanks!

2. Install from repository, enabling sudo dpkg --add-architecture i386:
```

**sudo apt-get install skype-bin:i386**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 skype-bin:i386 : Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not going to be installed
                  Depends: libgl1-mesa-glx:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

It's worth noting I had no problems with Skype under Xubuntu 14.10. If anyone has any insight (or can walk me through a workaround to get it installed), please let me know. I'd also be very happy if there were a statically-linked binary to try, if anyone has one that might be compatible with the architecture.

Many thanks!

---

### Post by Bucky Ball on 2015-06-21
*Thread moved to **General Help**.*

Welcome. You don't need to install it from a third party or from Skype. Install it from Software Centre if you can. That way the dependencies will be taken care of. If you can't let us know the errors.  

Open 'Software and Updates' (not using Ubuntu and Unity but should be that) and in the Other Software tab, enable 'Canonical Partners'. Update> Open SCentre> search, it should be there, and install. If you've done this, disregard.

See the section under 'GUI WAY' in the answers [here]("http://askubuntu.com/questions/293693/how-to-install-skype-with-ubuntu-13-04").

---

### Post by Mike_Walsh on 2015-06-21
I concur with Bucky, here.

The way I've always done it:-

Enable the 'Canonical Partners' repo in 'Software & Updates'.

Then, in the terminal:-

```
sudo apt-get update
```

entering your password when requested, followed by

```
sudo apt-get install skype
```


Works **every** time. Bucky's link also shows, further down the page, how to do it entirely from the CLI (terminal). Both methods work equally well; I just prefer to carry out the actual install via the terminal. I occasionally find that the GUI method will stall; the CLI method never does.

Hope that helps.


Regards,

Mike. ;)

---

### Post by dnamurphy on 2015-06-21
Hi Bucky, Mike,

Thanks first of all for moving my post to the correct area: I'd seen other Skype-woes in that section, so it seemed appropriate to post in there, but thanks for finding it the right home on the forum :-)

Thank you also for the advice: I agree that normally installing from the supplied repository is the best thing to do, and prevents any issues with dependencies. That said (and this is generally the exception!), I've historically just taken the .deb directly from Skype. I deferred to your experience, and tried it after adding "Canonical Partners" and the result is the same.

I get a "Package dependencies cannot be resolved" error in the Software Centre, with "Details":

```

The following packages have unmet dependencies:

skype: Depends: skype-bin but it is a virtual package

```

So next, to see if I have any luck following from above, I search for skype-bin in the software centre, (which points to skype-bin:386), and try to install that, again with the "Package dependencies cannot be resolved" error:

```

The following packages have unmet dependencies:

skype-bin:i386: Depends: libgcc1 (>= 1:4.1.1) but 1:5.1~rc1-0ubuntu1 is to be installed
                Depends: libqt4-dbus (>= 4:4.5.3) but 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 is to be installed
                Depends: libqt4-network (>= 4:4.8.0) but 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 is to be installed
                Depends: libqt4-xml (>= 4:4.5.3) but 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 is to be installed
                Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 is to be installed
                Depends: libqtgui4 (>= 4:4.8.0) but 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 is to be installed

```

When I try to install skype via apt-get:

```

**sudo apt-get install skype**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 skype : Depends: skype-bin
**E: Unable to correct problems, you have held broken packages.**

```

I ran Synaptic to try and "fix Broken packages", which it claims to have done, but I see no difference in the output here when trying again.... :?

---

### Post by Bucky Ball on 2015-06-22
I would say:

```
sudo apt-get remove skype

```

If you have the Canonical Partners repo on:

```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install skype
```

Report any and all errors. 

Same? If you're having to do anything more than that, there is something wrong beyond Skype not installing as if installed from the official repos, all dependencies will be taken care of. If they're not, then perhaps there are leftovers from your previous attempts with third-party versions that are screwing things up or there is something wrong beyond just Skype and this is a symptom rather than the problem.

What happens when:

---

### Post by dnamurphy on 2015-06-27
Hi BB, 

Apologies for only coming back to this now - I've not had access to my laptop until today. So, I performed the steps above, all being fine apart from the last stage:

```

**sudo apt-get install skype**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.

```

The **aptitude** alternative sometimes gives more information, so I've posted the details here:

```

**sudo aptitude install skype**
The following NEW packages will be installed:
  gstreamer1.0-plugins-base:i386{a} libcdparanoia0:i386{a} libdbusmenu-qt2:i386{a} libdrm-intel1:i386{a} libdrm-nouveau2:i386{a} libdrm-radeon1:i386{a} 
  libdrm2:i386{a} libedit2:i386{a} libelf1:i386{a} libgl1-mesa-dri:i386{ab} libgl1-mesa-glx:i386{ab} libglapi-mesa:i386{ab} libglu1-mesa:i386{a} 
  libgstreamer-plugins-base1.0-0:i386{a} libgstreamer1.0-0:i386{a} libllvm3.6:i386{a} liborc-0.4-0:i386{a} libpciaccess0:i386{a} libqt4-opengl:i386{a} 
  libqtwebkit4:i386{a} libtheora0:i386{a} libtinfo5:i386{a} libtxc-dxtn-s2tc0:i386{a} libudev1:i386{a} libvisual-0.4-0:i386{a} 
  libvisual-0.4-plugins:i386{a} libx11-xcb1:i386{a} libxcb-dri2-0:i386{a} libxcb-dri3-0:i386{a} libxcb-glx0:i386{a} libxcb-present0:i386{a} 
  libxcb-sync1:i386{a} libxshmfence1:i386{a} libxxf86vm1:i386{a} skype skype-bin:i386{a} sni-qt:i386{a} 
0 packages upgraded, 37 newly installed, 0 to remove and 0 not upgraded.
Need to get 45.5 MB of archives. After unpacking 147 MB will be used.
The following packages have unmet dependencies:
 libgl1-mesa-dri : Breaks: libgl1-mesa-dri:i386 (!= 10.6.0~git20150423.125574d1-0ubuntu0ricotz~utopic) but 10.5.2-0ubuntu1 is to be installed.
 libgl1-mesa-dri:i386 : Breaks: libgl1-mesa-dri (!= 10.5.2-0ubuntu1) but 10.6.0~git20150423.125574d1-0ubuntu0ricotz~utopic is installed.
 libglapi-mesa : Breaks: libglapi-mesa:i386 (!= 10.6.0~git20150423.125574d1-0ubuntu0ricotz~utopic) but 10.5.2-0ubuntu1 is to be installed.
 libglapi-mesa:i386 : Breaks: libglapi-mesa (!= 10.5.2-0ubuntu1) but 10.6.0~git20150423.125574d1-0ubuntu0ricotz~utopic is installed.
 libgl1-mesa-glx : Breaks: libgl1-mesa-glx:i386 (!= 10.6.0~git20150423.125574d1-0ubuntu0ricotz~utopic) but 10.5.2-0ubuntu1 is to be installed.
 libgl1-mesa-glx:i386 : Breaks: libgl1-mesa-glx (!= 10.5.2-0ubuntu1) but 10.6.0~git20150423.125574d1-0ubuntu0ricotz~utopic is installed.
Internal error: found 2 (choice -> promotion) mappings for a single choice.
Internal error: found 2 (choice -> promotion) mappings for a single choice.
The following actions will resolve these dependencies:

      Keep the following packages at their current version:       
1)      libgl1-mesa-dri:i386 [Not Installed]                      
2)      libgl1-mesa-glx:i386 [Not Installed]                      
3)      libglapi-mesa:i386 [Not Installed]                        
4)      libglu1-mesa:i386 [Not Installed]                         
5)      libqt4-opengl:i386 [Not Installed]                        
6)      libqtwebkit4:i386 [Not Installed]                         
7)      libvisual-0.4-plugins:i386 [Not Installed]                
[B]8)      skype [Not Installed]                                     
9)      skype-bin:i386 [Not Installed]                            
[/B]
      Leave the following dependencies unresolved:                
10)     libvisual-0.4-0:i386 recommends libvisual-0.4-plugins:i386

```

If I reject this solution, the "alternative" aptitude suggests is to remove pretty much everything, including (and likely because of) **xubuntu-core** and **xubuntu-desktop  **. I'm not running a particularly non-standard setup, so I can't really figure out what's wrong here. Had no problems in 14.10 LTS, but it will be a bit of a mess if I want to downgrade.

---

### Post by Bucky Ball on 2015-06-27
If you have xubuntu-desktop installed, forget about xubuntu-core. You basically have Xubuntu installed. Defeats the purpose of a *buntu-core install if you install *buntu-desktop. A standard Ubuntu is basically the mini.iso (the Ubuntu base kernel) and ubuntu-desktop. ;)

So, let's consider you are running Xubuntu. Either way, I don't have many clues at this end. I'm don't have a 15.04 install (or perhaps I do, I'll have a look tomorrow) that I can test it on. I stick to LTS releases.

---

### Post by cariboo on 2015-06-27
I just installed skype on my laptop, the complete name of the skype-bin package is:

```
skype-bin_4.3.0.37-0ubuntu0.12.04.1_i386.deb
```

If you install it using gdebi, it should pick up all the dependencies.

---

### Post by dnamurphy on 2015-06-27
Hi cariboo,

Thanks for the suggestion. I downloaded the .deb and tried with gdebi - again, I come against the same dependency issue:

```

**sudo gdebi skype-bin_4.3.0.37-0ubuntu0.12.04.1_i386.deb **
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Building data structures... Done 
This package is uninstallable
Cannot install 'libqtwebkit4:i386'

```

I don't think it's the route by which I install that's the problem, it's more that there is an underlying issue with the package requirements that would involve me removing most of xubuntu just to get it running.

---

### Post by dnamurphy on 2015-06-27
Hi Bucky Ball,

As per the header, I'm running Xubuntu. I'm not aware I myself "installed" xubuntu-core AND/OR xubuntu-desktop - I'm pretty sure these were "installed" (AFAIK, they are meta-packages?) during the actual OS install. I assume removal of them (and all the packages therefore that depend in them) as good as removes xfce.... I certainly don't want to do anything so drastic! 

But yes, lesson learnt: LTS, LTS, LTS! I don't even know why I thought it would be a good idea to update to 15.04! I seriously don't want to have to do a re-install just for the sake of getting Skype running. I do have dual boot on the laptop, but it's extremely annoying to have to restart (and lose my in-progress work) if I have a telecon!

---

### Post by Bucky Ball on 2015-06-28
> **cariboo said:**
> I just installed skype on my laptop, the complete name of the skype-bin package is:

```
skype-bin_4.3.0.37-0ubuntu0.12.04.1_i386.deb
```

If you install it using gdebi, it should pick up all the dependencies.

Try that. It's not about installing Skype directly, its advice for installing the missing dependencies. ;)

---

### Post by dnamurphy on 2015-06-28
Hi Bucky,

I did this here: [http://ubuntuforums.org/showthread.php?t=2283386&p=13311400#post13311400](http://ubuntuforums.org/showthread.php?t=2283386&p=13311400#post13311400)

```
Cannot install 'libqtwebkit4:i386'
```

I attempted with aptitude (as this gives sometimes more information about missing packages / conflicts etc) - attempt listed here: [http://ubuntuforums.org/showthread.php?t=2283386&p=13311242#post13311242](http://ubuntuforums.org/showthread.php?t=2283386&p=13311242#post13311242)

I'm not sure where to go from this point to try and fix it...

---

