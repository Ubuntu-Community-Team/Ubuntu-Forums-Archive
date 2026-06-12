---
title: "[SOLVED] I need a fresh start to load compiz"
date: 2008-06-19
forum: General Help
---

### Post by SteveNorman on 2008-06-19
So I tried to download compiz-git from this thread:

[http://ubuntuforums.org/showthread.php?t=781218](http://ubuntuforums.org/showthread.php?t=781218)

and screwed up my compiz pretty bad.

So I tried the suggestions for unloading and starting over. Including the lengthy sudo rm series from page 2. 

Afterwords I still have icons in my system>preferences for Compizconfig settings manager and emerald settings. They give and error message when I click them stating failed to start child process, there is no such file etc. I tried reloading compiz and all the accoutrement from synaptic package manager, but the old icons remained. When clicked they did nothing. I tried un-selecting them in synaptic pkgmngr and applying, but I still have a light blue compiz file (directory) in my home,,that will not let me delete it.

So...how can I completely wipe out compiz et al so I can reinstall from scratch?  I needs my cube yo...

still pretty noob at the file hunting and working with w/links etc, so please reply as if you are talking to an idiot...because you are.

---

### Post by SteveNorman on 2008-06-19
I also tried this:

wget [http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz](http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz)
tar xzf compiz-git-newest.tar.gz
cd compiz-git
sudo ./compiz-git uninstall

still have icons and things in the menu under systems>pref,,how do I get rid of those links?

thank you

---

### Post by SteveNorman on 2008-06-19
so I found where the icon lives and removed it. I reloaded compiz,,and it says Advanced desktop settings now,,however it does nothing when I click it.
If I type compiz at the prompt, the desktop resets without window borders. I know this is because windows decorations needs to be turned on,,but since I cant open the manager I cant turn it on! I end up right clicking on the desktop and turning off desktop effects to get my borders back.


How do I link the system>pref>advanced desktop effects to something useful?

---

### Post by ElSlunko on 2008-06-19
I had the exact same issue last night. Decided to try to install the updates from git and it didn't work out so well. Now I'm a total noob (look at post count) but I managed to get things back to pre-update so excuse any mistakes I make.

First I ran the clean up commands on page 2 of that thread you mentioned. I also made sure I "Complete Removal" anything leftover from compiz in Synaptic.

Then I proceeded to reinstall compiz and ccsm through Synaptic. This got CCSM back up, but the icons were gone.

Then I downloaded the latest version of ccsm from compiz-fusion.org

```
wget http://releases.compiz-fusion.org/0.7.6/ccsm-0.7.6.tar.gz
tar xzf ccsm-0.7.6.tar.gz
cd ccsm-0.7.6
sudo ./setup.py install
```

That got the icons back. There are other packages available at that address. I installed simple ccsm as well.

I'm recalling this from memory since I'm not on my Ubuntu machine (I'm at work). Hope this helps!

---

### Post by ElSlunko on 2008-06-19
Also, the script from this thread : [http://ubuntuforums.org/showthread.php?t=820802]("http://ubuntuforums.org/showthread.php?t=820802") was very useful.

---

### Post by ElSlunko on 2008-06-19
Oh and one more thing I forgot. Compiz wasn't loading on it's own during startup so I added it to System > Preferences > Sessions. The command was compiz --replace.

---

### Post by SteveNorman on 2008-06-19
thanks,,I'm not booted to ubuntu now so Ill have to try in a bit,

Did you have the issue with there still being an emerald manager and a ccsm in prefs that did nothing when clicked?

---

### Post by SteveNorman on 2008-06-19
still not working,,I must be missing something obvious
What did you put in for namr in sessions? compiz or compizconfigure management....?

---

### Post by ElSlunko on 2008-06-19
Name : Compiz
Command : compiz --replace
Comment : WHY DOESN'T THIS WORK LIKE NORMAL

As far as I know only the Command matters as far as what you name it, the rest are arbitrary labels :P.

Emerald theme manager link still exists, but I hid it with Edit Menus.

Try typing in console :```
compiz --replace
```

If your normal windows manager works and the CCSM works, the only thing left to do would be to get it to start automatically on startup, right?

---

### Post by SteveNorman on 2008-06-19
the ccsm isnt working,,thats the problem I think. It doesnt seem to be linked to anything.

I get this with compize --replace:

```
desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0193 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (shift) - Warn: No compatible text plugin loaded.
Segmentation fault

```

I smell fish...

---

### Post by ElSlunko on 2008-06-19
Try uninstalling then reinstalling it from Applications > Add/Remove. Type compiz in the search field and it should be the first item.

---

### Post by SteveNorman on 2008-06-19
no go,,I even tried the fusion icon,,Nothing happens when I click it,,

I hosed it good

---

### Post by ElSlunko on 2008-06-19
Okay let's first get rid of compiz :

```
sudo apt-get remove libcompiz* compiz* compiz compizconfig-backend-gconf compizconfig-backend-kconfig libdecoration0 compizconfig-settings-manager python-compizconfig emerald
```

Then remove all the trash

```
sudo rm -rf /etc/compiz* > /dev/null 2>&1
sudo rm -rf /etc/xdg/compiz* > /dev/null 2>&1
sudo rm -rf /home/*/.compiz* > /dev/null 2>&1
sudo rm -rf /home/*/.gconf/apps/compiz* > /dev/null 2>&1
sudo rm -rf /root/.compiz* > /dev/null 2>&1
sudo rm -rf /usr/bin/compiz* > /dev/null 2>&1
sudo rm -rf /usr/bin/bcop > /dev/null 2>&1
sudo rm -rf /usr/bin/ccsm > /dev/null 2>&1
sudo rm -rf /usr/bin/emerald* > /dev/null 2>&1
sudo rm -rf /usr/bin/fusion-icon > /dev/null 2>&1
sudo rm -rf /usr/bin/gtk-window-decorator > /dev/null 2>&1
sudo rm -rf /usr/etc/compiz* > /dev/null 2>&1
sudo rm -rf /usr/etc/gconf/schemas/compiz* > /dev/null 2>&1
sudo rm -rf /usr/include/compiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/compiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/emerald* > /dev/null 2>&1
sudo rm -rf /usr/lib/libcompiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/libdecoration* > /dev/null 2>&1
sudo rm -rf /usr/lib/libemerald* > /dev/null 2>&1
sudo rm -rf /usr/lib/libcompiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/pkgconfig/compiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/pkgconfig/emerald* > /dev/null 2>&1
sudo rm -rf /usr/lib/pkgconfig/libcompiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/pkgconfig/libdecoration* > /dev/null 2>&1
sudo rm -rf /usr/lib/pkgconfig/libemerald* > /dev/null 2>&1
sudo rm -rf /usr/share/compiz* > /dev/null 2>&1
sudo rm -rf /usr/share/bcop* > /dev/null 2>&1
sudo rm -rf /usr/share/ccsm* > /dev/null 2>&1
sudo rm -rf /usr/share/emerald* > /dev/null 2>&1
sudo rm -rf /usr/share/pkgconfig/bcop.pc > /dev/null 2>&1
sudo rm -rf /usr/local/bin/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/bin/bcop > /dev/null 2>&1
sudo rm -rf /usr/local/bin/ccsm > /dev/null 2>&1
sudo rm -rf /usr/local/bin/emerald* > /dev/null 2>&1
sudo rm -rf /usr/local/bin/fusion-icon > /dev/null 2>&1
sudo rm -rf /usr/local/bin/gtk-window-decorator > /dev/null 2>&1
sudo rm -rf /usr/local/etc/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/etc/gconf/schemas/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/include/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/emerald* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/libcompiz* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/libdecoration* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/libemerald* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/pkgconfig/emerald* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/pkgconfig/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/pkgconfig/libcompiz* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/pkgconfig/libdecoration* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/pkgconfig/libemerald* > /dev/null 2>&1
sudo rm -rf /usr/local/share/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/share/bcop* > /dev/null 2>&1
sudo rm -rf /usr/local/share/ccsm* > /dev/null 2>&1
sudo rm -rf /usr/local/share/emerald* > /dev/null 2>&1
sudo rm -rf /usr/local/share/pkgconfig/bcop.pc > /dev/null 2>&1
sudo rm /usr/local/share/locale/*/LC_MESSAGES/*compiz*.mo > /dev/null 2>&1
sudo rm /usr/share/locale-langpack/*/LC_MESSAGES/compiz* > /dev/null 2>&1
sudo rm /usr/lib/window-manager-settings/libcompiz.so > /dev/null 2>&1
sudo rm /usr/lib/window-manager-settings/libcompiz.a > /dev/null 2>&1
sudo rm /usr/lib/window-manager-settings/libcompiz.la > /dev/null 2>&1
sudo rm /usr/local/lib/python2.5/site-packages/compiz* > /dev/null 2>&1

```

Now use Synaptic to install compiz only.

Then reinstall ccsm with 

```

wget http://releases.compiz-fusion.org/0.7.6/ccsm-0.7.6.tar.gz
tar xzf ccsm-0.7.6.tar.gz
cd ccsm-0.7.6
sudo ./setup.py install

```

Finally run compiz in terminal and see if there are any errors
```
compiz --replace
```

---

### Post by SteveNorman on 2008-06-19
That was the removal procedure I tried before,,I am going to be away from the computer tonight for a bit,,hopefully I can re-run the sudo rm party when I am back tonight,,I'll post the results,,thanks for your help so far.

---

### Post by SteveNorman on 2008-06-20
when I get to replace --compiz


```
~/ccsm-0.7.6$ compiz --replace
The program 'compiz' is currently not installed.  You can install it by typing:
sudo apt-get install compiz-core
bash: compiz: command not found
steve@teampeanut-desktop:~/ccsm-0.7.6$ cd
steve@teampeanut-desktop:~$ compiz --replace
The program 'compiz' is currently not installed.  You can install it by typing:
sudo apt-get install compiz-core
bash: compiz: command not found
steve@teampeanut-desktop:~$ sudo apt-get install compiz-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-core is already the newest version.
compiz-core set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
steve@teampeanut-desktop:~$ compiz --replace
The program 'compiz' is currently not installed.  You can install it by typing:
sudo apt-get install compiz-core
bash: compiz: command not found
steve@teampeanut-desktop:~$ sudo apt-get install compiz-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

it gets redundant from here on out....In synaptic package manager all the compiz options are there and checked,,

When I removed compiz with the above post I still had icons in preferences for ccsm and emerald. I think there are links still that are not being removed, and as per my usual MO I must have found a way to screw up compiz in a way no-one else ever has! I excell at that sort of thing.

---

### Post by ElSlunko on 2008-06-20
The link for emerald still exists for me as well. There's got to be a file that you can manually edit to remove it from the panels, but I don't know what it may be.

Alternatvely, you can hide it by rightclicking anywhere on the menu and choosing "Edit Menu".

---

### Post by SteveNorman on 2008-06-20
edited menu there is no longer a ccsm option,,I re-installed via spm but now there is still no option in preferences. I added the fusion-icon to the menu,,but pressing it does nothing.

I must have created a link somewhere,,and when I download things must be getting linked to where I cant use them. Very useful..

---

### Post by ElSlunko on 2008-06-20
I meant edit menus in the Menu Bar in Panels. IE right clicking where it says <Applications><Places><System>

---

### Post by SteveNorman on 2008-06-20
thats what I did,,pretty weird i cant get back the og compiz,,wonder if a fresh install is the only way.

---

### Post by SteveNorman on 2008-06-21
```
~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0193 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 406: /usr/local/bin/compiz: not found

```


missing library?

---

### Post by Forlong on 2008-06-22
What's your current Compiz install? From the repos or compiled from git?

---

### Post by SteveNorman on 2008-06-22
The last attempt was from the repros using system>admin>spm

But it goes like this...

Upgrade to hardy,using compiz from upgrade just fine with left over plugins from one of I believe to be your posts from a long time ago. Most everything worked,,fire,water,rain,cube,etc

then I tried to use this post to add cube distortion
[http://ubuntuforums.org/showthread.php?t=781218](http://ubuntuforums.org/showthread.php?t=781218)

also after removing via the instructions I tried this

[http://ubuntuforums.org/showthread.php?t=820802](http://ubuntuforums.org/showthread.php?t=820802)

I have been hosed since,,and have tried deleting and reloading from that post and from synaptic a few times,,with my last load from synaptic and 

application>add remove

I am using the latest nvidia driver on geforce 8800

---

### Post by Forlong on 2008-06-23
Seems like you completely messed up Compiz with that first script.

**Please do not use any scripts to compile Compiz from source**

Let's try to fix this then...

0. Make sure Compiz ain't running

1. Remove Compiz completely:
```
sudo apt-get purge compiz-core && sudo apt-get autoremove
```

2. Afterwards, run this in a terminal:
```
sudo updatedb
```
That will take some time -- it updates mlocate's search index.

3. Finally run this:
```
locate compiz | grep -v /var | grep -v /home
```
and post the output here.

---

### Post by SteveNorman on 2008-06-23
out put of locate compiz | grep -v /var | grep -v /home:


```
desktop:~$ locate compiz | grep -v /var | grep -v /home
/usr/include/compiz
/usr/include/compiz/compiz-common.h
/usr/include/compiz/compiz-core.h
/usr/include/compiz/compiz-cube.h
/usr/include/compiz/compiz-plugin.h
/usr/include/compiz/compiz-scale.h
/usr/include/compiz/compiz.h
/usr/lib/pkgconfig/compiz-cube.pc
/usr/lib/pkgconfig/compiz-gconf.pc
/usr/lib/pkgconfig/compiz-scale.pc
/usr/lib/pkgconfig/compiz.pc
/usr/lib/pkgconfig/compizconfig-python.pc
/usr/lib/python2.5/site-packages/compizconfig.so
/usr/share/compiz
/usr/share/app-install/desktop/gnome-compiz-preferences.desktop
/usr/share/app-install/icons/_usr_share_gnome-compiz-manager_gnome-compiz-manager.png
/usr/share/compiz/schemas.xslt
/usr/share/doc/compiz-bcop
/usr/share/doc/compiz-dev
/usr/share/doc/compizconfig-settings-manager
/usr/share/doc/libcompizconfig0
/usr/share/doc/python-compizconfig
/usr/share/doc/compiz-bcop/AUTHORS
/usr/share/doc/compiz-bcop/NEWS.gz
/usr/share/doc/compiz-bcop/changelog.Debian.gz
/usr/share/doc/compiz-bcop/copyright
/usr/share/doc/compiz-dev/AUTHORS
/usr/share/doc/compiz-dev/NEWS.gz
/usr/share/doc/compiz-dev/README
/usr/share/doc/compiz-dev/TODO
/usr/share/doc/compiz-dev/changelog.Debian.gz
/usr/share/doc/compiz-dev/changelog.gz
/usr/share/doc/compiz-dev/copyright
/usr/share/doc/compizconfig-settings-manager/AUTHORS
/usr/share/doc/compizconfig-settings-manager/changelog.Debian.gz
/usr/share/doc/compizconfig-settings-manager/copyright
/usr/share/doc/libcompizconfig0/AUTHORS
/usr/share/doc/libcompizconfig0/NEWS.gz
/usr/share/doc/libcompizconfig0/TODO
/usr/share/doc/libcompizconfig0/changelog.Debian.gz
/usr/share/doc/libcompizconfig0/copyright
/usr/share/doc/python-compizconfig/changelog.Debian.gz
/usr/share/doc/python-compizconfig/copyright
/usr/share/pyshared-data/compizconfig-settings-manager

```

---

### Post by Forlong on 2008-06-23
OK, now run these two commands:

```
sudo rm -r /usr/include/compiz /usr/share/compiz /usr/share/doc/compiz-bcop /usr/share/doc/compiz-dev /usr/share/doc/compizconfig-settings-manager /usr/share/doc/libcompizconfig0 /usr/share/doc/python-compizconfig
```

```
sudo rm /usr/lib/pkgconfig/compiz-cube.pc /usr/lib/pkgconfig/compiz-gconf.pc /usr/lib/pkgconfig/compiz-scale.pc /usr/lib/pkgconfig/compiz.pc /usr/lib/pkgconfig/compizconfig-python.pc /usr/lib/python2.5/site-packages/compizconfig.so /usr/share/pyshared-data/compizconfig-settings-manager /usr/share/app-install/desktop/gnome-compiz-preferences.desktop /usr/share/app-install/icons/_usr_share_gnome-compiz-manager_gnome-compiz-manager.png
```

Those will delete all remaining files.

**[COLOR="Red"]Anybody else reading this: do _not_ run those commands on your machine![/COLOR]**

Afterwards run
```
sudo updatedb
```
again and then post the output of
```
locate compiz | grep -v /var
```

---

### Post by SteveNorman on 2008-06-23
I assume this was all the output,,I could not scroll any higher that where it starts:
```
/home/steve/compiz/elements/build/.libs/libelements.lai
/home/steve/compiz/elements/build/.libs/libelements.so
/home/steve/compiz/elements/build/.libs/libelements.so.0
/home/steve/compiz/elements/build/.libs/libelements.so.0.0.0
/home/steve/compiz/elements/images/autumn1.png
/home/steve/compiz/elements/images/autumn2.png
/home/steve/compiz/elements/images/bubbles1.png
/home/steve/compiz/elements/images/bubbles2.png
/home/steve/compiz/elements/images/fireflies1.svg
/home/steve/compiz/elements/images/fireflies2.svg
/home/steve/compiz/elements/images/plugin-elements.png
/home/steve/compiz/elements/images/snow1.png
/home/steve/compiz/elements/images/snow2.png
/home/steve/compiz/elements/images/stars1.png
/home/steve/compiz/freewins/.git
/home/steve/compiz/freewins/AUTHORS
/home/steve/compiz/freewins/CMakeLists.txt
/home/steve/compiz/freewins/COPYING
/home/steve/compiz/freewins/Makefile
/home/steve/compiz/freewins/action.c
/home/steve/compiz/freewins/build
/home/steve/compiz/freewins/events.c
/home/steve/compiz/freewins/freewins.c
/home/steve/compiz/freewins/freewins.h
/home/steve/compiz/freewins/freewins.xml.in
/home/steve/compiz/freewins/input.c
/home/steve/compiz/freewins/paint.c
/home/steve/compiz/freewins/plugin.info
/home/steve/compiz/freewins/util.c
/home/steve/compiz/freewins/.git/HEAD
/home/steve/compiz/freewins/.git/branches
/home/steve/compiz/freewins/.git/config
/home/steve/compiz/freewins/.git/description
/home/steve/compiz/freewins/.git/hooks
/home/steve/compiz/freewins/.git/index
/home/steve/compiz/freewins/.git/info
/home/steve/compiz/freewins/.git/logs
/home/steve/compiz/freewins/.git/objects
/home/steve/compiz/freewins/.git/refs
/home/steve/compiz/freewins/.git/hooks/applypatch-msg
/home/steve/compiz/freewins/.git/hooks/commit-msg
/home/steve/compiz/freewins/.git/hooks/post-commit
/home/steve/compiz/freewins/.git/hooks/post-receive
/home/steve/compiz/freewins/.git/hooks/post-update
/home/steve/compiz/freewins/.git/hooks/pre-applypatch
/home/steve/compiz/freewins/.git/hooks/pre-commit
/home/steve/compiz/freewins/.git/hooks/pre-rebase
/home/steve/compiz/freewins/.git/hooks/update
/home/steve/compiz/freewins/.git/info/exclude
/home/steve/compiz/freewins/.git/logs/HEAD
/home/steve/compiz/freewins/.git/logs/refs
/home/steve/compiz/freewins/.git/logs/refs/heads
/home/steve/compiz/freewins/.git/logs/refs/remotes
/home/steve/compiz/freewins/.git/logs/refs/heads/master
/home/steve/compiz/freewins/.git/logs/refs/remotes/origin
/home/steve/compiz/freewins/.git/logs/refs/remotes/origin/0.6.0
/home/steve/compiz/freewins/.git/logs/refs/remotes/origin/fw-rewrite
/home/steve/compiz/freewins/.git/logs/refs/remotes/origin/ir
/home/steve/compiz/freewins/.git/logs/refs/remotes/origin/master
/home/steve/compiz/freewins/.git/logs/refs/remotes/origin/warlock
/home/steve/compiz/freewins/.git/objects/info
/home/steve/compiz/freewins/.git/objects/pack
/home/steve/compiz/freewins/.git/objects/pack/pack-695560fd2f6615a0b150181740f2a5e65734a8b3.idx
/home/steve/compiz/freewins/.git/objects/pack/pack-695560fd2f6615a0b150181740f2a5e65734a8b3.keep
/home/steve/compiz/freewins/.git/objects/pack/pack-695560fd2f6615a0b150181740f2a5e65734a8b3.pack
/home/steve/compiz/freewins/.git/refs/heads
/home/steve/compiz/freewins/.git/refs/remotes
/home/steve/compiz/freewins/.git/refs/tags
/home/steve/compiz/freewins/.git/refs/heads/master
/home/steve/compiz/freewins/.git/refs/remotes/origin
/home/steve/compiz/freewins/.git/refs/remotes/origin/0.6.0
/home/steve/compiz/freewins/.git/refs/remotes/origin/HEAD
/home/steve/compiz/freewins/.git/refs/remotes/origin/fw-rewrite
/home/steve/compiz/freewins/.git/refs/remotes/origin/ir
/home/steve/compiz/freewins/.git/refs/remotes/origin/master
/home/steve/compiz/freewins/.git/refs/remotes/origin/warlock
/home/steve/compiz/freewins/build/.libs
/home/steve/compiz/freewins/build/action.lo
/home/steve/compiz/freewins/build/action.o
/home/steve/compiz/freewins/build/compiz-freewins.schema
/home/steve/compiz/freewins/build/events.lo
/home/steve/compiz/freewins/build/events.o
/home/steve/compiz/freewins/build/freewins.lo
/home/steve/compiz/freewins/build/freewins.o
/home/steve/compiz/freewins/build/freewins.xml
/home/steve/compiz/freewins/build/freewins_options.c
/home/steve/compiz/freewins/build/freewins_options.h
/home/steve/compiz/freewins/build/freewins_options.lo
/home/steve/compiz/freewins/build/freewins_options.o
/home/steve/compiz/freewins/build/input.lo
/home/steve/compiz/freewins/build/input.o
/home/steve/compiz/freewins/build/libfreewins.la
/home/steve/compiz/freewins/build/paint.lo
/home/steve/compiz/freewins/build/paint.o
/home/steve/compiz/freewins/build/util.lo
/home/steve/compiz/freewins/build/util.o
/home/steve/compiz/freewins/build/.libs/action.o
/home/steve/compiz/freewins/build/.libs/events.o
/home/steve/compiz/freewins/build/.libs/freewins.o
/home/steve/compiz/freewins/build/.libs/freewins_options.o
/home/steve/compiz/freewins/build/.libs/input.o
/home/steve/compiz/freewins/build/.libs/libfreewins.a
/home/steve/compiz/freewins/build/.libs/libfreewins.la
/home/steve/compiz/freewins/build/.libs/libfreewins.lai
/home/steve/compiz/freewins/build/.libs/libfreewins.so
/home/steve/compiz/freewins/build/.libs/libfreewins.so.0
/home/steve/compiz/freewins/build/.libs/libfreewins.so.0.0.0
/home/steve/compiz/freewins/build/.libs/paint.o
/home/steve/compiz/freewins/build/.libs/util.o
/home/steve/compiz/photowheel/.git
/home/steve/compiz/photowheel/Makefile
/home/steve/compiz/photowheel/build
/home/steve/compiz/photowheel/photo.c
/home/steve/compiz/photowheel/photo.xml.in
/home/steve/compiz/photowheel/plugin.info
/home/steve/compiz/photowheel/.git/HEAD
/home/steve/compiz/photowheel/.git/branches
/home/steve/compiz/photowheel/.git/config
/home/steve/compiz/photowheel/.git/description
/home/steve/compiz/photowheel/.git/hooks
/home/steve/compiz/photowheel/.git/index
/home/steve/compiz/photowheel/.git/info
/home/steve/compiz/photowheel/.git/logs
/home/steve/compiz/photowheel/.git/objects
/home/steve/compiz/photowheel/.git/refs
/home/steve/compiz/photowheel/.git/hooks/applypatch-msg
/home/steve/compiz/photowheel/.git/hooks/commit-msg
/home/steve/compiz/photowheel/.git/hooks/post-commit
/home/steve/compiz/photowheel/.git/hooks/post-receive
/home/steve/compiz/photowheel/.git/hooks/post-update
/home/steve/compiz/photowheel/.git/hooks/pre-applypatch
/home/steve/compiz/photowheel/.git/hooks/pre-commit
/home/steve/compiz/photowheel/.git/hooks/pre-rebase
/home/steve/compiz/photowheel/.git/hooks/update
/home/steve/compiz/photowheel/.git/info/exclude
/home/steve/compiz/photowheel/.git/logs/HEAD
/home/steve/compiz/photowheel/.git/logs/refs
/home/steve/compiz/photowheel/.git/logs/refs/heads
/home/steve/compiz/photowheel/.git/logs/refs/remotes
/home/steve/compiz/photowheel/.git/logs/refs/heads/master
/home/steve/compiz/photowheel/.git/logs/refs/remotes/origin
/home/steve/compiz/photowheel/.git/logs/refs/remotes/origin/0.6
/home/steve/compiz/photowheel/.git/logs/refs/remotes/origin/master
/home/steve/compiz/photowheel/.git/objects/info
/home/steve/compiz/photowheel/.git/objects/pack
/home/steve/compiz/photowheel/.git/objects/pack/pack-70f06a9661c0daadce13b54736026538b74142d6.idx
/home/steve/compiz/photowheel/.git/objects/pack/pack-70f06a9661c0daadce13b54736026538b74142d6.keep
/home/steve/compiz/photowheel/.git/objects/pack/pack-70f06a9661c0daadce13b54736026538b74142d6.pack
/home/steve/compiz/photowheel/.git/refs/heads
/home/steve/compiz/photowheel/.git/refs/remotes
/home/steve/compiz/photowheel/.git/refs/tags
/home/steve/compiz/photowheel/.git/refs/heads/master
/home/steve/compiz/photowheel/.git/refs/remotes/origin
/home/steve/compiz/photowheel/.git/refs/remotes/origin/0.6
/home/steve/compiz/photowheel/.git/refs/remotes/origin/HEAD
/home/steve/compiz/photowheel/.git/refs/remotes/origin/master
/home/steve/compiz/photowheel/build/.libs
/home/steve/compiz/photowheel/build/compiz-photo.schema
/home/steve/compiz/photowheel/build/libphoto.la
/home/steve/compiz/photowheel/build/photo.lo
/home/steve/compiz/photowheel/build/photo.o
/home/steve/compiz/photowheel/build/photo.xml
/home/steve/compiz/photowheel/build/photo_options.c
/home/steve/compiz/photowheel/build/photo_options.h
/home/steve/compiz/photowheel/build/photo_options.lo
/home/steve/compiz/photowheel/build/photo_options.o
/home/steve/compiz/photowheel/build/.libs/libphoto.a
/home/steve/compiz/photowheel/build/.libs/libphoto.la
/home/steve/compiz/photowheel/build/.libs/libphoto.lai
/home/steve/compiz/photowheel/build/.libs/libphoto.so
/home/steve/compiz/photowheel/build/.libs/libphoto.so.0
/home/steve/compiz/photowheel/build/.libs/libphoto.so.0.0.0
/home/steve/compiz/photowheel/build/.libs/photo.o
/home/steve/compiz/photowheel/build/.libs/photo_options.o
/home/steve/compiz/screensaver/.git
/home/steve/compiz/screensaver/CMakeLists.txt
/home/steve/compiz/screensaver/Makefile
/home/steve/compiz/screensaver/README
/home/steve/compiz/screensaver/build
/home/steve/compiz/screensaver/effect.cpp
/home/steve/compiz/screensaver/effect.h
/home/steve/compiz/screensaver/flyingwindows.cpp
/home/steve/compiz/screensaver/flyingwindows.h
/home/steve/compiz/screensaver/matrix.cpp
/home/steve/compiz/screensaver/matrix.h
/home/steve/compiz/screensaver/plugin.info
/home/steve/compiz/screensaver/rotatingcube.cpp
/home/steve/compiz/screensaver/rotatingcube.h
/home/steve/compiz/screensaver/screensaver.cpp
/home/steve/compiz/screensaver/screensaver.xml.in
/home/steve/compiz/screensaver/screensaver_internal.h
/home/steve/compiz/screensaver/vector.cpp
/home/steve/compiz/screensaver/vector.h
/home/steve/compiz/screensaver/wrapper.cpp
/home/steve/compiz/screensaver/wrapper.h
/home/steve/compiz/screensaver/.git/HEAD
/home/steve/compiz/screensaver/.git/branches
/home/steve/compiz/screensaver/.git/config
/home/steve/compiz/screensaver/.git/description
/home/steve/compiz/screensaver/.git/hooks
/home/steve/compiz/screensaver/.git/index
/home/steve/compiz/screensaver/.git/info
/home/steve/compiz/screensaver/.git/logs
/home/steve/compiz/screensaver/.git/objects
/home/steve/compiz/screensaver/.git/refs
/home/steve/compiz/screensaver/.git/hooks/applypatch-msg
/home/steve/compiz/screensaver/.git/hooks/commit-msg
/home/steve/compiz/screensaver/.git/hooks/post-commit
/home/steve/compiz/screensaver/.git/hooks/post-receive
/home/steve/compiz/screensaver/.git/hooks/post-update
/home/steve/compiz/screensaver/.git/hooks/pre-applypatch
/home/steve/compiz/screensaver/.git/hooks/pre-commit
/home/steve/compiz/screensaver/.git/hooks/pre-rebase
/home/steve/compiz/screensaver/.git/hooks/update
/home/steve/compiz/screensaver/.git/info/exclude
/home/steve/compiz/screensaver/.git/logs/HEAD
/home/steve/compiz/screensaver/.git/logs/refs
/home/steve/compiz/screensaver/.git/logs/refs/heads
/home/steve/compiz/screensaver/.git/logs/refs/remotes
/home/steve/compiz/screensaver/.git/logs/refs/heads/master
/home/steve/compiz/screensaver/.git/logs/refs/remotes/origin
/home/steve/compiz/screensaver/.git/logs/refs/remotes/origin/master
/home/steve/compiz/screensaver/.git/objects/info
/home/steve/compiz/screensaver/.git/objects/pack
/home/steve/compiz/screensaver/.git/objects/pack/pack-6edb0ddafe6ef7def655db04b8554c235391457c.idx
/home/steve/compiz/screensaver/.git/objects/pack/pack-6edb0ddafe6ef7def655db04b8554c235391457c.keep
/home/steve/compiz/screensaver/.git/objects/pack/pack-6edb0ddafe6ef7def655db04b8554c235391457c.pack
/home/steve/compiz/screensaver/.git/refs/heads
/home/steve/compiz/screensaver/.git/refs/remotes
/home/steve/compiz/screensaver/.git/refs/tags
/home/steve/compiz/screensaver/.git/refs/heads/master
/home/steve/compiz/screensaver/.git/refs/remotes/origin
/home/steve/compiz/screensaver/.git/refs/remotes/origin/HEAD
/home/steve/compiz/screensaver/.git/refs/remotes/origin/master
/home/steve/compiz/screensaver/build/.libs
/home/steve/compiz/screensaver/build/compiz-screensaver.schema
/home/steve/compiz/screensaver/build/effect.lo
/home/steve/compiz/screensaver/build/effect.o
/home/steve/compiz/screensaver/build/flyingwindows.lo
/home/steve/compiz/screensaver/build/flyingwindows.o
/home/steve/compiz/screensaver/build/libscreensaver.la
/home/steve/compiz/screensaver/build/matrix.lo
/home/steve/compiz/screensaver/build/matrix.o
/home/steve/compiz/screensaver/build/rotatingcube.lo
/home/steve/compiz/screensaver/build/rotatingcube.o
/home/steve/compiz/screensaver/build/screensaver.lo
/home/steve/compiz/screensaver/build/screensaver.o
/home/steve/compiz/screensaver/build/screensaver.xml
/home/steve/compiz/screensaver/build/screensaver_options.c
/home/steve/compiz/screensaver/build/screensaver_options.h
/home/steve/compiz/screensaver/build/screensaver_options.lo
/home/steve/compiz/screensaver/build/screensaver_options.o
/home/steve/compiz/screensaver/build/vector.lo
/home/steve/compiz/screensaver/build/vector.o
/home/steve/compiz/screensaver/build/wrapper.lo
/home/steve/compiz/screensaver/build/wrapper.o
/home/steve/compiz/screensaver/build/.libs/effect.o
/home/steve/compiz/screensaver/build/.libs/flyingwindows.o
/home/steve/compiz/screensaver/build/.libs/libscreensaver.a
/home/steve/compiz/screensaver/build/.libs/libscreensaver.la
/home/steve/compiz/screensaver/build/.libs/libscreensaver.lai
/home/steve/compiz/screensaver/build/.libs/libscreensaver.so
/home/steve/compiz/screensaver/build/.libs/libscreensaver.so.0
/home/steve/compiz/screensaver/build/.libs/libscreensaver.so.0.0.0
/home/steve/compiz/screensaver/build/.libs/matrix.o
/home/steve/compiz/screensaver/build/.libs/rotatingcube.o
/home/steve/compiz/screensaver/build/.libs/screensaver.o
/home/steve/compiz/screensaver/build/.libs/screensaver_options.o
/home/steve/compiz/screensaver/build/.libs/vector.o
/home/steve/compiz/screensaver/build/.libs/wrapper.o
/home/steve/compiz/snowglobe/.git
/home/steve/compiz/snowglobe/Makefile
/home/steve/compiz/snowglobe/build
/home/steve/compiz/snowglobe/movement.c
/home/steve/compiz/snowglobe/plugin.info
/home/steve/compiz/snowglobe/snowflake.c
/home/steve/compiz/snowglobe/snowglobe-internal.h
/home/steve/compiz/snowglobe/snowglobe.c
/home/steve/compiz/snowglobe/snowglobe.xml.in
/home/steve/compiz/snowglobe/snowman.c
/home/steve/compiz/snowglobe/water.c
/home/steve/compiz/snowglobe/.git/HEAD
/home/steve/compiz/snowglobe/.git/branches
/home/steve/compiz/snowglobe/.git/config
/home/steve/compiz/snowglobe/.git/description
/home/steve/compiz/snowglobe/.git/hooks
/home/steve/compiz/snowglobe/.git/index
/home/steve/compiz/snowglobe/.git/info
/home/steve/compiz/snowglobe/.git/logs
/home/steve/compiz/snowglobe/.git/objects
/home/steve/compiz/snowglobe/.git/refs
/home/steve/compiz/snowglobe/.git/hooks/applypatch-msg
/home/steve/compiz/snowglobe/.git/hooks/commit-msg
/home/steve/compiz/snowglobe/.git/hooks/post-commit
/home/steve/compiz/snowglobe/.git/hooks/post-receive
/home/steve/compiz/snowglobe/.git/hooks/post-update
/home/steve/compiz/snowglobe/.git/hooks/pre-applypatch
/home/steve/compiz/snowglobe/.git/hooks/pre-commit
/home/steve/compiz/snowglobe/.git/hooks/pre-rebase
/home/steve/compiz/snowglobe/.git/hooks/update
/home/steve/compiz/snowglobe/.git/info/exclude
/home/steve/compiz/snowglobe/.git/logs/HEAD
/home/steve/compiz/snowglobe/.git/logs/refs
/home/steve/compiz/snowglobe/.git/logs/refs/heads
/home/steve/compiz/snowglobe/.git/logs/refs/remotes
/home/steve/compiz/snowglobe/.git/logs/refs/heads/master
/home/steve/compiz/snowglobe/.git/logs/refs/remotes/origin
/home/steve/compiz/snowglobe/.git/logs/refs/remotes/origin/0.6.0
/home/steve/compiz/snowglobe/.git/logs/refs/remotes/origin/master
/home/steve/compiz/snowglobe/.git/objects/info
/home/steve/compiz/snowglobe/.git/objects/pack
/home/steve/compiz/snowglobe/.git/objects/pack/pack-6897d4a55d41c720c1e4e0e991549e9c77c3f493.idx
/home/steve/compiz/snowglobe/.git/objects/pack/pack-6897d4a55d41c720c1e4e0e991549e9c77c3f493.keep
/home/steve/compiz/snowglobe/.git/objects/pack/pack-6897d4a55d41c720c1e4e0e991549e9c77c3f493.pack
/home/steve/compiz/snowglobe/.git/refs/heads
/home/steve/compiz/snowglobe/.git/refs/remotes
/home/steve/compiz/snowglobe/.git/refs/tags
/home/steve/compiz/snowglobe/.git/refs/heads/master
/home/steve/compiz/snowglobe/.git/refs/remotes/origin
/home/steve/compiz/snowglobe/.git/refs/remotes/origin/0.6.0
/home/steve/compiz/snowglobe/.git/refs/remotes/origin/HEAD
/home/steve/compiz/snowglobe/.git/refs/remotes/origin/master
/home/steve/compiz/snowglobe/build/.libs
/home/steve/compiz/snowglobe/build/compiz-snowglobe.schema
/home/steve/compiz/snowglobe/build/libsnowglobe.la
/home/steve/compiz/snowglobe/build/movement.lo
/home/steve/compiz/snowglobe/build/movement.o
/home/steve/compiz/snowglobe/build/snowflake.lo
/home/steve/compiz/snowglobe/build/snowflake.o
/home/steve/compiz/snowglobe/build/snowglobe.lo
/home/steve/compiz/snowglobe/build/snowglobe.o
/home/steve/compiz/snowglobe/build/snowglobe.xml
/home/steve/compiz/snowglobe/build/snowglobe_options.c
/home/steve/compiz/snowglobe/build/snowglobe_options.h
/home/steve/compiz/snowglobe/build/snowglobe_options.lo
/home/steve/compiz/snowglobe/build/snowglobe_options.o
/home/steve/compiz/snowglobe/build/snowman.lo
/home/steve/compiz/snowglobe/build/snowman.o
/home/steve/compiz/snowglobe/build/water.lo
/home/steve/compiz/snowglobe/build/water.o
/home/steve/compiz/snowglobe/build/.libs/libsnowglobe.a
/home/steve/compiz/snowglobe/build/.libs/libsnowglobe.la
/home/steve/compiz/snowglobe/build/.libs/libsnowglobe.lai
/home/steve/compiz/snowglobe/build/.libs/libsnowglobe.so
/home/steve/compiz/snowglobe/build/.libs/libsnowglobe.so.0
/home/steve/compiz/snowglobe/build/.libs/libsnowglobe.so.0.0.0
/home/steve/compiz/snowglobe/build/.libs/movement.o
/home/steve/compiz/snowglobe/build/.libs/snowflake.o
/home/steve/compiz/snowglobe/build/.libs/snowglobe.o
/home/steve/compiz/snowglobe/build/.libs/snowglobe_options.o
/home/steve/compiz/snowglobe/build/.libs/snowman.o
/home/steve/compiz/snowglobe/build/.libs/water.o
/home/steve/compiz/tile/.git
/home/steve/compiz/tile/CMakeLists.txt
/home/steve/compiz/tile/Makefile
/home/steve/compiz/tile/build
/home/steve/compiz/tile/plugin.info
/home/steve/compiz/tile/tile.c
/home/steve/compiz/tile/tile.xml.in
/home/steve/compiz/tile/.git/HEAD
/home/steve/compiz/tile/.git/branches
/home/steve/compiz/tile/.git/config
/home/steve/compiz/tile/.git/description
/home/steve/compiz/tile/.git/hooks
/home/steve/compiz/tile/.git/index
/home/steve/compiz/tile/.git/info
/home/steve/compiz/tile/.git/logs
/home/steve/compiz/tile/.git/objects
/home/steve/compiz/tile/.git/refs
/home/steve/compiz/tile/.git/hooks/applypatch-msg
/home/steve/compiz/tile/.git/hooks/commit-msg
/home/steve/compiz/tile/.git/hooks/post-commit
/home/steve/compiz/tile/.git/hooks/post-receive
/home/steve/compiz/tile/.git/hooks/post-update
/home/steve/compiz/tile/.git/hooks/pre-applypatch
/home/steve/compiz/tile/.git/hooks/pre-commit
/home/steve/compiz/tile/.git/hooks/pre-rebase
/home/steve/compiz/tile/.git/hooks/update
/home/steve/compiz/tile/.git/info/exclude
/home/steve/compiz/tile/.git/logs/HEAD
/home/steve/compiz/tile/.git/logs/refs
/home/steve/compiz/tile/.git/logs/refs/heads
/home/steve/compiz/tile/.git/logs/refs/remotes
/home/steve/compiz/tile/.git/logs/refs/heads/master
/home/steve/compiz/tile/.git/logs/refs/remotes/origin
/home/steve/compiz/tile/.git/logs/refs/remotes/origin/master
/home/steve/compiz/tile/.git/objects/info
/home/steve/compiz/tile/.git/objects/pack
/home/steve/compiz/tile/.git/objects/pack/pack-aa8562bf99bcfa423231379900137fc0a99d9d7c.idx
/home/steve/compiz/tile/.git/objects/pack/pack-aa8562bf99bcfa423231379900137fc0a99d9d7c.keep
/home/steve/compiz/tile/.git/objects/pack/pack-aa8562bf99bcfa423231379900137fc0a99d9d7c.pack
/home/steve/compiz/tile/.git/refs/heads
/home/steve/compiz/tile/.git/refs/remotes
/home/steve/compiz/tile/.git/refs/tags
/home/steve/compiz/tile/.git/refs/heads/master
/home/steve/compiz/tile/.git/refs/remotes/origin
/home/steve/compiz/tile/.git/refs/remotes/origin/HEAD
/home/steve/compiz/tile/.git/refs/remotes/origin/master
/home/steve/compiz/tile/build/.libs
/home/steve/compiz/tile/build/compiz-tile.schema
/home/steve/compiz/tile/build/libtile.la
/home/steve/compiz/tile/build/tile.lo
/home/steve/compiz/tile/build/tile.o
/home/steve/compiz/tile/build/tile.xml
/home/steve/compiz/tile/build/tile_options.c
/home/steve/compiz/tile/build/tile_options.h
/home/steve/compiz/tile/build/tile_options.lo
/home/steve/compiz/tile/build/tile_options.o
/home/steve/compiz/tile/build/.libs/libtile.a
/home/steve/compiz/tile/build/.libs/libtile.la
/home/steve/compiz/tile/build/.libs/libtile.lai
/home/steve/compiz/tile/build/.libs/libtile.so
/home/steve/compiz/tile/build/.libs/libtile.so.0
/home/steve/compiz/tile/build/.libs/libtile.so.0.0.0
/home/steve/compiz/tile/build/.libs/tile.o
/home/steve/compiz/tile/build/.libs/tile_options.o
/home/steve/compiz/wallpaper/.git
/home/steve/compiz/wallpaper/CMakeLists.txt
/home/steve/compiz/wallpaper/Makefile
/home/steve/compiz/wallpaper/build
/home/steve/compiz/wallpaper/plugin.info
/home/steve/compiz/wallpaper/wallpaper.c
/home/steve/compiz/wallpaper/wallpaper.xml.in
/home/steve/compiz/wallpaper/.git/HEAD
/home/steve/compiz/wallpaper/.git/branches
/home/steve/compiz/wallpaper/.git/config
/home/steve/compiz/wallpaper/.git/description
/home/steve/compiz/wallpaper/.git/hooks
/home/steve/compiz/wallpaper/.git/index
/home/steve/compiz/wallpaper/.git/info
/home/steve/compiz/wallpaper/.git/logs
/home/steve/compiz/wallpaper/.git/objects
/home/steve/compiz/wallpaper/.git/refs
/home/steve/compiz/wallpaper/.git/hooks/applypatch-msg
/home/steve/compiz/wallpaper/.git/hooks/commit-msg
/home/steve/compiz/wallpaper/.git/hooks/post-commit
/home/steve/compiz/wallpaper/.git/hooks/post-receive
/home/steve/compiz/wallpaper/.git/hooks/post-update
/home/steve/compiz/wallpaper/.git/hooks/pre-applypatch
/home/steve/compiz/wallpaper/.git/hooks/pre-commit
/home/steve/compiz/wallpaper/.git/hooks/pre-rebase
/home/steve/compiz/wallpaper/.git/hooks/update
/home/steve/compiz/wallpaper/.git/info/exclude
/home/steve/compiz/wallpaper/.git/logs/HEAD
/home/steve/compiz/wallpaper/.git/logs/refs
/home/steve/compiz/wallpaper/.git/logs/refs/heads
/home/steve/compiz/wallpaper/.git/logs/refs/remotes
/home/steve/compiz/wallpaper/.git/logs/refs/heads/master
/home/steve/compiz/wallpaper/.git/logs/refs/remotes/origin
/home/steve/compiz/wallpaper/.git/logs/refs/remotes/origin/master
/home/steve/compiz/wallpaper/.git/objects/info
/home/steve/compiz/wallpaper/.git/objects/pack
/home/steve/compiz/wallpaper/.git/objects/pack/pack-04abaaf4dc73af893248d49d82edea3209277c10.idx
/home/steve/compiz/wallpaper/.git/objects/pack/pack-04abaaf4dc73af893248d49d82edea3209277c10.keep
/home/steve/compiz/wallpaper/.git/objects/pack/pack-04abaaf4dc73af893248d49d82edea3209277c10.pack
/home/steve/compiz/wallpaper/.git/refs/heads
/home/steve/compiz/wallpaper/.git/refs/remotes
/home/steve/compiz/wallpaper/.git/refs/tags
/home/steve/compiz/wallpaper/.git/refs/heads/master
/home/steve/compiz/wallpaper/.git/refs/remotes/origin
/home/steve/compiz/wallpaper/.git/refs/remotes/origin/HEAD
/home/steve/compiz/wallpaper/.git/refs/remotes/origin/master
/home/steve/compiz/wallpaper/build/.libs
/home/steve/compiz/wallpaper/build/compiz-wallpaper.schema
/home/steve/compiz/wallpaper/build/libwallpaper.la
/home/steve/compiz/wallpaper/build/wallpaper.lo
/home/steve/compiz/wallpaper/build/wallpaper.o
/home/steve/compiz/wallpaper/build/wallpaper.xml
/home/steve/compiz/wallpaper/build/wallpaper_options.c
/home/steve/compiz/wallpaper/build/wallpaper_options.h
/home/steve/compiz/wallpaper/build/wallpaper_options.lo
/home/steve/compiz/wallpaper/build/wallpaper_options.o
/home/steve/compiz/wallpaper/build/.libs/libwallpaper.a
/home/steve/compiz/wallpaper/build/.libs/libwallpaper.la
/home/steve/compiz/wallpaper/build/.libs/libwallpaper.lai
/home/steve/compiz/wallpaper/build/.libs/libwallpaper.so
/home/steve/compiz/wallpaper/build/.libs/libwallpaper.so.0
/home/steve/compiz/wallpaper/build/.libs/libwallpaper.so.0.0.0
/home/steve/compiz/wallpaper/build/.libs/wallpaper.o
/home/steve/compiz/wallpaper/build/.libs/wallpaper_options.o

```

---

### Post by Forlong on 2008-06-23
Oh, use this instead:
```
locate compiz | grep -v /var | grep -v /home/steve/compiz
```

---

### Post by SteveNorman on 2008-06-23
```
-desktop:~$ locate compiz | grep -v /var | grep -v /home/steve/compiz
/home/steve/.compiz
/home/steve/.compiz/images
/home/steve/.compiz/metadata
/home/steve/.compiz/plugins
/home/steve/.compiz/images/autumn1.png
/home/steve/.compiz/images/autumn2.png
/home/steve/.compiz/images/bubbles1.png
/home/steve/.compiz/images/bubbles2.png
/home/steve/.compiz/images/fireflies1.svg
/home/steve/.compiz/images/fireflies2.svg
/home/steve/.compiz/images/plugin-elements.png
/home/steve/.compiz/images/snow1.png
/home/steve/.compiz/images/snow2.png
/home/steve/.compiz/images/stars1.png
/home/steve/.compiz/metadata/anaglyph.xml
/home/steve/.compiz/metadata/atlantis.xml
/home/steve/.compiz/metadata/elements.xml
/home/steve/.compiz/metadata/freewins.xml
/home/steve/.compiz/metadata/photo.xml
/home/steve/.compiz/metadata/screensaver.xml
/home/steve/.compiz/metadata/snowglobe.xml
/home/steve/.compiz/metadata/tile.xml
/home/steve/.compiz/metadata/wallpaper.xml
/home/steve/.compiz/plugins/libanaglyph.so
/home/steve/.compiz/plugins/libatlantis.so
/home/steve/.compiz/plugins/libelements.so
/home/steve/.compiz/plugins/libfreewins.so
/home/steve/.compiz/plugins/libphoto.so
/home/steve/.compiz/plugins/libscreensaver.so
/home/steve/.compiz/plugins/libsnowglobe.so
/home/steve/.compiz/plugins/libtile.so
/home/steve/.compiz/plugins/libwallpaper.so
/home/steve/.config/compiz
/home/steve/.config/compiz/compizconfig
/home/steve/.config/compiz/fusion-icon
/home/steve/.config/compiz/compizconfig/Default.ini
/home/steve/.config/compiz/compizconfig/config
/home/steve/.gconf/apps/compiz
/home/steve/.gconf/apps/compiz/%gconf.xml
/home/steve/.gconf/apps/compiz/general
/home/steve/.gconf/apps/compiz/plugins
/home/steve/.gconf/apps/compiz/general/%gconf.xml
/home/steve/.gconf/apps/compiz/general/allscreens
/home/steve/.gconf/apps/compiz/general/allscreens/%gconf.xml
/home/steve/.gconf/apps/compiz/general/allscreens/options
/home/steve/.gconf/apps/compiz/general/allscreens/options/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/anaglyph
/home/steve/.gconf/apps/compiz/plugins/atlantis
/home/steve/.gconf/apps/compiz/plugins/elements
/home/steve/.gconf/apps/compiz/plugins/freewins
/home/steve/.gconf/apps/compiz/plugins/photo
/home/steve/.gconf/apps/compiz/plugins/screensaver
/home/steve/.gconf/apps/compiz/plugins/snowglobe
/home/steve/.gconf/apps/compiz/plugins/tile
/home/steve/.gconf/apps/compiz/plugins/wallpaper
/home/steve/.gconf/apps/compiz/plugins/anaglyph/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/anaglyph/allscreens
/home/steve/.gconf/apps/compiz/plugins/anaglyph/screen0
/home/steve/.gconf/apps/compiz/plugins/anaglyph/allscreens/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/anaglyph/allscreens/options
/home/steve/.gconf/apps/compiz/plugins/anaglyph/allscreens/options/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/anaglyph/screen0/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/anaglyph/screen0/options
/home/steve/.gconf/apps/compiz/plugins/anaglyph/screen0/options/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/atlantis/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/atlantis/screen0
/home/steve/.gconf/apps/compiz/plugins/atlantis/screen0/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/atlantis/screen0/options
/home/steve/.gconf/apps/compiz/plugins/atlantis/screen0/options/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/elements/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/elements/allscreens
/home/steve/.gconf/apps/compiz/plugins/elements/allscreens/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/elements/allscreens/options
/home/steve/.gconf/apps/compiz/plugins/elements/allscreens/options/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/freewins/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/freewins/allscreens
/home/steve/.gconf/apps/compiz/plugins/freewins/screen0
/home/steve/.gconf/apps/compiz/plugins/freewins/allscreens/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/freewins/allscreens/options
/home/steve/.gconf/apps/compiz/plugins/freewins/allscreens/options/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/freewins/screen0/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/freewins/screen0/options
/home/steve/.gconf/apps/compiz/plugins/freewins/screen0/options/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/photo/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/photo/screen0
/home/steve/.gconf/apps/compiz/plugins/photo/screen0/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/photo/screen0/options
/home/steve/.gconf/apps/compiz/plugins/photo/screen0/options/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/screensaver/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/screensaver/allscreens
/home/steve/.gconf/apps/compiz/plugins/screensaver/allscreens/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/screensaver/allscreens/options
/home/steve/.gconf/apps/compiz/plugins/screensaver/allscreens/options/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/snowglobe/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/snowglobe/screen0
/home/steve/.gconf/apps/compiz/plugins/snowglobe/screen0/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/snowglobe/screen0/options
/home/steve/.gconf/apps/compiz/plugins/snowglobe/screen0/options/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/tile/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/tile/allscreens
/home/steve/.gconf/apps/compiz/plugins/tile/allscreens/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/tile/allscreens/options
/home/steve/.gconf/apps/compiz/plugins/tile/allscreens/options/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/wallpaper/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/wallpaper/screen0
/home/steve/.gconf/apps/compiz/plugins/wallpaper/screen0/%gconf.xml
/home/steve/.gconf/apps/compiz/plugins/wallpaper/screen0/options
/home/steve/.gconf/apps/compiz/plugins/wallpaper/screen0/options/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz
/home/steve/.gconf/schemas/apps/compiz/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins
/home/steve/.gconf/schemas/apps/compiz/plugins/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/anaglyph
/home/steve/.gconf/schemas/apps/compiz/plugins/atlantis
/home/steve/.gconf/schemas/apps/compiz/plugins/elements
/home/steve/.gconf/schemas/apps/compiz/plugins/freewins
/home/steve/.gconf/schemas/apps/compiz/plugins/photo
/home/steve/.gconf/schemas/apps/compiz/plugins/screensaver
/home/steve/.gconf/schemas/apps/compiz/plugins/snowglobe
/home/steve/.gconf/schemas/apps/compiz/plugins/tile
/home/steve/.gconf/schemas/apps/compiz/plugins/wallpaper
/home/steve/.gconf/schemas/apps/compiz/plugins/anaglyph/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/anaglyph/allscreens
/home/steve/.gconf/schemas/apps/compiz/plugins/anaglyph/screen0
/home/steve/.gconf/schemas/apps/compiz/plugins/anaglyph/allscreens/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/anaglyph/allscreens/options
/home/steve/.gconf/schemas/apps/compiz/plugins/anaglyph/allscreens/options/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/anaglyph/screen0/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/anaglyph/screen0/options
/home/steve/.gconf/schemas/apps/compiz/plugins/anaglyph/screen0/options/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/atlantis/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/atlantis/screen0
/home/steve/.gconf/schemas/apps/compiz/plugins/atlantis/screen0/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/atlantis/screen0/options
/home/steve/.gconf/schemas/apps/compiz/plugins/atlantis/screen0/options/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/elements/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/elements/allscreens
/home/steve/.gconf/schemas/apps/compiz/plugins/elements/allscreens/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/elements/allscreens/options
/home/steve/.gconf/schemas/apps/compiz/plugins/elements/allscreens/options/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/freewins/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/freewins/allscreens
/home/steve/.gconf/schemas/apps/compiz/plugins/freewins/screen0
/home/steve/.gconf/schemas/apps/compiz/plugins/freewins/allscreens/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/freewins/allscreens/options
/home/steve/.gconf/schemas/apps/compiz/plugins/freewins/allscreens/options/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/freewins/screen0/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/freewins/screen0/options
/home/steve/.gconf/schemas/apps/compiz/plugins/freewins/screen0/options/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/photo/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/photo/screen0
/home/steve/.gconf/schemas/apps/compiz/plugins/photo/screen0/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/photo/screen0/options
/home/steve/.gconf/schemas/apps/compiz/plugins/photo/screen0/options/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/screensaver/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/screensaver/allscreens
/home/steve/.gconf/schemas/apps/compiz/plugins/screensaver/allscreens/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/screensaver/allscreens/options
/home/steve/.gconf/schemas/apps/compiz/plugins/screensaver/allscreens/options/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/snowglobe/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/snowglobe/screen0
/home/steve/.gconf/schemas/apps/compiz/plugins/snowglobe/screen0/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/snowglobe/screen0/options
/home/steve/.gconf/schemas/apps/compiz/plugins/snowglobe/screen0/options/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/tile/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/tile/allscreens
/home/steve/.gconf/schemas/apps/compiz/plugins/tile/allscreens/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/tile/allscreens/options
/home/steve/.gconf/schemas/apps/compiz/plugins/tile/allscreens/options/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/wallpaper/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/wallpaper/screen0
/home/steve/.gconf/schemas/apps/compiz/plugins/wallpaper/screen0/%gconf.xml
/home/steve/.gconf/schemas/apps/compiz/plugins/wallpaper/screen0/options
/home/steve/.gconf/schemas/apps/compiz/plugins/wallpaper/screen0/options/%gconf.xml
/home/steve/.themes/LUX/LUX_compiz.profile
/home/steve/Desktop/randomcrap/compizplugins4.sh
/home/steve/Desktop/randomcrap/LUX/LUX_compiz.profile

```

---

### Post by SteveNorman on 2008-06-23
Forlong I have to go to work and wont be on the forum for a bit,,Thank you for your help so far!

I will be back in a few hours hopefully..

---

### Post by Forlong on 2008-06-23
Alright, I was away for a few hours too :)

So now let's delete those as well:
```
rm -r /home/steve/.compiz
```
You shouldn't need sudo to do that. Please report back if you encounter any problems.

Additionally, you might want to delete thos as well:
```
rm -r /home/steve/.gconf/apps/compiz /home/steve/.gconf/schemas/apps/compiz /home/steve/.config/compiz
```
But this will delete all your previous configurations for Compiz.

Afterwards **reboot** and install Compiz like this:
```
sudo apt-get install compiz
```
You want most probably ccsm as well:
```
sudo apt-get install compizconfig-settings-manager
```
And in case you want to use Emerald:
```
sudo apt-get install emerald
```

Finally run this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)
And if everything's OK, enable Compiz via *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects*


I'm keeping my fingers crossed. :)

---

### Post by SteveNorman on 2008-06-23
I am up to the re-install portion now,,but before I start to load I still have the fusion icon and advanced desktop settings (ccsm manager) checked as installed in applications>add-remove


Should I mark them for removal or just ignore them?

---

### Post by SteveNorman on 2008-06-23
I went ahead and re-installed via your last post. Same effect,,there is no option for ccsm or emerald,,

when I do pref>appearance> visual effects>extra  the screen resets and asks me if I want to keep the settings. 

The problem is I cant find a way to enter ccsm to enable anything

There is still a compiz fusion icon on my tool bar (I know thats not the right term for it), but it does nothing when clicked.

Thats what made me think there is a weird link floating around from the script

---

### Post by Forlong on 2008-06-24
> **SteveNorman said:**
> when I do pref>appearance> visual effects>extra  the screen resets and asks me if I want to keep the settings.
Great, that means, Compiz is running.
> **SteveNorman said:**
> The problem is I cant find a way to enter ccsm to enable anything
What' the output when running ```
ccsm
``` in a terminal?

---

### Post by SteveNorman on 2008-06-24
t-desktop:~$ ccsm
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: No module named compizconfig

---

### Post by Forlong on 2008-06-24
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by SteveNorman on 2008-06-24
deleted due to incompetence

---

### Post by SteveNorman on 2008-06-24
sorry

```
desktop:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.7.4-0ubuntu7                                   OpenGL window and compositing manager
ii  compiz-bcop                                0.7.4-0ubuntu1                                     Compiz option code generator
ii  compiz-core                                1:0.7.4-0ubuntu7                                   OpenGL window and compositing manager
ii  compiz-dev                                 1:0.7.4-0ubuntu7                                   OpenGL window and compositing manager - development
ii  compiz-fusion-plugins-extra                0.7.4-0ubuntu1                                     Collection of extra plugins from OpenCompositing fo
ii  compiz-fusion-plugins-main                 0.7.4-0ubuntu5                                     Collection of plugins from OpenCompositing for Comp
ii  compiz-gnome                               1:0.7.4-0ubuntu7                                   OpenGL window and compositing manager - GNOME windo
ii  compiz-plugins                             1:0.7.4-0ubuntu7                                   OpenGL window and compositing manager - plugins
ii  compizconfig-backend-gconf                 0.7.4-0ubuntu1                                     Settings library for plugins - OpenCompositing Proj
ii  compizconfig-settings-manager              0.7.4-0ubuntu2                                     Compiz configuration settings manager
ii  emerald                                    0.7.2-0ubuntu2                                     Decorator for compiz-fusion
rc  gnome-compiz-manager                       0.10.3-0ubuntu2                                    Compiz Gnome Manager
ii  libcompizconfig0                           0.7.4-0ubuntu1                                     Settings library for plugins - OpenCompositing Proj
ii  libemeraldengine0                          0.7.2-0ubuntu2                                     Decoration engines for compiz-fusion
rc  libgnome-compiz-manager0                   0.10.3-0ubuntu2                                    Compiz Gnome Manager
ii  python-compizconfig                        0.7.4-0ubuntu1                                     Compiz configuration system bindings

```

---

### Post by Forlong on 2008-06-25
I don't see anything obviously wrong here.
Try this:
```
sudo apt-get purge gnome-compiz-manager libgnome-compiz-manager0
```

---

### Post by SteveNorman on 2008-06-25
```
-desktop:~$ sudo apt-get purge gnome-compiz-manager libgnome-compiz-manager0
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-compiz-manager is not installed, so not removed
Package libgnome-compiz-manager0 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

looks like its not there. Should I :
```
sudo apt-get install gnome-compiz-manager
```?

---

### Post by Forlong on 2008-06-25
Try it like this:
```
sudo dpkg --purge gnome-compiz-manager libgnome-compiz-manager0
```

---

### Post by SteveNorman on 2008-06-25
```
desktop:~$ sudo dpkg --purge gnome-compiz-manager libgnome-compiz-manager0
[sudo] password for steve: 
(Reading database ... 184547 files and directories currently installed.)
Removing gnome-compiz-manager ...
Purging configuration files for gnome-compiz-manager ...
Removing libgnome-compiz-manager0 ...
Purging configuration files for libgnome-compiz-manager0 ...


```

---

### Post by Forlong on 2008-06-25
Now try to run ccsm in a terminal.

---

### Post by SteveNorman on 2008-06-25
No noticeable activity or screen flickers 

```
-desktop:~$ ccsm
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: No module named compizconfig

```

---

### Post by SteveNorman on 2008-06-27
bump

---

### Post by Forlong on 2008-06-27
Sorry for the late reply.
I think we have to do the same thing for 'ccsm' we did for 'compiz' -- purge every package related to Compiz and afterwards post the output of ```
locate ccsm | grep -v ^/var | grep -v ^/home
```

---

### Post by SteveNorman on 2008-06-27
No problem,,Im grateful you are on the case!

```
desktop:~$ locate ccsm | grep -v ^/var | grep -v ^/home

* For Snow: There is no default texture. You can set one in ccsm-
/usr/bin/ccsm
/usr/lib/python2.4/site-packages/ccsm-0.7.4.egg-info
/usr/lib/python2.5/site-packages/ccsm-0.7.4.egg-info
/usr/local/bin/ccsm
/usr/local/lib/python2.5/site-packages/ccsm-0.7.6.egg-info
/usr/local/lib/python2.5/site-packages/ccsm-0.7.7.egg-info
/usr/local/share/ccsm
/usr/local/share/applications/ccsm.desktop
/usr/local/share/ccsm/icons
/usr/local/share/ccsm/images
/usr/local/share/ccsm/icons/hicolor
/usr/local/share/ccsm/icons/hicolor/22x22
/usr/local/share/ccsm/icons/hicolor/icon-theme.cache
/usr/local/share/ccsm/icons/hicolor/scalable
/usr/local/share/ccsm/icons/hicolor/22x22/categories
/usr/local/share/ccsm/icons/hicolor/22x22/devices
/usr/local/share/ccsm/icons/hicolor/22x22/mimetypes
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-accessibility.png
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-desktop.png
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-effects.png
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-extras.png
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-general.png
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-image_loading.png
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-uncategorized.png
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-utility.png
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-window_management.png
/usr/local/share/ccsm/icons/hicolor/22x22/devices/input-keyboard.png
/usr/local/share/ccsm/icons/hicolor/22x22/devices/input-mouse.png
/usr/local/share/ccsm/icons/hicolor/22x22/devices/video-display.png
/usr/local/share/ccsm/icons/hicolor/22x22/mimetypes/audio-x-generic.png
/usr/local/share/ccsm/icons/hicolor/scalable/apps
/usr/local/share/ccsm/icons/hicolor/scalable/categories
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-3d.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-addhelper.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-animation.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-annotate.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-atlantis.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-bench.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-bicubic.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-blur.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-bs.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-capture.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-clone.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-colorfilter.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-core.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-crashhandler.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-cube.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-cubeaddon.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-dbus.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-debug.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-decoration.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-expo.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-extrawm.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-ezoom.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-fade.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-fadedesktop.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-fakeargb.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-firepaint.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-fs.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-gears.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-glib.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-group.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-imgjpeg.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-inotify.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-loginout.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-mag.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-maximumize.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-mblur.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-minimize.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-mousepoll.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-move.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-mswitch.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-neg.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-notification.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-opacify.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-place.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-plane.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-png.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-put.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-reflex.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-regex.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-resize.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-resizeinfo.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-ring.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-rotate.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-scale.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-scaleaddon.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-scalefilter.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-schemep.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-screencasting.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-screensaver.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-screenshot.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-session.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-shelf.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-shift.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-showdesktop.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-showmouse.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-snap.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-snow.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-splash.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-state.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-svg.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-switcher.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-text.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-thumbnail.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-tile.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-trailfocus.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-unknown.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-video.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-vpswitch.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-wall.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-wallpaper.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-water.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-widget.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-winrules.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-wobbly.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-workarounds.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-zoom.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-accessibility.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-all.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-desktop.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-effects.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-extras.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-general.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-image_loading.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-profiles.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-search.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-uncategorized.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-utility.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-window_management.svg
/usr/local/share/ccsm/images/display.png
/usr/local/share/ccsm/images/modifier.png
/usr/local/share/icons/hicolor/16x16/apps/ccsm.png
/usr/local/share/icons/hicolor/22x22/apps/ccsm.png
/usr/local/share/icons/hicolor/22x22/apps/ccsm.svg
/usr/local/share/icons/hicolor/24x24/apps/ccsm.png
/usr/local/share/icons/hicolor/32x32/apps/ccsm.png
/usr/local/share/icons/hicolor/32x32/apps/ccsm.svg
/usr/local/share/icons/hicolor/48x48/apps/ccsm.png
/usr/local/share/icons/hicolor/scalable/apps/ccsm.svg
/usr/local/share/locale/ar/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/bn/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/bn_IN/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/ca/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/cs/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/de/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/el/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/en_GB/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/es/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/eu/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/fi/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/fr/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/gl/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/gu/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/he/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/hi/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/hr/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/hu/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/id/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/it/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/ja/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/ko/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/md/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/nb/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/nl/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/or/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/pa/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/pl/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/pt/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/pt_BR/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/ru/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/sk/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/sv/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/tr/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/wo/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/zh_CN/LC_MESSAGES/ccsm.mo
/usr/share/ccsm
/usr/share/app-install/desktop/ccsm.desktop
/usr/share/app-install/desktop/simple-ccsm.desktop
/usr/share/app-install/icons/ccsm.png
/usr/share/app-install/icons/simple-ccsm.png
/usr/share/applications/ccsm.desktop
/usr/share/ccsm/icons
/usr/share/ccsm/images
/usr/share/ccsm/icons/hicolor
/usr/share/ccsm/icons/hicolor/22x22
/usr/share/ccsm/icons/hicolor/scalable
/usr/share/ccsm/icons/hicolor/22x22/categories
/usr/share/ccsm/icons/hicolor/22x22/devices
/usr/share/ccsm/icons/hicolor/22x22/mimetypes
/usr/share/ccsm/icons/hicolor/22x22/categories/dummy
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-accessibility.png
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-desktop.png
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-effects.png
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-extras.png
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-general.png
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-image_loading.png
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-uncategorized.png
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-utility.png
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-window_management.png
/usr/share/ccsm/icons/hicolor/22x22/devices/input-keyboard.png
/usr/share/ccsm/icons/hicolor/22x22/devices/input-mouse.png
/usr/share/ccsm/icons/hicolor/22x22/devices/video-display.png
/usr/share/ccsm/icons/hicolor/22x22/mimetypes/audio-x-generic.png
/usr/share/ccsm/icons/hicolor/scalable/apps
/usr/share/ccsm/icons/hicolor/scalable/categories
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-3d.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-addhelper.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-animation.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-annotate.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-atlantis.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-bench.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-blur.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-bs.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-capture.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-clone.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-colorfilter.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-core.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-crashhandler.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-cube.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-cubecaps.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-cubereflex.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-dbus.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-debug.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-decoration.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-expo.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-extrawm.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-ezoom.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-fade.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-fadedesktop.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-fakeargb.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-firepaint.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-fs.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-gears.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-glib.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-group.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-imgjpeg.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-inotify.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-loginout.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-mag.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-maximumize.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-mblur.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-minimize.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-mousepoll.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-move.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-mswitch.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-neg.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-notification.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-opacify.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-place.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-plane.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-png.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-put.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-reflex.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-regex.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-resize.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-resizeinfo.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-ring.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-rotate.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-scale.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-scaleaddon.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-scalefilter.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-schemep.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-screencasting.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-screensaver.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-screenshot.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-session.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-shelf.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-shift.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-showdesktop.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-showmouse.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-snap.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-snow.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-splash.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-state.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-svg.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-switcher.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-text.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-thumbnail.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-tile.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-trailfocus.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-unknown.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-video.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-vpswitch.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-wall.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-wallpaper.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-water.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-widget.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-winrules.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-wobbly.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-workarounds.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-zoom.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-accessibility.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-all.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-desktop.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-effects.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-extras.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-general.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-image_loading.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-key_bindings.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-profiles.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-search.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-uncategorized.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-utility.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-window_management.svg
/usr/share/ccsm/images/display.png
/usr/share/ccsm/images/modifier.png
/usr/share/icons/hicolor/16x16/apps/ccsm.png
/usr/share/icons/hicolor/22x22/apps/ccsm.png
/usr/share/icons/hicolor/22x22/apps/ccsm.svg
/usr/share/icons/hicolor/24x24/apps/ccsm.png
/usr/share/icons/hicolor/32x32/apps/ccsm.png
/usr/share/icons/hicolor/32x32/apps/ccsm.svg
/usr/share/icons/hicolor/48x48/apps/ccsm.png
/usr/share/icons/hicolor/scalable/apps/ccsm.svg
/usr/share/locale/ar/LC_MESSAGES/ccsm.mo
/usr/share/locale/bn/LC_MESSAGES/ccsm.mo
/usr/share/locale/bn_IN/LC_MESSAGES/ccsm.mo
/usr/share/locale/ca/LC_MESSAGES/ccsm.mo
/usr/share/locale/cs/LC_MESSAGES/ccsm.mo
/usr/share/locale/de/LC_MESSAGES/ccsm.mo
/usr/share/locale/el/LC_MESSAGES/ccsm.mo
/usr/share/locale/en_GB/LC_MESSAGES/ccsm.mo
/usr/share/locale/es/LC_MESSAGES/ccsm.mo
/usr/share/locale/eu/LC_MESSAGES/ccsm.mo
/usr/share/locale/fi/LC_MESSAGES/ccsm.mo
/usr/share/locale/fr/LC_MESSAGES/ccsm.mo
/usr/share/locale/gl/LC_MESSAGES/ccsm.mo
/usr/share/locale/gu/LC_MESSAGES/ccsm.mo
/usr/share/locale/hi/LC_MESSAGES/ccsm.mo
/usr/share/locale/hr/LC_MESSAGES/ccsm.mo
/usr/share/locale/hu/LC_MESSAGES/ccsm.mo
/usr/share/locale/id/LC_MESSAGES/ccsm.mo
/usr/share/locale/it/LC_MESSAGES/ccsm.mo
/usr/share/locale/ja/LC_MESSAGES/ccsm.mo
/usr/share/locale/ko/LC_MESSAGES/ccsm.mo
/usr/share/locale/md/LC_MESSAGES/ccsm.mo
/usr/share/locale/nb/LC_MESSAGES/ccsm.mo
/usr/share/locale/nl/LC_MESSAGES/ccsm.mo
/usr/share/locale/or/LC_MESSAGES/ccsm.mo
/usr/share/locale/pa/LC_MESSAGES/ccsm.mo
/usr/share/locale/pl/LC_MESSAGES/ccsm.mo
/usr/share/locale/pt/LC_MESSAGES/ccsm.mo
/usr/share/locale/pt_BR/LC_MESSAGES/ccsm.mo
/usr/share/locale/ru/LC_MESSAGES/ccsm.mo
/usr/share/locale/sk/LC_MESSAGES/ccsm.mo
/usr/share/locale/sv/LC_MESSAGES/ccsm.mo
/usr/share/locale/tr/LC_MESSAGES/ccsm.mo
/usr/share/locale/wo/LC_MESSAGES/ccsm.mo
/usr/share/locale/zh_CN/LC_MESSAGES/ccsm.mo
/usr/share/pyshared/ccsm-0.7.4.egg-info

```

---

### Post by Forlong on 2008-06-27
> **Forlong said:**
> purge every package related to Compiz
Did you do that?
If not, please remove it:
```
sudo apt-get purge compizconfig-settings-manager
```
It appears you have still ccsm installed. But that may be because mlocate's database is not up-to date.

Make sure to run this before running the 'locate' command:
```
sudo updatedb
```

---

### Post by SteveNorman on 2008-06-27
I thought I did delete everything,,


```
desktop:~$ sudo apt-get purge compizconfig-settings-manager
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  compizconfig-settings-manager*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4022kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 184585 files and directories currently installed.)
Removing compizconfig-settings-manager ...
Purging configuration files for compizconfig-settings-manager ...

```

```
desktop:~$ sudo updatedb
[sudo] password for steve: 
steve@teampeanut-desktop:~$ locate ccsm | grep -v ^/var | grep -v ^/home

* For Snow: There is no default texture. You can set one in ccsm-
/usr/local/bin/ccsm
/usr/local/lib/python2.5/site-packages/ccsm-0.7.6.egg-info
/usr/local/lib/python2.5/site-packages/ccsm-0.7.7.egg-info
/usr/local/share/ccsm
/usr/local/share/applications/ccsm.desktop
/usr/local/share/ccsm/icons
/usr/local/share/ccsm/images
/usr/local/share/ccsm/icons/hicolor
/usr/local/share/ccsm/icons/hicolor/22x22
/usr/local/share/ccsm/icons/hicolor/icon-theme.cache
/usr/local/share/ccsm/icons/hicolor/scalable
/usr/local/share/ccsm/icons/hicolor/22x22/categories
/usr/local/share/ccsm/icons/hicolor/22x22/devices
/usr/local/share/ccsm/icons/hicolor/22x22/mimetypes
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-accessibility.png
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-desktop.png
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-effects.png
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-extras.png
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-general.png
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-image_loading.png
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-uncategorized.png
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-utility.png
/usr/local/share/ccsm/icons/hicolor/22x22/categories/plugins-window_management.png
/usr/local/share/ccsm/icons/hicolor/22x22/devices/input-keyboard.png
/usr/local/share/ccsm/icons/hicolor/22x22/devices/input-mouse.png
/usr/local/share/ccsm/icons/hicolor/22x22/devices/video-display.png
/usr/local/share/ccsm/icons/hicolor/22x22/mimetypes/audio-x-generic.png
/usr/local/share/ccsm/icons/hicolor/scalable/apps
/usr/local/share/ccsm/icons/hicolor/scalable/categories
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-3d.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-addhelper.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-animation.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-annotate.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-atlantis.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-bench.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-bicubic.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-blur.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-bs.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-capture.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-clone.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-colorfilter.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-core.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-crashhandler.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-cube.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-cubeaddon.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-dbus.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-debug.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-decoration.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-expo.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-extrawm.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-ezoom.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-fade.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-fadedesktop.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-fakeargb.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-firepaint.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-fs.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-gears.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-glib.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-group.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-imgjpeg.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-inotify.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-loginout.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-mag.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-maximumize.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-mblur.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-minimize.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-mousepoll.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-move.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-mswitch.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-neg.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-notification.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-opacify.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-place.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-plane.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-png.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-put.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-reflex.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-regex.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-resize.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-resizeinfo.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-ring.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-rotate.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-scale.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-scaleaddon.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-scalefilter.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-schemep.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-screencasting.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-screensaver.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-screenshot.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-session.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-shelf.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-shift.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-showdesktop.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-showmouse.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-snap.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-snow.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-splash.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-state.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-svg.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-switcher.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-text.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-thumbnail.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-tile.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-trailfocus.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-unknown.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-video.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-vpswitch.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-wall.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-wallpaper.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-water.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-widget.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-winrules.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-wobbly.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-workarounds.svg
/usr/local/share/ccsm/icons/hicolor/scalable/apps/plugin-zoom.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-accessibility.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-all.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-desktop.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-effects.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-extras.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-general.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-image_loading.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-profiles.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-search.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-uncategorized.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-utility.svg
/usr/local/share/ccsm/icons/hicolor/scalable/categories/plugins-window_management.svg
/usr/local/share/ccsm/images/display.png
/usr/local/share/ccsm/images/modifier.png
/usr/local/share/icons/hicolor/16x16/apps/ccsm.png
/usr/local/share/icons/hicolor/22x22/apps/ccsm.png
/usr/local/share/icons/hicolor/22x22/apps/ccsm.svg
/usr/local/share/icons/hicolor/24x24/apps/ccsm.png
/usr/local/share/icons/hicolor/32x32/apps/ccsm.png
/usr/local/share/icons/hicolor/32x32/apps/ccsm.svg
/usr/local/share/icons/hicolor/48x48/apps/ccsm.png
/usr/local/share/icons/hicolor/scalable/apps/ccsm.svg
/usr/local/share/locale/ar/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/bn/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/bn_IN/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/ca/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/cs/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/de/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/el/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/en_GB/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/es/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/eu/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/fi/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/fr/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/gl/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/gu/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/he/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/hi/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/hr/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/hu/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/id/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/it/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/ja/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/ko/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/md/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/nb/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/nl/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/or/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/pa/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/pl/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/pt/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/pt_BR/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/ru/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/sk/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/sv/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/tr/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/wo/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/zh_CN/LC_MESSAGES/ccsm.mo
/usr/share/app-install/desktop/ccsm.desktop
/usr/share/app-install/desktop/simple-ccsm.desktop
/usr/share/app-install/icons/ccsm.png
/usr/share/app-install/icons/simple-ccsm.png

```

---

### Post by Forlong on 2008-06-27
Alright, now try this
```
sudo rm -r /usr/local/share/ccsm
```
```
sudo rm /usr/local/bin/ccsm /usr/local/lib/python2.5/site-packages/ccsm-0.7.6.egg-info /usr/local/lib/python2.5/site-packages/ccsm-0.7.7.egg-info /usr/local/share/applications/ccsm.desktop

```
```
sudo rm $(locate ccsm | grep ^/usr/local/share/locale)
```

Afterwards, install it again and try to run it.

---

### Post by SteveNorman on 2008-06-27
```
desktop:~$ sudo rm -r /usr/local/share/ccsm
[sudo] password for steve: 
steve@teampeanut-desktop:~$ sudo rm /usr/local/bin/ccsm /usr/local/lib/python2.5/site-packages/ccsm-0.7.6.egg-info /usr/local/lib/python2.5/site-packages/ccsm-0.7.7.egg-info /usr/local/share/applications/ccsm.desktop
steve@teampeanut-desktop:~$ sudo rm $(locate ccsm | grep ^/usr/local/share/locale)


```

and for good measure```
~$ locate ccsm | grep -v ^/var | grep -v ^/home
* For Snow: There is no default texture. You can set one in ccsm-
/usr/local/bin/ccsm
/usr/local/lib/python2.5/site-packages/ccsm-0.7.6.egg-info
/usr/local/lib/python2.5/site-packages/ccsm-0.7.7.egg-info
/usr/local/share/ccsm
/usr/local/share/applications/ccsm.desktop
/usr/local/share/icons/hicolor/16x16/apps/ccsm.png
/usr/local/share/icons/hicolor/22x22/apps/ccsm.png
/usr/local/share/icons/hicolor/22x22/apps/ccsm.svg
/usr/local/share/icons/hicolor/24x24/apps/ccsm.png
/usr/local/share/icons/hicolor/32x32/apps/ccsm.png
/usr/local/share/icons/hicolor/32x32/apps/ccsm.svg
/usr/local/share/icons/hicolor/48x48/apps/ccsm.png
/usr/local/share/icons/hicolor/scalable/apps/ccsm.svg
/usr/local/share/locale/ar/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/bn/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/bn_IN/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/ca/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/cs/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/de/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/el/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/en_GB/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/es/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/eu/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/fi/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/fr/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/gl/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/gu/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/he/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/hi/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/hr/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/hu/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/id/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/it/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/ja/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/ko/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/md/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/nb/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/nl/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/or/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/pa/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/pl/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/pt/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/pt_BR/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/ru/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/sk/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/sv/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/tr/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/wo/LC_MESSAGES/ccsm.mo
/usr/local/share/locale/zh_CN/LC_MESSAGES/ccsm.mo
/usr/share/app-install/desktop/ccsm.desktop
/usr/share/app-install/desktop/simple-ccsm.desktop
/usr/share/app-install/icons/ccsm.png
/usr/share/app-install/icons/simple-ccsm.png

```

---

### Post by SteveNorman on 2008-06-29
Bummer furlong,, I was going for Germany too.....

---

### Post by SteveNorman on 2008-07-01
Ttt

---

### Post by SteveNorman on 2008-07-15
I ran through the thread again and redid everything.
When I run ccsm I get this

```
:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: No module named compizconfig

```


I found a similar problem in another thread here:

[http://forum.compiz-fusion.org/showthread.php?t=7626](http://forum.compiz-fusion.org/showthread.php?t=7626)

Unfortunately it is a little to technical for me,,but it looks like the same problem I have. Does anyone have a fix for this?

---

### Post by SteveNorman on 2008-08-28
wells heres the closure on this thread, maybe it can help others. Make sure you read very carefully the warnings on <sudo rm -rf> before attempting this...

what worked for me:

using ubdatedb for ccsm, compiz, emerald
removing everything I found including .ccsm, .compiz, .emerald using the dreaded sudo rm -rf. This was scary, but checking spaces etc. I think I got everything without wiping my / out. 

updateb 
locate <keyword>
rm -rf <*keyword>
rm -rf <keyword*>

repeated for <keyword> = ccsm
                       = .ccsm
                       = compiz
                       = .compiz
                       = fusion
                       = emerald
                       = .emerald
then reloading usings furlongs method from a previous post in this thread.

So now I have my advanced desktop settings available, my ccsm, some effects (burning page water etc). What I still need to fix, rotating cube, in ccsm the icons are blacked out. So I am back on the road, but limping still.

Thanks to all who helped me with this I learned a lot!

summary,,
1 remove all previous versions of an app before installing over it.
2 A program or app may not work if there are duplicate files left/
3 use the command line to search out files and directories, since synaptic may not find them all.
 -"$sudo updatedb" to update the search engine
 -"$locate keyword" where keyword is a file name related to the app being removed
 - remove by hand all files found by locate.
4 after all files are removed, reboot, then reload the app.

BTW I felt safe doing this since I was only deleteing files related to compiz, ccsm, and emerald.

---

