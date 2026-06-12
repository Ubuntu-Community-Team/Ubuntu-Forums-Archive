---
title: "Google Earth"
date: 2014-04-20
forum: General Help
---

### Post by BigSilly on 2014-04-20
Hey! :)

Install of 64 bit edition of Ubuntu 14.04 onto a Samsung NP355VC with 6Gb RAM but a dual core AMD processor. Install went flawlessly and setup similarly so with minimal tweaking regarding function keys. Only real issue thus far has been installation of Google Earth which isn't working. Followed numerous guides but nowt works.

Otherwise massively impressed with new Ubuntu and am considering it for my own desktop PC which is running Mint at the mo. ;)

---

### Post by jdeca57 on 2014-04-20
> **BigSilly said:**
>  Only real issue thus far has been installation of Google Earth which isn't working. 
Otherwise massively impressed with new Ubuntu and am considering it for my own desktop PC which is running Mint at the mo. ;)
I followed [http://www.noobslab.com/2014/03/install-google-earth-in-ubuntulinux.html](http://www.noobslab.com/2014/03/install-google-earth-in-ubuntulinux.html) and that seems to work. (64-bit) but I'm no expert with Google Earth, I just play with it.
But indeed, it seems a very good release.

---

### Post by BigSilly on 2014-04-20
> **jdeca57 said:**
> I followed [http://www.noobslab.com/2014/03/install-google-earth-in-ubuntulinux.html](http://www.noobslab.com/2014/03/install-google-earth-in-ubuntulinux.html) and that seems to work. (64-bit) but I'm no expert with Google Earth, I just play with it.
But indeed, it seems a very good release.

Thanks for that but I've already tried it. Doesn't work for me sadly on this laptop. Splash screen appears, then I get a crash and a signal 11 error if running from the terminal. :(

---

### Post by bapoumba on 2014-04-20
Moved these posts (first one copied so it is still in the original thread : [http://ubuntuforums.org/showthread.php?t=2217531](http://ubuntuforums.org/showthread.php?t=2217531)) in a separate support thread. The original one is for feedback only :)

---

### Post by Newbunto on 2014-04-25
Google Earth was flaky in 13.10 and is still flaky in 14.04. Started OK twice. Crashed lots of times at the splash screen. Was really hoping that this would be reliable in 14.04.

---

### Post by monkeybrain20122 on 2014-04-25
I installed the 64 bit by rebuilding the .deb
See post #5 of [http://ubuntuforums.org/showthread.php?t=2196304](http://ubuntuforums.org/showthread.php?t=2196304)
See post #27 and #28 for getting the Panoramio pictures back.

Tested in 13.10 and 14.04.

---

### Post by Cbhihe on 2014-06-23
My install of G-Earth to run on Trusty 64 bits was flawless. 
I used: *[http://www.noobslab.com/2014/03/install-google-earth-in-ubuntulinux.html#alternative-method64](http://www.noobslab.com/2014/03/install-google-earth-in-ubuntulinux.html#alternative-method64)*

I just had to relaunch it a second time before all of G-Earth's  features kicked in. (wonder why this happens sometimes, especially if I don't restart my session, but just relaunch the app.)

I am wondering if others see the same thing as I...
    Everything seems to work perfectly well except I see none of the pictures usually available in Google Earth. Concretely, I can open the corresponding windows, but the pictures are actually never displayed.
    Any clue anyone ? Tx.
-ced

---

### Post by oldos2er on 2014-06-23
See posts #27, 28 & 29 here: [http://ubuntuforums.org/showthread.php?t=2196304](http://ubuntuforums.org/showthread.php?t=2196304)

---

### Post by Cbhihe on 2014-06-25
Hi oldos2er and thank you for the pointer.
I had not realized that the "Panoramio images" mentioned by monkeybrain20122 were just what I called "pictures" in the post following his. So much for being awake.

I have a little problem though as, for instance, I have no 'ia32-libs' dependency shown on  the *Depends* line of my '/var/lib/dpkg/status' file. So I am not sure of the extent to which your fix applies in my case.

I downloaded the version of the tar.xz you refer to in your post, 'ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz' and untarred it in /opt/google/earth/free after installing libfreeimage3 per monkeybrain20122's post [http://ubuntuforums.org/showthread.php?t=2196304&p=12892580#post12892580](http://ubuntuforums.org/showthread.php?t=2196304&p=12892580#post12892580).
The stdout for the untarring was:
```
googleearth
libQtCore.so.4
libQtGui.so.4
libQtNetwork.so.4
libQtWebKit.so.4
patchlib
plugins/
plugins/imageformats/
plugins/imageformats/libqjpeg.so
plugins/imageformats/libqgif.so
```

Trying to launch G-Earth produced:
```
>  google-earth
ERROR: ld.so: object 'libfreeimage.so.3' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS64): ignored.
./googleearth-bin: symbol lookup error: ./libge_chrome_net.so: undefined symbol: _Z34QBasicAtomicInt_fetchAndAddOrderedPVii
```

So obviously I did something incomplete and/or wrong.... :confused:

---

