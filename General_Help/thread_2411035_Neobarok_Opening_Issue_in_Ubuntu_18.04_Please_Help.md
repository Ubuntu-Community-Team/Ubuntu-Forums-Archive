---
title: "Neobarok Opening Issue in Ubuntu 18.04 Please Help Thanks"
date: 2019-01-23
forum: General Help
---

### Post by specflowlover123 on 2019-01-23
Hi Everyone  i am a little new to using Linux - and i am having an Issue opening this Application:
Neobarok is an Open Source 3D Modelling Software:
[https://neobarok.com/](https://neobarok.com/)

The Installation for Neobarok seems a little Cryptic for a Newbie like me:
[https://sites.google.com/site/neobarokguide/install](https://sites.google.com/site/neobarokguide/install)
[LINUX]("http://neobarok.com/Neobarok-1.1.3-linux.zip")


[LIST]
[*]install Qt packages: libqt5core5, libqt5gui5, libqt5opengl5, libqt5widgets5
[*]install SFML package: libsfml-window2
[*]run Neobarok
[*]if "error while loading shared libraries: libsfml-window.so.2.3" 
create symlink: 
sudo ln -s /usr/lib/libsfml-window.so.2.4 /usr/lib/libsfml-window.so.2.3
[/LIST]

Ubuntu Version:
```

lsb_release -aNo LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.1 LTS
Release:	18.04
Codename:	bionic

```

i am recieving this Error Message everytime i try to Open Neobarok:
```

./Neobarok
./Neobarok: error while loading shared libraries: libsfml-window.so.2.3: cannot open shared object file: No such file or directory

```

i assume what i need to do is install libsfml - but i do not know how to do that

would somebody be able to help please
Please let me know if you need any more information about my current System - i would be more than happy to give it
Thank you very much :KS

---

### Post by specflowlover123 on 2019-01-23
```
dpkg -s 'libsfml'dpkg-query: package 'libsfml' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

dpkg -s 'sfml'
dpkg-query: package 'sfml' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

```

---

### Post by coffeecat on 2019-01-23
*Thread moved to **General Help**, for a better fit.*

You are getting the exact error the installation instructions describe in bullet point 4. Did you create the symlink? What that means is to run this:

```
sudo ln -s /usr/lib/libsfml-window.so.2.4 /usr/lib/libsfml-window.so.2.3
```

... in a terminal.

If you don't know how to do that:

1 - open a terminal with ctrl-alt-t
2 - run the command. To avoid errors, copy and paste that line from the website. For pasting into a terminal, use ctrl-shift-v.
3 - you will be prompted for your password. Simply type it in and press enter. Nothing will be echoed to the screen as you do that, but the password is being typed in.

---

### Post by coffeecat on 2019-01-23
Just to add:

Looking at those listed dependencies, the nearest matches in the 18.04 repository are:

libqt5core5a, libqt5gui5, libqt5opengl5, libqt5widgets5

That is, 5a and not 5 for the first package. I suggest you try installing those four as I have listed them.

For libsfml-window2, the 18.04 repository has libsfml-window2.4. That symlink looks as though it should work with libsfml-window2.4, and my guess is that "libsfml-window2" was just shorthand for whatever point version of libsfml-window2 you are able to install.

---

### Post by HermanAB on 2019-01-24
Note that FreeCAD and MeshLab are in the software repositories and can be installed easily.
[https://www.aeronetworks.ca/2014/12/freecad.html](https://www.aeronetworks.ca/2014/12/freecad.html)

---

### Post by specflowlover123 on 2019-01-24
Hello Thank you very much for helping out
i tried the Symlink query you gave me: it looks like it worked from the Outset - but i still cannot open Neobarok for some reason

```

sudo ln -s /usr/lib/libsfml-window.so.2.4 /usr/lib/libsfml-window.so.2.3
[sudo] password for ME :
```

i Tried again to see if that would make a difference both in the folder in question and in 
```

~/Desktop$ sudo ln -s /usr/lib/libsfml-window.so.2.4 /usr/lib/libsfml-window.so.2.3 ln: failed to create symbolic link '/usr/lib/libsfml-window.so.2.3': File exists
~/Desktop$ cd
~$ sudo ln -s /usr/lib/libsfml-window.so.2.4 /usr/lib/libsfml-window.so.2.3 ln: failed to create symbolic link '/usr/lib/libsfml-window.so.2.3': File exists

```

if you could give me some more brain energy pretty please
i feel like i mucked up somewhere
Thank you very much

---

### Post by specflowlover123 on 2019-01-24
Thank you for the Suggestion - i like Neobarok because it has an easy to use UI, also this is an important stepping stone in learning how to use Ubuntu and the Linux CMD, Thank you.

---

### Post by coffeecat on 2019-01-24
> **specflowlover123 said:**
> 
i tried the Symlink query you gave me: it looks like it worked from the Outset - but i still cannot open Neobarok for some reason


I think the symlink won't work unless you have installed the  libsfml-window2.4 package. See my second post in this thread.

---

### Post by specflowlover123 on 2019-01-24
i  don't know how to do that- thank you for your help
sorry im a bit new - Thanks

---

### Post by specflowlover123 on 2019-01-25
it seems i have the latest Libsfml-2.4 installed

```

sudo apt-get install libsfml-devReading package lists... Done
Building dependency tree       
Reading state information... Done
libsfml-dev is already the newest version (2.4.2+dfsg-4).
The following packages were automatically installed and are no longer required:
  cura-engine fdm-materials fonts-open-sans libarcus3 libllvm6.0:i386
  libmono-system-runtime-interopservices-runtimeinformation4.0-cil
  libpolyclipping22 libpugixml1v5 libsavitar0 python3-arcus python3-decorator
  python3-nine python3-numpy python3-pyqt5.qtopengl python3-pyqt5.qtquick
  python3-pyqt5.qtsvg python3-python-utils python3-savitar python3-scipy
  python3-serial python3-stl python3-uranium python3-zeroconf
  qml-module-qt-labs-folderlistmodel qml-module-qt-labs-settings
  qml-module-qtgraphicaleffects qml-module-qtqml-models2
  qml-module-qtquick-controls qml-module-qtquick-dialogs
  qml-module-qtquick-layouts qml-module-qtquick-privatewidgets
  qml-module-qtquick-window2 qml-module-qtquick2 uranium-plugins
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 4 not to upgrade.

```

i did a Sudo Apt Update
and Sudo apt -full-Upgrade
with no Yield

Please Help

---

### Post by coffeecat on 2019-01-25
> **specflowlover123 said:**
> it seems i have the latest Libsfml-2.4 installed


Maybe, maybe not. You installed libsfml-dev. You need to install libsfml-window2.4. Read my post #4. When instructions tell you to install butterflies, you won't get very far installing humming-birds. You have to be accurate. Even down to capitalisation. There is no such thing as Libsfml, only libsfml. That being said, libsfml-window2.4 ought to be a dependency of lbsfml-dev so it may already be installed. Check that you have libsfml-window2.4 installed, and if you don't, install it.

And you need to install the other four packages listed in my post #4. Even then I'm not sure it will work. The installation instructions are sloppy.

---

### Post by specflowlover123 on 2019-01-26
Apologies for that
and thanks for the Help
it looks like i have this one already as well:
Thanks

```

sudo apt-get install libsfml-window2.4[sudo] password for dilan2814: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsfml-window2.4 is already the newest version (2.4.2+dfsg-4).
libsfml-window2.4 set to manually installed.
The following packages were automatically installed and are no longer required:
  cura-engine fdm-materials fonts-open-sans libarcus3 libllvm6.0:i386
  libmono-system-runtime-interopservices-runtimeinformation4.0-cil
  libpolyclipping22 libpugixml1v5 libsavitar0 python3-arcus python3-decorator
  python3-nine python3-numpy python3-pyqt5.qtopengl python3-pyqt5.qtquick
  python3-pyqt5.qtsvg python3-python-utils python3-savitar python3-scipy
  python3-serial python3-stl python3-uranium python3-zeroconf
  qml-module-qt-labs-folderlistmodel qml-module-qt-labs-settings
  qml-module-qtgraphicaleffects qml-module-qtqml-models2
  qml-module-qtquick-controls qml-module-qtquick-dialogs
  qml-module-qtquick-layouts qml-module-qtquick-privatewidgets
  qml-module-qtquick-window2 qml-module-qtquick2 uranium-plugins
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 4 not to upgrade.



```

---

### Post by coffeecat on 2019-01-26
And.... ?

(hint - 4 packages)

---

### Post by specflowlover123 on 2019-01-27
Good Point
it seems i have all of those as well

```

sudo apt-get install libqt5core5a[sudo] password for Me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt5core5a is already the newest version (5.9.5+dfsg-0ubuntu1).
The following packages were automatically installed and are no longer required:
  cura-engine fdm-materials fonts-open-sans libarcus3 libllvm6.0:i386
  libmono-system-runtime-interopservices-runtimeinformation4.0-cil
  libpolyclipping22 libpugixml1v5 libsavitar0 python3-arcus python3-decorator
  python3-nine python3-numpy python3-pyqt5.qtopengl python3-pyqt5.qtquick
  python3-pyqt5.qtsvg python3-python-utils python3-savitar python3-scipy
  python3-serial python3-stl python3-uranium python3-zeroconf
  qml-module-qt-labs-folderlistmodel qml-module-qt-labs-settings
  qml-module-qtgraphicaleffects qml-module-qtqml-models2
  qml-module-qtquick-controls qml-module-qtquick-dialogs
  qml-module-qtquick-layouts qml-module-qtquick-privatewidgets
  qml-module-qtquick-window2 qml-module-qtquick2 uranium-plugins
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 4 not to upgrade.

sudo apt-get install libqt5gui5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt5gui5 is already the newest version (5.9.5+dfsg-0ubuntu1).
The following packages were automatically installed and are no longer required:
  cura-engine fdm-materials fonts-open-sans libarcus3 libllvm6.0:i386
  libmono-system-runtime-interopservices-runtimeinformation4.0-cil
  libpolyclipping22 libpugixml1v5 libsavitar0 python3-arcus python3-decorator
  python3-nine python3-numpy python3-pyqt5.qtopengl python3-pyqt5.qtquick
  python3-pyqt5.qtsvg python3-python-utils python3-savitar python3-scipy
  python3-serial python3-stl python3-uranium python3-zeroconf
  qml-module-qt-labs-folderlistmodel qml-module-qt-labs-settings
  qml-module-qtgraphicaleffects qml-module-qtqml-models2
  qml-module-qtquick-controls qml-module-qtquick-dialogs
  qml-module-qtquick-layouts qml-module-qtquick-privatewidgets
  qml-module-qtquick-window2 qml-module-qtquick2 uranium-plugins
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 4 not to upgrade.

sudo apt-get install libqt5opengl5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt5opengl5 is already the newest version (5.9.5+dfsg-0ubuntu1).
The following packages were automatically installed and are no longer required:
  cura-engine fdm-materials fonts-open-sans libarcus3 libllvm6.0:i386
  libmono-system-runtime-interopservices-runtimeinformation4.0-cil
  libpolyclipping22 libpugixml1v5 libsavitar0 python3-arcus python3-decorator
  python3-nine python3-numpy python3-pyqt5.qtopengl python3-pyqt5.qtquick
  python3-pyqt5.qtsvg python3-python-utils python3-savitar python3-scipy
  python3-serial python3-stl python3-uranium python3-zeroconf
  qml-module-qt-labs-folderlistmodel qml-module-qt-labs-settings
  qml-module-qtgraphicaleffects qml-module-qtqml-models2
  qml-module-qtquick-controls qml-module-qtquick-dialogs
  qml-module-qtquick-layouts qml-module-qtquick-privatewidgets
  qml-module-qtquick-window2 qml-module-qtquick2 uranium-plugins
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 4 not to upgrade.

sudo apt-get install libqt5widgets5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt5widgets5 is already the newest version (5.9.5+dfsg-0ubuntu1).
The following packages were automatically installed and are no longer required:
  cura-engine fdm-materials fonts-open-sans libarcus3 libllvm6.0:i386
  libmono-system-runtime-interopservices-runtimeinformation4.0-cil
  libpolyclipping22 libpugixml1v5 libsavitar0 python3-arcus python3-decorator
  python3-nine python3-numpy python3-pyqt5.qtopengl python3-pyqt5.qtquick
  python3-pyqt5.qtsvg python3-python-utils python3-savitar python3-scipy
  python3-serial python3-stl python3-uranium python3-zeroconf
  qml-module-qt-labs-folderlistmodel qml-module-qt-labs-settings
  qml-module-qtgraphicaleffects qml-module-qtqml-models2
  qml-module-qtquick-controls qml-module-qtquick-dialogs
  qml-module-qtquick-layouts qml-module-qtquick-privatewidgets
  qml-module-qtquick-window2 qml-module-qtquick2 uranium-plugins
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 4 not to upgrade.



```

Thanks for the help :KS
we're almost there i can already taste it

---

### Post by coffeecat on 2019-01-28
I have no good news for you.

I'm running Ubuntu 18.04, so I downloaded the Neobarok package for Linux, and installed the 4 packages plus libsfml-window2.4. Like you at first I got the "error while loading shared libraries: libsfml-window.so.2.3" message.

What I've discovered is that this suggested command:

```
sudo ln -s /usr/lib/libsfml-window.so.2.4 /usr/lib/libsfml-window.so.2.3
```

... is never going to work as intended. To deconstruct that for you, It created a symlink at /usr/lib/libsfml-window.so.2.3 - which is what the Neobarok application expects - to the installed library /usr/lib/libsfml-window.so.2.4 . Except that the version of libsfml-window2.4 in the 18.04 repository puts that library at /usr/lib/x86_64-linux-gnu/libsfml-window.so.2.4 .

I tried creating the /usr/lib/libsfml-window.so.2.3 symlink linked to /usr/lib/x86_64-linux-gnu/libsfml-window.so.2.4. After that if I try to run Neobarok from the terminal, the error message no longer appears, but I just get taken back to the terminal prompt. Nothing opens.

I don't know what to suggest next, or even if anything would be productive. It's not a good sign that their instructions for creating a symlink are faulty, at least with Ubuntu and every distro that uses the Ubuntu repositories - a very significant chunk of the Linux world.

---

