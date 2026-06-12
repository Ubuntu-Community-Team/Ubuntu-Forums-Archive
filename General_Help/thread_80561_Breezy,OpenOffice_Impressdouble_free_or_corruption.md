---
title: "Breezy,OpenOffice Impress:double free or corruption"
date: 2005-10-22
forum: General Help
---

### Post by arska on 2005-10-22
Hi,

After upgrading Horay->Breezy I get a nasty error with the Impress of  Openoffice.org2 (1.9.129-1ubuntu4) and openoffice.org(1.1.5-0ubuntu1).

It seems to happen when I try to view/visualize certain slide in my presentation which contains various small bitmap pictures. I'm not sure if that is the actual problem but it happens on the same slide.

It used to open well with OO 1.1.4 on Hoary, and I have confirmed it on other debian machine with OO1.1.4.

The error I get is 
*** glibc detected *** double free or corruption (fasttop): 0x085b5c18 ***
/usr/lib/openoffice2/program/soffice: line 224: 28833 Killed                  "$sd_prog/$sd_binary" "$@"


And with impress (1.1.5)
Fatal exception: Signal 11
Stack:
/usr/lib/openoffice/program/libsal.so.3[0xb72e23fe]
/usr/lib/openoffice/program/libsal.so.3[0xb72e258b]
/usr/lib/openoffice/program/libsal.so.3[0xb72e2656]
[0xffffe420]
/usr/lib/libX11.so.6[0xb6f49e48]
/usr/lib/libX11.so.6(XUnionRegion+0x115)[0xb6f4a5d9]
/usr/lib/libX11.so.6(XXorRegion+0x69)[0xb6f4b20a]
/usr/lib/openoffice/program/libvclplug_gen645li.so(_ZN14X11SalGraphics15drawPolyPolygonEmPKmPPK8SalPoint+0x13a)[0xb6037c04]
/usr/lib/openoffice/program/libvcl645li.so(_ZN11SalGraphics15DrawPolyPolygonEmPKmPPK8SalPointPK12OutputDevice+0x108)[0xb7edb590]
/usr/lib/openoffice/program/libvcl645li.so(_ZN12OutputDevice19ImplDrawPolyPolygonEtRK11PolyPolygon+0x348)[0xb7e6a706]
/usr/lib/openoffice/program/libvcl645li.so(_ZN12OutputDevice15DrawPolyPolygonERK11PolyPolygon+0x1e2)[0xb7e6e3d4]
/usr/lib/openoffice/program/libvcl645li.so(_ZN21MetaPolyPolygonAction7ExecuteEP12OutputDevice+0x29)[0xb7e54aa3]
/usr/lib/openoffice/program/libvcl645li.so(_ZN11GDIMetaFile4PlayEP12OutputDevicem+0x91)[0xb7e2dd6d]
/usr/lib/openoffice/program/libvcl645li.so(_ZN11GDIMetaFile4PlayEP12OutputDeviceRK5PointRK4Sizem+0x25b)[0xb7e2e003]
/usr/lib/openoffice/program/libgo645li.so(_ZN14GraphicManager8ImplDrawEP12OutputDeviceRK5PointRK4SizeRK11GDIMetaFileRK11GraphicAttr+0x1d8)[0xb2929424]
/usr/lib/openoffice/program/libgo645li.so(_ZN14GraphicManager16ImplCreateOutputEP12OutputDeviceRK5PointRK4SizeRK11GDIMetaFileRK11GraphicAttrmPS8_+0x365)[0xb2924a2d]
/usr/lib/openoffice/program/libgo645li.so(_ZN14GraphicManager8ImplDrawEP12OutputDeviceRK5PointRK4SizeR13GraphicObjectRK11GraphicAttrmRh+0x2c0)[0xb292367c]
/usr/lib/openoffice/program/libgo645li.so(_ZN14GraphicManager7DrawObjEP12OutputDeviceRK5PointRK4SizeR13GraphicObjectRK11GraphicAttrmRh+0x2d2)[0xb2923208]
/usr/lib/openoffice/program/libgo645li.so(_ZN13GraphicObject4DrawEP12OutputDeviceRK5PointRK4SizePK11GraphicAttrm+0x225)[0xb2920d15]
/usr/lib/openoffice/program/libsvx645li.so(_ZNK10SdrGrafObj5PaintER15ExtOutputDeviceRK15SdrPaintInfoRec+0x6da)[0xb363e652]
/usr/lib/openoffice/program/libsvx645li.so(_ZNK10SdrObjList5PaintER15ExtOutputDeviceRK15SdrPaintInfoRecit+0x8f4)[0xb36824ec]
/usr/lib/openoffice/program/libsvx645li.so(_ZNK10SdrObjList5PaintER15ExtOutputDeviceRK15SdrPaintInfoReci+0xe2)[0xb3681bc4]
/usr/lib/openoffice/program/libsvx645li.so(_ZNK11SdrObjGroup5PaintER15ExtOutputDeviceRK15SdrPaintInfoRec+0x5a)[0xb3644a8a]
/usr/lib/openoffice/program/libsvx645li.so(_ZNK10SdrObjList5PaintER15ExtOutputDeviceRK15SdrPaintInfoRecit+0x8f4)[0xb36824ec]
/usr/lib/openoffice/program/libsvx645li.so(_ZNK10SdrObjList5PaintER15ExtOutputDeviceRK15SdrPaintInfoReci+0xe2)[0xb3681bc4]
/usr/lib/openoffice/program/libsvx645li.so(_ZNK11SdrObjGroup5PaintER15ExtOutputDeviceRK15SdrPaintInfoRec+0x5a)[0xb3644a8a]
/usr/lib/openoffice/program/libsvx645li.so(_ZNK10SdrObjList5PaintER15ExtOutputDeviceRK15SdrPaintInfoRecit+0x8f4)[0xb36824ec]
/usr/lib/openoffice/program/libsvx645li.so(_ZNK10SdrObjList5PaintER15ExtOutputDeviceRK15SdrPaintInfoReci+0xe2)[0xb3681bc4]
/usr/lib/openoffice/program/libsvx645li.so(_ZNK11SdrObjGroup5PaintER15ExtOutputDeviceRK15SdrPaintInfoRec+0x5a)[0xb3644a8a]
/usr/lib/openoffice/program/libsvx645li.so(_ZNK10SdrObjList5PaintER15ExtOutputDeviceRK15SdrPaintInfoRecit+0x8f4)[0xb36824ec]
/usr/lib/openoffice/program/libsvx645li.so(_ZNK10SdrObjList5PaintER15ExtOutputDeviceRK15SdrPaintInfoReci+0xe2)[0xb3681bc4]
/usr/lib/openoffice/program/libsvx645li.so(_ZN11SdrPageView10InitRedrawEP12OutputDeviceRK6RegiontPK4Link+0x89a)[0xb368d4e4]
/usr/lib/openoffice/program/libsvx645li.so(_ZN12SdrPaintView10InitRedrawEP12OutputDeviceRK6Regiont+0x6a)[0xb369493c]
/usr/lib/openoffice/program/libsd645li.so[0xb0b9241b]
/usr/lib/openoffice/program/libsd645li.so[0xb0bedbb5]
/usr/lib/openoffice/program/libsd645li.so[0xb0bc0c70]
/usr/lib/openoffice/program/libsd645li.so[0xb0bafe90]
/usr/lib/openoffice/program/libvcl645li.so(_ZN6Window13ImplCallPaintEPK6Regiont+0x3a3)[0xb7f30f33]
/usr/lib/openoffice/program/libvcl645li.so(_ZN6Window13ImplCallPaintEPK6Regiont+0x465)[0xb7f30ff5]
/usr/lib/openoffice/program/libvcl645li.so(_ZN6Window13ImplCallPaintEPK6Regiont+0x465)[0xb7f30ff5]
/usr/lib/openoffice/program/libvcl645li.so(_ZN6Window13ImplCallPaintEPK6Regiont+0x465)[0xb7f30ff5]
/usr/lib/openoffice/program/libvcl645li.so(_ZN6Window13ImplCallPaintEPK6Regiont+0x465)[0xb7f30ff5]
/usr/lib/openoffice/program/libvcl645li.so(_ZN6Window13ImplCallPaintEPK6Regiont+0x465)[0xb7f30ff5]
/usr/lib/openoffice/program/libvcl645li.so(_ZN6Window13ImplCallPaintEPK6Regiont+0x465)[0xb7f30ff5]
/usr/lib/openoffice/program/libvcl645li.so(_ZN6Window20ImplCallOverlapPaintEv+0x5f)[0xb7f3110f]
/usr/lib/openoffice/program/libvcl645li.so(_ZN6Window18ImplHandlePaintHdlEPv+0x2c)[0xb7f311a4]
/usr/lib/openoffice/program/libvcl645li.so(_ZN6Window26LinkStubImplHandlePaintHdlEPvS0_+0x26)[0xb7f31170]
/usr/lib/openoffice/program/libvcl645li.so(_ZN5Timer7TimeoutEv+0x1f)[0xb7dfa4db]
/usr/lib/openoffice/program/libvcl645li.so(_Z21ImplTimerCallbackProcv+0x83)[0xb7dfa1e3]
/usr/lib/openoffice/program/libvclplug_gen645li.so(_ZNK7SalData7TimeoutEv+0x2e)[0xb60561ea]
/usr/lib/openoffice/program/libvclplug_gen645li.so(_ZN7SalXLib12CheckTimeoutEb+0xe1)[0xb6055d83]
/usr/lib/openoffice/program/libvclplug_gen645li.so(_ZN7SalXLib5YieldEh+0x29f)[0xb6056033]
/usr/lib/openoffice/program/libvclplug_gen645li.so(_ZN14X11SalInstance5YieldEh+0x31)[0xb605eb47]
/usr/lib/openoffice/program/libvcl645li.so(_ZN11Application5YieldEv+0x64)[0xb7df47f6]
/usr/lib/openoffice/program/libvcl645li.so(_ZN11Application7ExecuteEv+0x35)[0xb7df4703]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0x1f44)[0x8065b38]
/usr/lib/openoffice/program/libvcl645li.so(_Z6SVMainv+0x4a)[0xb7df9608]
/usr/lib/openoffice/program/libvcl645li.so(main+0x4c)[0xb7fad3c0]
/lib/tls/libc.so.6(__libc_start_main+0xd4)[0xb6c34eb4]
/usr/lib/openoffice/program/soffice.bin(_ZN6Window11RequestHelpERK9HelpEvent+0x31)[0x805e131]
Aborted


Thanx in advance,

---

### Post by emperon on 2005-10-22
I had a similar error. After seaching i realized that my CD burning process went wrong and Open Office package was defected. This may or may not be the issue for you but i suggest you to check out the checksum for each package on the CD. There's a checksum file in the CD that you can compare all with a single command.

---

### Post by arska on 2005-10-22
Actually, I upgraded it from the Net.
At this moment I reinstalled from the CD ISO and the same problem persists :confused: 
I tried it also unde XFCE4 and same thing. I tend to suspect the Hoary itself....

---

### Post by karora on 2005-11-13
Hi,

I similarly see this error in OpenOffice.org 1.129 and 2.0.0 on Breezy.  It tends to happen for me either (a) after using writer for some time (but without saving or modifying the document) or (b) when I try to save the document.

OpenOffice is the only application I have seen this in so far.  This was a clean install of Breezy onto a brand new laptop.

Thanks.

---

### Post by steffen on 2005-11-23
This has suddenly started happening to me as well over the last week. I'm actually not able to save any Word .doc files as .odt - every time I try, openoffice freezes with:
***> *** glibc detected *** double free or corruption (fasttop): 0x086864b8 ***

I tried updating OOo2 to the official 2.0 version, and I also tried downloading StarOffice 8. Same problem every time.

This is a clean desktop install of Breezy (Gnome). Haven't had any trouble like this with it until a week ago.

When OOo2 freezes, I kill it, and it exits with error:
> /usr/lib/openoffice2/program/soffice: line 224:  4830 Killed                  "$sd_prog/$sd_binary" "$@"

---

### Post by gyrev on 2005-12-12
I managed this issue with:
```
export MALLOC_CHECK_=2
```
also, it looks like you have to launch OOo through command line, not the menu icons.
I have to do the export stuff every day, I don't know how to have it done automatically at the start up...

---

### Post by WoodyDragon on 2005-12-19
[QUOTE=gyrev]I managed this issue with:
```
export MALLOC_CHECK_=2
```
also, it looks like you have to launch OOo through command line, not the menu icons.
I have to do the export stuff every day, I don't know how to have it done automatically at the start up...[/QUOTE]


Thanks, I'll try that today, because my OO2 Impress freezes whenever I try to write something onto a sheet.

For the export thingie, you must put it into ".bash_profile" or ".bashrc" to have it set on user-login (kde-start)

---

### Post by SyncMaster on 2005-12-20
Super!
Using the malloc (and starting from a shell ) works for me as well. I already thought i can not use Impress as mostly all the bigger PPTs crashed,
Thanks a lot

---

### Post by Canguçu on 2005-12-23
Same here. I was already suspecting my hardware was dying, but it is indeed a OpenOffice bug. That Malloc hack worked, but the fact a major desktop app - shiped on default installation - needs that kind of hack worries me :(

---

### Post by deja-vix on 2006-01-29
[QUOTE=WoodyDragon]Thanks, I'll try that today, because my OO2 Impress freezes whenever I try to write something onto a sheet.

For the export thingie, you must put it into ".bash_profile" or ".bashrc" to have it set on user-login (kde-start)[/QUOTE]

I've managed to run openoffice even from the GNOME menus:

1) create /usr/local/bin/soffice, put:
export MALLOC_CHECK_=2
/usr/bin/soffice $*

2) save, chmod 755
3) ln -s /usr/local/bin/soffice /usr/local/bin/openoffice.org-2.0

If you have /usr/local/bin in your PATH, OOo will run just fine, even when run from the menu (GNOME runs OOo as "openoffice.org-2.0" without specifying full path.

You may need to relogin to your GNOME.

Regards,
Ivan

---

### Post by am4c130d on 2006-05-20
You people are gods!  This little fix probably saved my marriage :D 

The only thing I can offer back is that you can add the MALLOC statement to /usr/bin/openoffice.org-2.0 directly - it's just a borne script.  

Mine now reads

#!/bin/sh
export MALLOC_CHECK_=2
exec /etc/openoffice.org-2.0/program/soffice "$@"

and everything works as it should.

I'm not convinced it's a OOo issue.  I have one PC, running Ubuntu Breezy that needed this, using the latest OOo 2.0.2 from OOo's website (aliened the rpm's - no issues, and not a beta version like 1.9.129), another running Dapper with no issues and a third running XP again with no issues.  All using 2.0.2...

Anyway, thanks!

Alan

---

### Post by deja-vix on 2006-05-20
Hi,

I did my own scripts just for the case I will upgrade OOo, which is certainly what I will do :-) So it won't overwrite my work.

Regards,
IVan

---

### Post by dragibusds on 2007-11-23
Dear all,

I had the same problem and following instruction at the following link I've solved it:

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/153173](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/153173)

I hope it will help.

Regards,
Dragibus

---

