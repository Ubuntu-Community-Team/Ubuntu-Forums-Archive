---
title: "Is the 'Unity Revamped' ppa working atm?"
date: 2012-12-10
forum: General Help
---

### Post by Baldrick_NZ on 2012-12-10
I have the ppa for dodge windows installed via synaptic. It's worked well until the latest Canonical Unity update. The ppa is still there when you view it in software sources, but no longer shows up in synaptic when you click on the 'origin' button.

Does this mean that the dodge windows ppa is broken, or maybe that it doesn't have any updates at this point in time?

I ask because unity has updated to 5.18 and I can't seem to get dodge windows to work again.

Any help would be much appreciated.

Baldrick

(This was posted on a sub-forum on this site, but I marked it as solved when I realised this was the better place for it. Hope that's ok. Cheers)

---

### Post by SantaFe on 2012-12-10
From what I've heard, it doesn't work in Ubuntu 12.10.  I guess when they figure out how to make it work they'll update the PPA's.

But if I'm wrong, I'm sure someone will point it out.  I use Xubuntu 12.10 myself so I'm not too up on Ubuntu/Unity stuff. :)

---

### Post by pansmanse on 2012-12-11
Removing the workspace switcher does not seem to be working in 12.04 either. Launchpad does not indicate any outstanding builds.

---

### Post by Baldrick_NZ on 2012-12-11
Bumpety, Bump Bump Bump... :-) Any help? Anyone?

---

### Post by monkeybrain2012 on 2012-12-11
> **Baldrick_NZ said:**
> I have the ppa for dodge windows installed via synaptic. It's worked well until the latest Canonical Unity update. The ppa is still there when you view it in software sources, but no longer shows up in synaptic when you click on the 'origin' button.



The "origin" button shows the version installed, this means that the version of the ppa is not installed because a more updated version of Unity has been installed. You can downgrade it to the ppa version or wait for the ppa to update. 

To downgrade Unity, open synaptic, choose Unity and then go to Packages > Forced Version and choose the ppa's version, after that choose "locked version". If you downgrade Unity you will have to downgrade and lock other Unity related packages as well.

---

### Post by Baldrick_NZ on 2012-12-12
> **monkeybrain2012 said:**
> The "origin" button shows the version installed, this means that the version of the ppa is not installed because a more updated version of Unity has been installed. You can downgrade it to the ppa version or wait for the ppa to update. 

To downgrade Unity, open synaptic, choose Unity and then go to Packages > Forced Version and choose the ppa's version, after that choose "locked version". If you downgrade Unity you will have to downgrade and lock other Unity related packages as well.

I've just tried that, but instead of reverting to the previous 'revamped' version it removed unity altogether! Thanks for the help anyway. Looks like I might just have to wait for the dev's update.

While I'm thankful for the dev of this feature, it would be far better if Mr. Shuttleworth back-tracked on his decision to remove the native dodge version, and add it again - even if not activated by default. 
IMO, this is one of the leading features that sets Ubuntu apart not only from other distros, but also Windows.

---

### Post by SSOMaster on 2012-12-13
> **Baldrick_NZ said:**
> 
IMO, this is one of the leading features that sets Ubuntu apart not only from other distros, but also Windows.

I'm with you all the way on this one ;)

---

### Post by iurpas on 2012-12-13
amazing luck...came back from 12.10, unhappy with the release, installed mint 14, but still and again unhappy decided to go back to 12.04..whence..no more dodge windows...jeezz...

I know this doesn't help...but just had to say that I'm one of the several ubuntu users that do not get why this feature had to be removed completely from the OS..

Rui

---

### Post by mc4man on 2012-12-13
> **Baldrick_NZ said:**
> I've just tried that, but instead of reverting to the previous 'revamped' version it removed unity altogether! Thanks for the help anyway. Looks like I might just have to wait for the dev's update.

If you wanted to downgrade the easiest would be to download all the unity packages from the ppa that were upgraded, put in an empty folder, cd to that folder in a terminal & use

sudo dpkg -i *.deb

There would likely be 4 packages involved, one, 'unity-common', has be gotten from the i386 build if on 64 bit
(the 4 packages typically needed are
libunity-core 
unity-common
unity               
unity-service


The current 5.18 unity can be patched & all works as before so maybe the ppa owner will do so, or you can do so yourself, not that hard
(I don't use 12.04 but had an install so gave it a try. The revamped patch needed a little housekeeping/culling but works fine with the 5.18 unity source.

---

### Post by Baldrick_NZ on 2012-12-14
Thanks mc4man, 

so does that mean I need to download the 4 latest files from canonical, or unity revamped? If Unity revamped, I've been to their launchpad site and they don't include these files. Instead they have a source package that needs every part to be compiled separately ([https://launchpad.net/ubuntu/precise/+source/unity/5.18.0-0ubuntu1](https://launchpad.net/ubuntu/precise/+source/unity/5.18.0-0ubuntu1)), but this just confuses me greatly, and I really don't want to end screwing my PC up in the process.

How long does it usually take for the update to show up in the upgrades from the time it's posted to the ppa? It seems odd that the source files for 5.18 are ready to go, but they haven't as yet shown up on the ppa - especially when they were published in the 6th of Dec. Can it really take 8 days (or longer) for it to show up as an update via ppa? 

Another option I have is to use docky or awn in place of the launcher altogether, but neither appeal to me so much.

Thanks again, I really appreciate the help.

---

### Post by mc4man on 2012-12-14
> **Baldrick_NZ said:**
> 
so does that mean I need to download the 4 latest files from canonical, or unity revamped?  ..... and I really don't want to end screwing my PC up in the process.

How long does it usually take for the update to show up in the upgrades from the time it's posted to the ppa? 
From the ppa
It's up to the ppa owner to do new builds, maybe he has lost interest or is busy...

The downgrade with dpkg is quite simple, i could give you some generic instr. & likely you'd do ok.
But might as well be specific & get it correct the 1st. time
Please post whether you are using a 32 bit (i386) or 64 bit (amd64) install 
(uname -m

Also run this in a terminal & post whether the **-dev **package is installed
```
apt-cache policy libunity-core-*
```

---

### Post by Baldrick_NZ on 2012-12-14
Thanks again mc4man, much appreciated!

```
baldrick@baldrick:~$ uname -m
i686
```

and

```
baldrick@baldrick:~$ apt-cache policy libunity-core-*
libunity-core-5.0-dev:
  Installed: (none)
  Candidate: 5.18.0-0ubuntu1
  Version table:
     5.18.0-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
     5.16.0-0ubuntu1+ikarosdev2 0
        500 http://ppa.launchpad.net/ikarosdev/unity-revamped/ubuntu/ precise/main i386 Packages
     5.10.0-0ubuntu6 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main i386 Packages
libunity-core-5.0-5:
  Installed: 5.18.0-0ubuntu1
  Candidate: 5.18.0-0ubuntu1
  Version table:
 *** 5.18.0-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     5.16.0-0ubuntu1+ikarosdev2 0
        500 http://ppa.launchpad.net/ikarosdev/unity-revamped/ubuntu/ precise/main i386 Packages
     5.10.0-0ubuntu6 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main i386 Packages

```

Cheers.

---

### Post by mc4man on 2012-12-14
Open a terminal & run this, then **leave the terminal open** - 
 ```
mkdir unity_down && cd unity_down
```

Then go here in Firefox or whatever, - 
[https://launchpad.net/~ikarosdev/+archive/unity-revamped/+build/3858767](https://launchpad.net/~ikarosdev/+archive/unity-revamped/+build/3858767)

 In the "Built files" section at bottom of page download these 4 .debs into the 'unity_down' folder you just created.
(- right click on each .deb in turn > "save link as", browse to & select the  "unity_down" folder
 (unity_down is in your home folder

libunity-core-5.0-5_5.16.0-0ubuntu1+ikarosdev2_i386.deb
unity_5.16.0-0ubuntu1+ikarosdev2_i386.deb
unity-common_5.16.0-0ubuntu1+ikarosdev2_all.deb
unity-services_5.16.0-0ubuntu1+ikarosdev2_i386.deb


When all are dl'ed & in the unity_down folder (**screen 1**), then return to terminal & run this
```
sudo dpkg -i *.deb
```

Should downgrade all 4 without error, after that log out/in to use.
If dpkg shows any error, (shouldn't), don't fret. read back & see what the issue isor post complete terminal output. **Just don't log out till the downgrade is good**

ex. here on 64 bit of good downgrade

> doug@doug-XPS-M1330:~/unity_down$ sudo dpkg -i  *.deb
dpkg: warning: downgrading libunity-core-5.0-5 from 5.18.0-0ubuntu1 to 5.16.0-0ubuntu1+ikarosdev2.
(Reading database ... 339497 files and directories currently installed.)
Preparing to replace libunity-core-5.0-5 5.18.0-0ubuntu1 (using libunity-core-5.0-5_5.16.0-0ubuntu1+ikarosdev2_amd64.deb) ...
Unpacking replacement libunity-core-5.0-5 ...
dpkg: warning: downgrading unity from 5.18.0-0ubuntu1 to 5.16.0-0ubuntu1+ikarosdev2.
Preparing to replace unity 5.18.0-0ubuntu1 (using unity_5.16.0-0ubuntu1+ikarosdev2_amd64.deb) ...
Unpacking replacement unity ...
Preparing to replace unity-common 5.16.0-0ubuntu1+ikarosdev2 (using unity-common_5.16.0-0ubuntu1+ikarosdev2_all.deb) ...
Unpacking replacement unity-common ...
dpkg: warning: downgrading unity-services from 5.18.0-0ubuntu1 to 5.16.0-0ubuntu1+ikarosdev2.
Preparing to replace unity-services 5.18.0-0ubuntu1 (using unity-services_5.16.0-0ubuntu1+ikarosdev2_amd64.deb) ...
Unpacking replacement unity-services ...
Setting up unity-common (5.16.0-0ubuntu1+ikarosdev2) ...
Setting up unity-services (5.16.0-0ubuntu1+ikarosdev2) ...
Processing triggers for man-db ...
Setting up libunity-core-5.0-5 (5.16.0-0ubuntu1+ikarosdev2) ...
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0 ...
Processing triggers for libglib2.0-0:i386 ...
Setting up unity (5.16.0-0ubuntu1+ikarosdev2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
doug@doug-XPS-M1330:~/unity_down$



---

### Post by Baldrick_NZ on 2012-12-14
Wow, that did it! Thanks bro!

Just one more thing, having reverted back to 5.16, I see the update manager now wants me to update the package, which I won't for now.

Would there be any benefit to permanently disabling those four unity files downloading from canonical (during updates), instead preferring to wait until the 'revamped' version is ready in the ppa? If so, how would one do this?

Thanks again for your help!

---

### Post by mc4man on 2012-12-14
> **Baldrick_NZ said:**
> Wow, that did it! Thanks bro!

Just one more thing, having reverted back to 5.16, I see the update manager now wants me to update the package, which I won't for now.


You could - 
Just refrain from upgrading the 4
If done inadvertently then just cd to unity_down & run the dpkg command again
Look into app pinning which I never do so don't know if it would prevent you from being informed of a new ppa version?

Or - 
it's not that hard to build unity - a couple of ways will work
1. upgrade back to repo 5.18
 get the current source, patch, then build that source  as described in the wiki, skipping getting source from bzr

2. (Best), get the current source, patch, build as .deb's & install with dpkg.
In this case I'd up the version slightly & it won't upgrade until a new unity build is available

(have a new patch here if anyone needs in lieu of ppa getting updated.

---

### Post by Baldrick_NZ on 2012-12-14
> **mc4man said:**
> You could - 
Just refrain from upgrading the 4
If done inadvertently then just cd to unity_down & run the dpkg command again
Look into app pinning which I never do so don't know if it would prevent you from being informed of a new ppa version?

Or - 
it's not that hard to build unity - a couple of ways will work
1. upgrade back to repo 5.18
 get the current source, patch, then build that source  as described in the wiki, skipping getting source from bzr

2. (Best), get the current source, patch, build as .deb's & install with dpkg.
In this case I'd up the version slightly & it won't upgrade until a new unity build is available

(have a new patch here if anyone needs in lieu of ppa getting updated.

I'd be interested in learning more about point 2, and grabbing a copy of the new patch you have.

Cheers again.

---

### Post by mc4man on 2012-12-15
> **Baldrick_NZ said:**
> I'd be interested in learning more about point 2, and grabbing a copy of the new patch you have.

Cheers again.
Sure ck. back later or tomorrow (east usa here
Do you also want to restore the custom color setting in unity's compiz options?
Only found black (000000 with decent opacity) a useful color here..

---

### Post by Baldrick_NZ on 2012-12-15
> **mc4man said:**
> 
Do you also want to restore the custom color setting in unity's compiz options?
Only found black (000000 with decent opacity) a useful color here..

No, happy to stick with black. 

I prolly won't be around much today (Sun morning, NZDT), but I really appreciate your input. I'll check back later in the day.

Cheers.

---

### Post by mc4man on 2012-12-16
Quick C&P to build packaged unity-5.18 with the revamp changes, assumes current unity source in 12.04 as of TODAY (unity_5.18.0-0ubuntu1
Open terminal, leave open till done, will do all from that one terminal to maintain correct prompt locations

```
mkdir -p unity_build && cd unity_build && \
sudo apt-get build-dep unity
```
(above ^ is one single command

When all installed then,
```
apt-get source unity && cd unity-5.18.0
```

Leave the terminal for a moment, dl, (r. click > save link as), & **extract** attached patch,  place in the unity_build folder as in **screen 1**

Then
```
patch -Np1 -i ../revamp-18.patch
```
Should apply cleanly, will quote ex. at the end of this post

To prevent being upgraded we'll just append a .1 to current version, not exactly package building etiquette but doesn't matter for self builds (that's a <dot>1, not just 1, see **screen 2**
```
gedit ~/unity_build/unity-5.18.0/debian/changelog
```
Save & close gedit
then
```
dpkg-buildpackage -rfakeroot -D -us -uc

```

When the build finishes create a folder named in inside unity_build folder, see **screen 3**
Drag & drop the 4 needed .debs into the 'in' folder, ala **screen 4**
finish with 
```
cd ../in && sudo dpkg -i *.deb
```

Then just log out/in
(if dodge isn't working after login then simply open ccsm > unity settings, switch to never then back to dodge

If for any reason this version doesn't suit you you can revert to old ppa version by cd'ing to your unity_down folder & downgrading like before

How the patch com. should look, note prompt location in blue
> doug@doug-XPS-M1330:[COLOR="Blue"]~/unity_build/unity-5.18.0$[/COLOR] patch -Np1 -i ../revamp-18.patch
patching file plugins/unityshell/unityshell.xml.in
patching file plugins/unityshell/src/WindowManager.cpp
patching file plugins/unityshell/src/LauncherOptions.h
patching file plugins/unityshell/src/LauncherControllerPrivate.h
patching file plugins/unityshell/src/Launcher.cpp
patching file plugins/unityshell/src/LauncherController.cpp
patching file plugins/unityshell/src/BamfLauncherIcon.cpp
patching file plugins/unityshell/src/BamfLauncherIcon.h
patching file plugins/unityshell/src/PluginAdapter.cpp
patching file plugins/unityshell/src/unityshell.cpp
patching file plugins/unityshell/src/LauncherHideMachine.cpp
patching file plugins/unityshell/src/Launcher.h
patching file plugins/unityshell/src/LauncherHideMachine.h
patching file plugins/unityshell/src/LauncherController.h
patching file plugins/unityshell/src/WindowManager.h
patching file plugins/unityshell/src/PluginAdapter.h
doug@doug-XPS-M1330:~/unity_build/unity-5.18.0$

---

### Post by iurpas on 2012-12-18
Well...I didn't want to interfere with the thread...but this worked perfectly till the update, it updated Unity and the same behavior was restored.

No problem here. Just saying the patch worked for me.

Thanks

Rui

---

### Post by adoet_t on 2012-12-28
well done, this patched make unity dodge worked..

c,

---

### Post by darior on 2013-01-02
> **mc4man said:**
> Quick C&P to build packaged unity-5.18 with the revamp changes, assumes current unity source in 12.04 as of TODAY (unity_5.18.0-0ubuntu1
Open terminal, leave open till done, will do all from that one terminal to maintain correct prompt locations

```
mkdir -p unity_build && cd unity_build && \
sudo apt-get build-dep unity
```(above ^ is one single command

When all installed then,
```
apt-get source unity && cd unity-5.18.0
```Leave the terminal for a moment, dl, (r. click > save link as), & **extract** attached patch,  place in the unity_build folder as in **screen 1**

Then
```
patch -Np1 -i ../revamp-18.patch
```Should apply cleanly, will quote ex. at the end of this post

To prevent being upgraded we'll just append a .1 to current version, not exactly package building etiquette but doesn't matter for self builds (that's a <dot>1, not just 1, see **screen 2**
```
gedit ~/unity_build/unity-5.18.0/debian/changelog
```Save & close gedit
then
```
dpkg-buildpackage -rfakeroot -D -us -uc

```When the build finishes create a folder named in inside unity_build folder, see **screen 3**
Drag & drop the 4 needed .debs into the 'in' folder, ala **screen 4**
finish with 
```
cd ../in && sudo dpkg -i *.deb
```Then just log out/in
(if dodge isn't working after login then simply open ccsm > unity settings, switch to never then back to dodge

If for any reason this version doesn't suit you you can revert to old ppa version by cd'ing to your unity_down folder & downgrading like before

How the patch com. should look, note prompt location in blue


This work-around by "mc4man" works like a charm!

Thanks a million for your work!

Darior

---

### Post by ontolimbo on 2013-01-04
And to reiterate mc4man's comment about 64-bit users who first download and install only the four Unity-revamped .deb files from [https://launchpad.net/~ikarosdev/+archive/unity-revamped/+build/3858766](https://launchpad.net/~ikarosdev/+archive/unity-revamped/+build/3858766) and then get the following ominous result:

> sudo dpkg -i *.deb
dpkg: warning: downgrading libunity-core-5.0-5 from 5.18.0-0ubuntu1 to 5.16.0-0ubuntu1+ikarosdev2.
(Reading database ... 396451 files and directories currently installed.)
Preparing to replace libunity-core-5.0-5 5.18.0-0ubuntu1 (using libunity-core-5.0-5_5.16.0-0ubuntu1+ikarosdev2_amd64.deb) ...
Unpacking replacement libunity-core-5.0-5 ...
dpkg: warning: downgrading libunity-core-5.0-dev from 5.18.0-0ubuntu1 to 5.16.0-0ubuntu1+ikarosdev2.
Preparing to replace libunity-core-5.0-dev 5.18.0-0ubuntu1 (using libunity-core-5.0-dev_5.16.0-0ubuntu1+ikarosdev2_amd64.deb) ...
Unpacking replacement libunity-core-5.0-dev ...
dpkg: warning: downgrading unity-services from 5.18.0-0ubuntu1 to 5.16.0-0ubuntu1+ikarosdev2.
Preparing to replace unity-services 5.18.0-0ubuntu1 (using unity-services_5.16.0-0ubuntu1+ikarosdev2_amd64.deb) ...
Unpacking replacement unity-services ...
Selecting previously unselected package unity.
Preparing to replace unity 5.16.0-0ubuntu1+ikarosdev2 (using unity_5.16.0-0ubuntu1+ikarosdev2_amd64.deb) ...
Unpacking replacement unity ...
Setting up unity-services (5.16.0-0ubuntu1+ikarosdev2) ...
dpkg: dependency problems prevent configuration of unity:
 unity depends on unity-common (= 5.16.0-0ubuntu1+ikarosdev2); however:
  Version of unity-common on system is 5.18.0-0ubuntu1.
dpkg: error processing unity (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Setting up libunity-core-5.0-5 (5.16.0-0ubuntu1+ikarosdev2) ...
Setting up libunity-core-5.0-dev (5.16.0-0ubuntu1+ikarosdev2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 unity

at least one if not both of the *all.deb packages from the i386 packages at [https://launchpad.net/~ikarosdev/+archive/unity-revamped/+build/3858767](https://launchpad.net/~ikarosdev/+archive/unity-revamped/+build/3858767) also seem to be required in order to avoid the error above.

Update: as for disabling my global menu autohide, I've found that it doesn't seem to matter whether one installs 5.16.0-0ubuntu1+ikarosdev2 or recompiles Unity 5.18.0 with the patches from mc4man (and by the way, my patching resulted in more than four .deb files and I seemed to need also to "sudo dpkg -i libunity-core-5.0-dev_5.18.0-0ubuntu1.1_amd64.deb").  Anyway, in both cases, unfortunately, I haven't found the good disable button appear in Compiz.

Cheers,


> **mc4man said:**
> Open a terminal & run this, then **leave the terminal open** - 
 ```
mkdir unity_down && cd unity_down
```Then go here in Firefox or whatever, - 
[https://launchpad.net/~ikarosdev/+archive/unity-revamped/+build/3858767](https://launchpad.net/~ikarosdev/+archive/unity-revamped/+build/3858767)

 In the "Built files" section at bottom of page download these 4 .debs into the 'unity_down' folder you just created.
(- right click on each .deb in turn > "save link as", browse to & select the  "unity_down" folder
 (unity_down is in your home folder

libunity-core-5.0-5_5.16.0-0ubuntu1+ikarosdev2_i386.deb
unity_5.16.0-0ubuntu1+ikarosdev2_i386.deb
unity-common_5.16.0-0ubuntu1+ikarosdev2_all.deb
unity-services_5.16.0-0ubuntu1+ikarosdev2_i386.deb


When all are dl'ed & in the unity_down folder (**screen 1**), then return to terminal & run this
```
sudo dpkg -i *.deb
```Should downgrade all 4 without error, after that log out/in to use.
If dpkg shows any error, (shouldn't), don't fret. read back & see what the issue isor post complete terminal output. **Just don't log out till the downgrade is good**

ex. here on 64 bit of good downgrade

---

### Post by SSOMaster on 2013-01-13
For 12.04 x64 going for downgrade to unity 5.16 all your unity _down folder has to contain is :

libunity-core-5.0-5_5.16.0-0ubuntu1+ikarosdev2_amd64
unity_5.16.0-0ubuntu1+ikarosdev2_amd64
unity-common_5.16.0-0ubuntu1+ikarosdev2_all
unity-services_5.16.0-0ubuntu1+ikarosdev2_amd64

Works like a charm.

thank you mc4man.

After installing these i got a incomplete update, corupt dependencies warning. 
It was resolved by downloading and installing via dpkh of these packages:


libunity-core-5.0-dev_5.16.0-0ubuntu1+ikarosdev2_amd64
netbook-launcher_5.16.0-0ubuntu1+ikarosdev2_all

Hope it hels.

---

### Post by 10010101 on 2013-01-17
Thanks to mc4man for the patch! :D
It is working good for me, except one little thing: the patch does not make global/app menu always visible :( (like it was in unity-revamped 5.16)
Does anyone knows how to integrate it? Because I think it is the most needed feature in the unity. I'm suspect to defend it because i use a tablet... but anyway, in my opinion it should be implemented.

---

### Post by isaacj87 on 2013-01-21
Hey, guys! I'm sorry if I went MIA, but life has a nasty habit of keeping me busy.

Unfortunately, my thread was taken from me (from the T&T section), so I don't have any way of publicly communicating my status.

I did, however, push an update up to the PPA, and packages (Unity 5.18.0 | Ubuntu 12.04) are currently awaiting building. If they build correctly, the update should be available via my PPA shortly.

Concerning Unity 6.0 and Quantal, I was able to (sort-of) get the "Dodge Windows" functionality working, but it is plagued with frequent crashes and breaks other functionality of Unity. (Not sure why either)

I, unfortunately, do not have time to figure out the issues as I'm very busy with school and work. I hope that someone will pick up the project. Long live dodge windows!

---

### Post by Keronn on 2013-01-23
It works well again (Ubuntu 12.04), thanks for your work Isaac.

---

### Post by 10010101 on 2013-01-25
Thanks Issac, thank you very much!
Hoping the next build will have back the feature to permanently  show the menus *.*

---

### Post by 10010101 on 2013-04-19
There is a new Unity Revamped PPA: ppa:garhuy/unity
Features at [https://launchpad.net/~garhuy/+archive/unity](https://launchpad.net/~garhuy/+archive/unity)

---

### Post by sudo89 on 2013-08-30
> **mc4man said:**
> Quick C&P to build packaged unity-5.18 with the revamp changes, assumes current unity source in 12.04 as of TODAY (unity_5.18.0-0ubuntu1
Open terminal, leave open till done, will do all from that one terminal to maintain correct prompt locations

```
mkdir -p unity_build && cd unity_build && \
sudo apt-get build-dep unity
```
(above ^ is one single command

When all installed then,
```
apt-get source unity && cd unity-5.18.0
```

Leave the terminal for a moment, dl, (r. click > save link as), & **extract** attached patch,  place in the unity_build folder as in **screen 1**

Then
```
patch -Np1 -i ../revamp-18.patch
```
Should apply cleanly, will quote ex. at the end of this post

To prevent being upgraded we'll just append a .1 to current version, not exactly package building etiquette but doesn't matter for self builds (that's a <dot>1, not just 1, see **screen 2**
```
gedit ~/unity_build/unity-5.18.0/debian/changelog
```
Save & close gedit
then
```
dpkg-buildpackage -rfakeroot -D -us -uc

```

When the build finishes create a folder named in inside unity_build folder, see **screen 3**
Drag & drop the 4 needed .debs into the 'in' folder, ala **screen 4**
finish with 
```
cd ../in && sudo dpkg -i *.deb
```

Then just log out/in
(if dodge isn't working after login then simply open ccsm > unity settings, switch to never then back to dodge

If for any reason this version doesn't suit you you can revert to old ppa version by cd'ing to your unity_down folder & downgrading like before

How the patch com. should look, note prompt location in blue


Working...
Thank you...
(Note: my unity version 5.20 still run)

---

