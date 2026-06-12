---
title: "How do I create a appimage from a deb files?"
date: 2021-07-09
forum: General Help
---

### Post by ardouronerous on 2021-07-09
Because of the fiasco regarding Audacity, I'm sticking to version 2.3.3, so I've downloaded it and all of it's dependencies:

```
audacity_2.3.3-1build1_amd64.deb
audacity-data_2.3.3-1build1_all.deb
libflac++6v5_1.3.3-1build1_amd64.deb
libportsmf0v5_0.1~svn20101010-5ubuntu2_amd64.deb
libsuil-0-0_0.10.6-1_amd64.deb
libvamp-hostsdk3v5_2.9.0-1build1_amd64.deb
libwxbase3.0-0v5_3.0.4+dfsg-15build1_amd64.deb
libwxgtk3.0-gtk3-0v5_3.0.4+dfsg-15build1_amd64.deb
```

I'd like to create an appimage of Audacity 2.3.3, so that when I upgrade to the next LTS release, I'm not face with dependency issues. How do I do this?

Note, I'm a noob to appimages and I don't know how to compile stuff from source.

---

### Post by tea for one on 2021-07-09
I imagine that your are referring to the privacy policy of Audacity.
For those who are unaware of this development, there are plenty of hits if you use your favourite search engine.

Anyway, I can't help you with an Appimage, but have you considered a pre-built snap?
[https://snapcraft.io/audacity](https://snapcraft.io/audacity)

---

### Post by ardouronerous on 2021-07-09
> **tea for one said:**
> I imagine that your are referring to the privacy policy of Audacity.
For those who are unaware of this development, there are plenty of hits if you use your favourite search engine.

Yes, I'm referring to the privacy policy which violates the GPL license. The versions without the telemetry is any version below 3.x, which is why I'm sticking to 2.3.3, which is the version available in the Ubuntu repos.

> have you considered a pre-built snap?
[https://snapcraft.io/audacity](https://snapcraft.io/audacity)

Is there a snap of Audacity 2.4.2, which is the last version before version 3.0.0? How do I download old versions of a snap and install offline?

> Anyway, I can't help you with an Appimage

If there is no snap of Audacity 2.4.2, I still want to make an appimage of the deb files that I have.

---

### Post by deadflowr on 2021-07-09
You do know that the telemetry and dial-home/tracking features can be disabled at compile time.
In fact it looks like Debian developers are already looking into it:
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=990737]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=990737")
As Ubuntu usually simply rebuilds what Debian does for audacity, expect whatever they do to be what Ubuntu does with it.


That stated, look here for appimage builder tools: [https://github.com/AppImageCrafters/appimage-builder]("https://github.com/AppImageCrafters/appimage-builder")

---

### Post by monkeybrain20122 on 2021-07-09
Here is a quick and dirty way which achieves the same goal for you as an appimage except it is a lot easier (though a bit tedious)

Create a folder somewhere called audacity, in it make the following directories : bin, lib, share

Now extract all the .debs you downloaded (right click and choose extract instead of install) They are just archives. In all of them there is a directory called 'data', extract that too (you can ignore the debian stuffs) In it there is a subfolder called usr, inside you find bin, lib, etc. Copy the contents to the matching locations inside the audacity folder you created.

Now to start using audacity you need to ensure the binary can find the runtime libraries, so create a script called audacity like so (let's say your audacity folder is in your $HOME, you can modify the LD_LIBRARY_PATH and PATH accordingly if you put it elsewhere


```
#! /bin/bash
export LD_LIBRARY_PATH=$HOME/audacity/lib:$LD_LIBRARY_PATH
export PATH=$HOME/audacity/bin:$PATH

$HOME/audacity/bin/audacity
```


Now make this script executable (either right click > properties > permission and check allow to execute or "chmod + x /path/to/audacity/script")

Place this script in your path (e.g ~/.local/bin)

then you should be able to start audacity by just typing audacity in the terminal. In audacity/share/applications there should be a audacity.desktop file. Open it with a text editor, make sure the Exec line should be "Exec=audacity %F" and in "Icon=" line, put the path to an audacity logo in audacity/share/icons. Now make this .desktop file executable and put it in .local/share/applications. You should be able to see it in the dash or menu depending on your DE (may need to logout and login) You can just click it to start like any other installed apps.

**Edited:** you may or may not face dependency issues after you do OS upgrade because even an appimage may depend on system libraries so this is not always portable. To find out what else from the system you may need you can do a ldd  and ld --verbose  for the libraries and the bin after you export the LD_LIBARRY_PATH  in the terminal as in the audacity script above (without running audacity) and check which libraries are loaded at run time besides those in audacity/lib. 

If something is amiss after OS update it can usually be fixed as follows: let's say it depends on libfoo.xxx and OS update upgrades to libfoo.xxx+1 or removes libfoo from repo, you can download an old deb from Ubuntu's archive, extract it as above and place the .so files in audacity/lib again as above.  The hardest stuffs maybe something like gtk or libc, if those are involved you may have no other ways but to compile from source.

If you have enough ram to run a VM maybe you could move the audacity folder and the audacity script (change the paths accordingly) to Ubuntu next or even a different distro  to see if it works.

---

### Post by TheFu on 2021-07-09
I use audacity and think worrying about this is premature for most people.  If you stay with an LTS release of Ubuntu, then you have a year before it becomes an issue. In the next year, it will be worked out either with a fork in the project (openoffice/libreoffice like) or with other cleaner options.

Snaps are not a replacement for AppImages, I'm sorry to say.  This is especially true when large data files are involved.  Snaps don't work with network storage. That makes them worthless for many people.  OTOH, AppImages do work fine with network storage.

---

### Post by monkeybrain20122 on 2021-07-09
Besides, snap is automatically updated and usually packaged by third parties or the upstream (meaning MUSE in this case) so it likely will have those undesirable features incorporated anyway.

---

### Post by ardouronerous on 2021-07-09
> **monkeybrain20122 said:**
> Here is a quick and dirty way which  achieves the same goal for you as an appimage except it is a lot easier  (though a bit tedious)

Create a folder somewhere called audacity, in it make the following directories : bin, lib, share

Now extract all the .debs you downloaded (right click and choose extract  instead of install) They are just archives. In all of them there is a  directory called 'data', extract that too (you can ignore the debian  stuffs) In it there is a subfolder called usr, inside you find bin, lib,  etc. Copy the contents to the matching locations inside the audacity  folder you created.

Now to start using audacity you need to ensure the binary can find the  runtime libraries, so create a script called audacity like so (let's say  your audacity folder is in your $HOME, you can modify the  LD_LIBRARY_PATH and PATH accordingly if you put it elsewhere


```
#! /bin/bash
export LD_LIBRARY_PATH=$HOME/audacity/lib:$LD_LIBRARY_PATH
export PATH=$HOME/audacity/bin:$PATH

$HOME/audacity/bin/audacity
```


Now make this script executable (either right click > properties >  permission and check allow to execute or "chmod + x  /path/to/audacity/script")

Place this script in your path (e.g ~/.local/bin)

then you should be able to start audacity by just typing audacity in the  terminal. In audacity/share/applications there should be a  audacity.desktop file. Open it with a text editor, make sure the Exec  line should be "Exec=audacity %F" and in "Icon=" line, put the path to  an audacity logo in audacity/share/icons. Now make this .desktop file  executable and put it in .local/share/applications. You should be able  to see it in the dash or menu depending on your DE (may need to logout  and login) You can just click it to start like any other installed apps.

**Edited:** you may or may not face dependency issues after  you do OS upgrade because even an appimage may depend on system  libraries so this is not always portable. To find out what else from the  system you may need you can do a ldd  and ld --verbose  for the  libraries and the bin after you export the LD_LIBARRY_PATH  in the  terminal as in the audacity script above (without running audacity) and  check which libraries are loaded at run time besides those in  audacity/lib. 

If something is amiss after OS update it can usually be fixed as  follows: let's say it depends on libfoo.xxx and OS update upgrades to  libfoo.xxx+1 or removes libfoo from repo, you can download an old deb  from Ubuntu's archive, extract it as above and place the .so files in  audacity/lib again as above.  The hardest stuffs maybe something like  gtk or libc, if those are involved you may have no other ways but to  compile from source.

If you have enough ram to run a VM maybe you could move the audacity  folder and the audacity script (change the paths accordingly) to Ubuntu  next or even a different distro  to see if it works.

Thank you, this worked!

---

### Post by ardouronerous on 2021-07-10
I spoke too soon, I'm getting an error:

```
audacity
/home/~/audacity/bin/audacity: error while loading shared libraries: libwx_gtk3u_html-3.0.so.0: cannot open shared object file: No such file or directory
```

libwx_gtk3u_html-3.0.so.0 is inside [FONT=courier new]/home/~/audacity/lib/x86_64-linux-gnu/[/FONT] though.

---

### Post by ardouronerous on 2021-07-10
> **ardouronerous said:**
> I spoke too soon, I'm getting an error:

```
audacity
/home/~/audacity/bin/audacity: error while loading shared libraries: libwx_gtk3u_html-3.0.so.0: cannot open shared object file: No such file or directory
```

libwx_gtk3u_html-3.0.so.0 is inside [FONT=courier new]/home/~/audacity/lib/x86_64-linux-gnu/[/FONT] though.

I figured it out:

```
#! /bin/bash
export LD_LIBRARY_PATH=$HOME/audacity/lib**/x86_64-linux-gnu**:$LD_LIBRARY_PATH
export PATH=$HOME/audacity/bin:$PATH

$HOME/audacity/bin/audacity 
```

---

### Post by ardouronerous on 2021-07-10
I'm experiencing some issues with this though. I cannot open mp3 files with Audacity from my file manager, like when I try to open an mp3 file from my file manager, Audacity opens, but the music doesn't load, however, if I open Audacity and press File -> Open -> mp3 file, the music loads.

---

### Post by monkeybrain20122 on 2021-07-10
> **ardouronerous said:**
> I'm experiencing some issues with this though. I cannot open mp3 files with Audacity from my file manager, like when I try to open an mp3 file from my file manager, Audacity opens, but the music doesn't load, however, if I open Audacity and press File -> Open -> mp3 file, the music loads.

Ok, try change the last line in your audacity script to 
```
$HOME/audacity/bin/audacity "$@"
```

Then logout and login and try again.

---

### Post by ardouronerous on 2021-07-10
> **monkeybrain20122 said:**
> Ok, try change the last line in your audacity script to 
```
$HOME/audacity/bin/audacity "$@"
```

Then logout and login and try again.

Thank you that worked!

```
#! /bin/bash
export LD_LIBRARY_PATH=$HOME/audacity/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH
export PATH=$HOME/audacity/bin:$PATH

**$HOME/audacity/bin/audacity "$@" **
```

---

