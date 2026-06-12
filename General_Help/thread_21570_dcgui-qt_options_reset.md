---
title: "dcgui-qt options reset"
date: 2005-03-22
forum: General Help
---

### Post by NeoChaosX on 2005-03-22
Just installed dcgui-qt from universe, and I'm having trouble getting it to work. Everytime it starts, the windows resizes itself to a really weird shape, and a lot of the images in the program are broken (replaced by images of ghosts). Also, all the preferences I set from the last use of the program have been reset to blanks for some reason.

When I start the program from the command line, I get these errors:

```
I/O warning : failed to load external entity "/home/nael/.dc//emoticons.xml"
I/O warning : failed to load external entity "/icons/emot/default/emoticons.xml"I/O warning : failed to load external entity "/home/nael/.dc/dcprof.cfg"
I/O warning : failed to load external entity "/home/nael/.dc/dchub.cfg"
CListenManager: start listen
QFont::fromString: invalid description '(null)'
Can't set empty themeCXml::xml_UTF8Toisolat1 error 1
CXml::xml_UTF8Toisolat1 error 5
CXml::xml_UTF8Toisolat1 error 5
CXml::xml_UTF8Toisolat1 error 5
I/O warning : failed to load external entity "/home/nael/.dc/dcfriendlist.cfg"
CHTTP: HOST : 'dcgui.berlios.de:80'
CHTTP: URL  : '/update.xml'

```

Before all that, there's a seemingly infinite amount of "CXmlxml_UTF8Toisolat1 error 5" errors that the board won't let me post.

Does anyone know what's going on?

EDIT: Okay, now noticing a pattern. If I close the program and delete the ~/.dc folder, it'll go back to normal and I can configure stuff again. However, once I close it, then reopen the program, everything messes up again. This is really weird.

---

### Post by earobinson on 2005-04-01
[QUOTE=NeoChaosX]Just installed dcgui-qt from universe, and I'm having trouble getting it to work. Everytime it starts, the windows resizes itself to a really weird shape, and a lot of the images in the program are broken (replaced by images of ghosts). Also, all the preferences I set from the last use of the program have been reset to blanks for some reason.

When I start the program from the command line, I get these errors:

```
I/O warning : failed to load external entity "/home/nael/.dc//emoticons.xml"
I/O warning : failed to load external entity "/icons/emot/default/emoticons.xml"I/O warning : failed to load external entity "/home/nael/.dc/dcprof.cfg"
I/O warning : failed to load external entity "/home/nael/.dc/dchub.cfg"
CListenManager: start listen
QFont::fromString: invalid description '(null)'
Can't set empty themeCXml::xml_UTF8Toisolat1 error 1
CXml::xml_UTF8Toisolat1 error 5
CXml::xml_UTF8Toisolat1 error 5
CXml::xml_UTF8Toisolat1 error 5
I/O warning : failed to load external entity "/home/nael/.dc/dcfriendlist.cfg"
CHTTP: HOST : 'dcgui.berlios.de:80'
CHTTP: URL  : '/update.xml'

```

Before all that, there's a seemingly infinite amount of "CXmlxml_UTF8Toisolat1 error 5" errors that the board won't let me post.

Does anyone know what's going on?

EDIT: Okay, now noticing a pattern. If I close the program and delete the ~/.dc folder, it'll go back to normal and I can configure stuff again. However, once I close it, then reopen the program, everything messes up again. This is really weird.[/QUOTE]
 I get the same problem, anyone got a working version of DC?

---

### Post by NeoChaosX on 2005-04-01
What a coincedence.

I managed to find two Sarge debs of dclib and Valknut 0.3.7 (which dcgui-qt become) that work just fine in Hoary shortly after creating this thread.  The site they're on is here: [http://peppesbodega.nu/turban/index.php?section=images&path=Debian%20Packages/Apps/Valknut](http://peppesbodega.nu/turban/index.php?section=images&path=Debian%20Packages/Apps/Valknut)

Download both dclib and valknut. Remember to remove the libdc package before installing dclib since they're different versions of the same package. Also make sure you have libqt3c102-mt installed as well.

---

### Post by earobinson on 2005-04-01
[QUOTE=NeoChaosX]What a coincedence.

I managed to find two Sarge debs of dclib and Valknut 0.3.7 (which dcquit-qt become) that work just fine in Hoary shortly after creating this thread.  The site they're on is here: [http://peppesbodega.nu/turban/index.php?section=images&path=Debian%20Packages/Apps/Valknut](http://peppesbodega.nu/turban/index.php?section=images&path=Debian%20Packages/Apps/Valknut)

Download both dclib and valknut. Remember to remove the libdc package before installing dclib since they're different versions of the same package. Also make sure you have libqt3c102-mt installed as well.[/QUOTE]
 got this error

```
root@user78-213:/home/earobinson/Desktop/temp # dpkg -i dclib_0.3.7-0quickpackage_i386.deb
Selecting previously deselected package dclib.
(Reading database ... 67933 files and directories currently installed.)
Unpacking dclib (from dclib_0.3.7-0quickpackage_i386.deb) ...
dpkg: error processing dclib_0.3.7-0quickpackage_i386.deb (--install):
 trying to overwrite `/usr/lib/libdc.so.0.0.1', which is also in package libdc0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 dclib_0.3.7-0quickpackage_i386.deb
```

---

### Post by NeoChaosX on 2005-04-01
I repeat, 

[quote=NeoChaosX]Remember to remove the libdc package before installing dclib since they're different versions of the same package.[/quote]

The dclib 0.3.7 deb is conflicting with libdc0. Remove libdc0, and then you'll have no trouble.

---

### Post by unkwn on 2005-04-02
same thing for me with dcgui-qt, and i can't for the life of me get dctc/dcgui to work either. guess I'll give this a go. thanks for the link.

---

### Post by earobinson on 2005-04-02
[QUOTE=NeoChaosX]I repeat, 



The dclib 0.3.7 deb is conflicting with libdc0. Remove libdc0, and then you'll have no trouble.[/QUOTE]
 Sorry for being so stupid, any idea why no backports work for DC?

---

### Post by DCBA25 on 2005-04-06
[QUOTE=NeoChaosX]I repeat, 



The dclib 0.3.7 deb is conflicting with libdc0. Remove libdc0, and then you'll have no trouble.[/QUOTE]

Sorry, for beeing a newbie to ubuntu/debian....
How can i uninstall dclib?
When i run apt-get remove dclib i get a message saying that i allready removed it.

But when i try to install  *dpkg -i dclib_0.3.7-0quickpackage_i386.deb* i get the same error as above...

Please help me. I need DC....

---

### Post by DCBA25 on 2005-04-06
Sorry, it was just a typing mistake!

Allthought i had one error from that package. I changed the connection from passive to active while it was hashing files and it crashed.
I turned off hashing (for a while) and went just fine!
Thx!

---

### Post by Elcoco on 2005-04-19
ive been getting the same message on dcgui-qt and i tried installing valknut and dclib  and i get an error with valknut, i cant see what the first one is cuz i get a loop of listen on socket messages. ive also tried replacing libdc0 with dclib and dcgui-qt with valknut but i get the same error as with dcgui-qt

---

### Post by rejser on 2005-04-27
Anyone know where I can get the newer dclib and valknut when peppesbodega.nu ain't working?

---

### Post by jnk on 2005-06-01
well, i installed these two packages, but after i restart valknut my settings are gone...
the darn thing just wont keep my settings... =( how to fix.?

---

### Post by qki on 2005-06-24
I have the same problem with valknut or dcgui-qt settings - every time after restart.
Waiting for help...

---

### Post by tpls on 2005-10-01
Has somebody found a solution for this problem?

---

