---
title: "RAW Thumbnails"
date: 2024-11-07
forum: General Help
---

### Post by asherax on 2024-11-07
Is anyone actively working on this issue? 

It appears across many forums, and seems to be a ubiquitously universal issue. No programs or apps in Ubuntu will allow RAW image Thumbnails to be displayed in Ubuntu 24.04.1, that kind of makes Ubuntu a no go, in fact maybe even the latest Gnome kernels a no go area for digital artists, photographers and graphic designers, or indeed anyone who works in the graphics industry or just uses a modern day digital camera. 

Kind of seems important, but I haven't seen any movement on it at all. It used to be handled by slight work arounds for alternate thumbnailers, with scripting available. But those thumbnailers no longer work or exist in 2024. 

Anyone had luck with any common RAWS?

---

### Post by 1fallen on 2024-11-07
My needs are simple, so this is all I need "nomacs"
```
apt show nomacs
Package: nomacs
Version: 3.17.2282+dfsg-2build2
Priority: optional
Section: universe/graphics
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: LXQt Packaging Team <team+lxqt@tracker.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 4,043 kB
Depends: libc6 (>= 2.34), libexiv2-27 (>= 0.27.5), libgcc-s1 (>= 3.3.1), libopencv-core406 (>= 4.6.0+dfsg), libopencv-imgproc406 (>= 4.6.0+dfsg), libqt5concurrent5t64 (>= 5.6.0~rc), libqt5core5t64 (>= 5.15.1), libqt5gui5t64 (>= 5.14.1) | libqt5gui5-gles (>= 5.14.1), libqt5network5t64 (>= 5.0.2), libqt5printsupport5t64 (>= 5.2.0), libqt5svg5 (>= 5.6.0~beta), libqt5widgets5t64 (>= 5.15.1), libquazip5-1 (>= 0.7.3), libraw23t64 (>= 0.21.1), libstdc++6 (>= 13.1), libtiff6 (>= 4.0.3), qt5-image-formats-plugins
Recommends: nomacs-l10n (= 3.17.2282+dfsg-2build2)
Breaks: libnomacscore3 (<< 3.6.1), libnomacsgui3 (<< 3.6.1), libnomacsloader3 (<< 3.6.1)
Replaces: libnomacscore3 (<< 3.6.1), libnomacsgui3 (<< 3.6.1), libnomacsloader3 (<< 3.6.1)
Homepage: https://nomacs.org/
Download-Size: 1,265 kB
APT-Manual-Installed: yes
APT-Sources: http://archive.ubuntu.com/ubuntu plucky/universe amd64 Packages
Description: image viewer with capability of syncing multiple instances
 nomacs is a free image viewer for Windows and Linux systems, which is
 licensed under the GNU General Public License v3. nomacs is small, fast and
 able to handle the most common image formats. Additionally it is possible to
 synchronize multiple viewers. A synchronization of viewers running on
 the same computer or via LAN is possible. It allows one to compare images
 and spot the differences (e.g. schemes of architects to show the
 progress).
```

BTW This is .deb install and not a snap. I run NO snaps.

---

### Post by ajgreeny on 2024-11-07
In my opinion **nomacs** is one of the best image viewers for Linux with many image editing and managing abilities as well; definitely worth having a look at.

---

### Post by asherax on 2024-11-07
Yep nothing wrong with nomacs... I mean, Eye of Gnome, GThumb, Rawtherapee, Darktable, Shotwell, etc etc are all good at what they do, some phenomenal editors, others good photographic and Image organizers, BUT it doesn't solve the issue of RAW thumbnails not showing in Nautilus or Ubuntu Desktop though, so whether Nomacs is a nice simple image viewer is somewhat redundant. Not much use when you open a file in Nautilus, to use a program like nomacs, and wish to select a RAW file, say from Olympus, Orf, or Nikon, Nef, and none of the images can be seen. 

It's like a big guessing game, where you have to troll through your images... and if you have say 2 terabytes of Images to go through, not being able to instantly identify the RAW file you need from a file in Nautilus, well that becomes an issue...

---

### Post by 1fallen on 2024-11-07
> **asherax said:**
> Yep nothing wrong with nomacs... I mean, Eye of Gnome, GThumb, Rawtherapee, Darktable, Shotwell, etc etc are all good at what they do, some phenomenal editors, others good photographic and Image organizers, BUT it doesn't solve the issue of RAW thumbnails not showing in Nautilus or Ubuntu Desktop though, so whether Nomacs is a nice simple image viewer is somewhat redundant. Not much use when you open a file in Nautilus, to use a program like nomacs, and wish to select a RAW file, say from Olympus, Orf, or Nikon, Nef, and none of the images can be seen. 

It's like a big guessing game, where you have to troll through your images... and if you have say 2 terabytes of Images to go through, not being able to instantly identify the RAW file you need from a file in Nautilus, well that becomes an issue...

I'm non Gnome user, but dose this file live in your world:
```
less /usr/share/thumbnailers/gdk-pixbuf-thumbnailer.thumbnailer 

```

Mine xfce session shows:
```
image/x-3fr;image/x-adobe-dng;image/x-arw;image/x-bay;image/x-canon-cr2;image/x-canon-crw;image/x-cap;image/x-cr2;image/x-crw;image/x-dcr;image/x-dcraw;image/x-dcs;image/x-dng;image/x-drf;image/x-eip;image/x-erf;image/x-fff;image/x-fuji-raf;image/x-iiq;image/x-k25;image/x-kdc;image/x-mef;image/x-minolta-mrw;image/x-mos;image/x-mrw;image/x-nef;image/x-nikon-nef;image/x-nrw;image/x-olympus-orf;image/x-orf;image/x-panasonic-raw;image/x-panasonic-raw2;image/x-pef;image/x-pentax-pef;image/x-ptx;image/x-pxn;image/x-r3d;image/x-raf;image/x-raw;image/x-rw2;image/x-rwl;image/x-rwz;image/x-samsung-srw;image/x-sigma-x3f;image/x-sony-arw;image/x-sony-sr2;image/x-sony-srf;image/x-sr2;image/x-srf;image/x-x3f;
```
That's not complete It's what I added years back and still work for me today, from 22.04 thru 25.04 (Devel) 

I'll leave you to it then... I did install Nautilus with screenshot included..

---

### Post by grahammechanical on 2024-11-07
This is a big issue for you. But not for me. I suspect that it is not a big issue for those who program file managers. Perhaps you could explain why the developers of file managers for the different distributions of Linux do not want to add providing thumbnails of RAW image files to their file managers.

It could be that there are already several programs dedicated to the manipulation of image files that also provide this functionality. It could also be that adding that functionality would be possible but difficult and turn a file manager into an image manipulation program.

Regards

---

### Post by asherax on 2024-11-07
> **1fallen said:**
> I'm non Gnome user, but dose this file live in your world:
```
less /usr/share/thumbnailers/gdk-pixbuf-thumbnailer.thumbnailer 

```

Mine xfce session shows:
```
image/x-3fr;image/x-adobe-dng;image/x-arw;image/x-bay;image/x-canon-cr2;image/x-canon-crw;image/x-cap;image/x-cr2;image/x-crw;image/x-dcr;image/x-dcraw;image/x-dcs;image/x-dng;image/x-drf;image/x-eip;image/x-erf;image/x-fff;image/x-fuji-raf;image/x-iiq;image/x-k25;image/x-kdc;image/x-mef;image/x-minolta-mrw;image/x-mos;image/x-mrw;image/x-nef;image/x-nikon-nef;image/x-nrw;image/x-olympus-orf;image/x-orf;image/x-panasonic-raw;image/x-panasonic-raw2;image/x-pef;image/x-pentax-pef;image/x-ptx;image/x-pxn;image/x-r3d;image/x-raf;image/x-raw;image/x-rw2;image/x-rwl;image/x-rwz;image/x-samsung-srw;image/x-sigma-x3f;image/x-sony-arw;image/x-sony-sr2;image/x-sony-srf;image/x-sr2;image/x-srf;image/x-x3f;
```
That's not complete It's what I added years back and still work for me today, from 22.04 thru 25.04 (Devel) 

I'll leave you to it then... I did install Nautilus with screenshot included..

That's exactly the fix I used with MATE 20.04 and it worked flawlessly for all RAW file types, with multiple cameras, although have to say UFRaw also worked great until it was discontinued. Its an elegant solution, and will fix it of course, I guess I'll just uninstall 24.04.1 and reinstall a discontinued LTS in order to get the imaging software to work and the thumbnails to show up on the desktop again. 

Just seemed odd to me that the latest version of Ubuntu using Nautilus was unable to thumbnail RAW images, when they have become even more prevalent these days than they were 5-12 years ago!

Thunar doesn't seem to suffer this problem either. Perhaps it is just the kernel iteration of this Gnome that is having issues with pixbuf-thumbnailer.

Ah well, thought ide ask the question anyway, and see if anyone was working on a solution to this issue. 

Thanks for your replies :)

---

### Post by Norm24 on 2024-11-09
So I take it using Thunar with tumbler and tumbler-plugins-extra was not a viable solution for you?

---

### Post by asherax on 2024-11-09
TBH Norm, I did try Thunar with Tumbler, and tumbler-plugins-extra and it worked fine, but although I quite like Thunar, I wanted to try an alternative, so I just did a flat install of Ubuntu Studio with all the bells and whistles, and decided to utilize Dolphin's file system, and have to say Im really liking Plasma these days. Everything just worked straight out of the box, and it is so configurable. Studio has come a long way, and is probably better suited to my needs in regards image processing, and film making. 

Gnome is a fine desktop, and its beautiful, but functionally I think KDE is just better suited to my needs at present. ORF's and NEF's work out of the box, thumbnails are better integrated with thumbs on folders to boot making it super easy to slow navigate, and programs like Digicam are radically faster and better integrated. GIMP, Rawtherapee, Darktable also all integrate perfectly making for a very streamlined imaging workflow for Raw Images. 

Just a flavour really... I used to love MATE and still do in a way, but Studio have really cracked it recently and its just effortless to use. Thinks like Da Vinci Resolve work basically out of the box, and Dolphin is such a lovely and configurable file manager. Perhaps it lacks some of the desktop bells and whistles of a Nautilus based Gnome, but I'm happy to compromise on the little things to have everything work together nicely without the need for a lot of time considerations aside from the creative work itself.

Thanks though, always good to interact with the community and see how things are going. We are all in it together! <3

---

### Post by 1fallen on 2024-11-09
+1 For Plasma6, I have become a 2 Desktop kind of user.
It's still hard for me to let XFCE go so I keep it on Two only systems, and the other 2 are Plasma6

---

### Post by Norm24 on 2024-11-09
> **asherax said:**
> TBH Norm, I did try Thunar with Tumbler, and tumbler-plugins-extra and it worked fine, but although I quite like Thunar, I wanted to try an alternative, so I just did a flat install of Ubuntu Studio with all the bells and whistles, and decided to utilize Dolphin's file system, and have to say Im really liking Plasma these days. Everything just worked straight out of the box, and it is so configurable. Studio has come a long way, and is probably better suited to my needs in regards image processing, and film making. 

Gnome is a fine desktop, and its beautiful, but functionally I think KDE is just better suited to my needs at present. ORF's and NEF's work out of the box, thumbnails are better integrated with thumbs on folders to boot making it super easy to slow navigate, and programs like Digicam are radically faster and better integrated. GIMP, Rawtherapee, Darktable also all integrate perfectly making for a very streamlined imaging workflow for Raw Images. 

Just a flavour really... I used to love MATE and still do in a way, but Studio have really cracked it recently and its just effortless to use. Thinks like Da Vinci Resolve work basically out of the box, and Dolphin is such a lovely and configurable file manager. Perhaps it lacks some of the desktop bells and whistles of a Nautilus based Gnome, but I'm happy to compromise on the little things to have everything work together nicely without the need for a lot of time considerations aside from the creative work itself.

Thanks though, always good to interact with the community and see how things are going. We are all in it together! <3

Nice!

I'm still a user of Mate to this day and it completely meets my daily use as a desktop user.

But with the wife upping her game when it comes to photography her current laptop is going to be getting a fresh install of Studio when she is ready.

---

