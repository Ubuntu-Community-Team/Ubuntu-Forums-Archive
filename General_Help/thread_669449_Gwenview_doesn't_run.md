---
title: "Gwenview doesn't run"
date: 2008-01-16
forum: General Help
---

### Post by mount_evans on 2008-01-16
I am running Ubuntu 7.10; since there is no letter in front of it, I assume it is the Gnome GUI.  I used Synaptic to install Gwenview.  It listed a bunch of KDE libraries that were needed, so I agreed to install
those as well.  The bar graphs did their thing, there were no error messages.  But when I execute Gwenview from the pulldown menu, nothing happens.  When I right click on a graphics file and ask to open it in Gwenview, nothing happens.  I did ps -u <myubuntuaccountname> to see if there were any Gwenview processes running in the background, but I didn't see anyting with Gwen in the name.

Any idea what I am missing?

---

### Post by p_quarles on 2008-01-16
Try running it from the terminal (the command is just "gwenview") and see what kind of error message you get.

---

### Post by mount_evans on 2008-01-16
> **p_quarles said:**
> Try running it from the terminal (the command is just "gwenview") and see what kind of error message you get.

OK, you asked for it...

kbuildsycoca running...
*** glibc detected *** gwenview: free(): invalid next size (fast): 0x080eb558 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d3fd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7d43800]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7f07d81]
/usr/lib/libstdc++.so.6(_ZdaPv+0x1d)[0xb7f07ddd]
/usr/lib/libqt-mt.so.3(_ZN11QStringDataD1Ev+0x34)[0xb6eacd30]
/usr/lib/libqt-mt.so.3(_ZN11QStringData10deleteSelfEv+0x23)[0xb6ea44b5]
/usr/lib/libgwenviewcore.so.1(_ZN7QStringD1Ev+0x41)[0xb7c7136f]
/usr/lib/libqt-mt.so.3(_ZN11QStringList5splitERK5QCharRK7QStringb+0x75)[0xb6eb63f5]
/usr/lib/libqt-mt.so.3(_ZN12QFontPrivate4loadEN5QFont6ScriptE+0x1c9)[0xb6aca7f3]
/usr/lib/libqt-mt.so.3(_ZNK12QFontPrivate15engineForScriptEN5QFont6ScriptE+0x50)[0xb6acc5a2]
======= Memory map: ========
08048000-08049000 r-xp 00000000 03:41 6625090    /usr/bin/gwenview
08049000-0804a000 rw-p 00000000 03:41 6625090    /usr/bin/gwenview
0804a000-080ef000 rw-p 0804a000 00:00 0          [heap]
b6000000-b6021000 rw-p b6000000 00:00 0 
b6021000-b6100000 ---p b6021000 00:00 0 
b618b000-b61f2000 r--s 00000000 03:41 7275134    /var/tmp/kdecache-pciszek/ksycoca
b61f2000-b61f7000 r-xp 00000000 03:41 6734428    /usr/lib/qt3/plugins/imageformats/libqmng.so
b61f7000-b61f8000 rw-p 00004000 03:41 6734428    /usr/lib/qt3/plugins/imageformats/libqmng.so
b61f8000-b6217000 r-xp 00000000 03:41 7275109    /usr/lib/kde3/plugins/styles/plastik.so
b6217000-b6218000 rw-p 0001e000 03:41 7275109    /usr/lib/kde3/plugins/styles/plastik.so
b6218000-b621e000 r--s 00000000 03:41 7193022    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b621e000-b6221000 r--s 00000000 03:41 7194247    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b6221000-b6225000 r--s 00000000 03:41 7194246    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b6225000-b6226000 r--s 00000000 03:41 7194245    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b6226000-b6229000 r--s 00000000 03:41 7192818    /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-x86.cache-2
b6229000-b622a000 r--s 00000000 03:41 7194244    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b622a000-b622d000 r--s 00000000 03:41 7194241    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b622d000-b622e000 r--s 00000000 03:41 7194240    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b622e000-b6234000 r--s 00000000 03:41 7192656    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6234000-b6236000 r--s 00000000 03:41 7194238    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6236000-b623e000 r--s 00000000 03:41 7194237    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b623e000-b6244000 r--s 00000000 03:41 7194235    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6244000-b6245000 r--s 00000000 03:41 7194176    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6245000-b6247000 r--s 00000000 03:41 7194175    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b6247000-b624d000 r--s 00000000 03:41 7194174    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b624d000-b6251000 r--s 00000000 03:41 7193007    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6251000-b6258000 r--s 00000000 03:41 7192653    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6258000-b6259000 r--s 00000000 03:41 7195557    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b6259000-b625a000 r--s 00000000 03:41 7195556    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b625a000-b625b000 r--s 00000000 03:41 7195555    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b625b000-b625e000 r--s 00000000 03:41 7195554    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b625e000-b6261000 r--s 00000000 03:41 7195553    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b6261000-b6263000 r-KCrash: Application 'gwenview' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
Alarm clock

---

### Post by p_quarles on 2008-01-16
Maybe it wasn't installed properly? Give this a try:
```
sudo dpkg-reconfigure gwenview
```
I like Gwenview myself, but there are a number of good image viewers that will work better with Gnome -- e.g., eye of gnome, gthumb, f-spot and so on.

---

### Post by mount_evans on 2008-01-16
> **p_quarles said:**
> 
I like Gwenview myself, but there are a number of good image viewers that will work better with Gnome -- e.g., eye of gnome, gthumb, f-spot and so on.

Do any of them allow you to easily browse through directories the way Gwenview does?

---

### Post by mount_evans on 2008-01-16
[QUOTE=p_quarles;4148869]Maybe it wasn't installed properly? Give this a try:
```
sudo dpkg-reconfigure gwenview
```

Doesn't seem to have made any difference.

---

### Post by p_quarles on 2008-01-16
I wonder if this could be related to your Compiz settings? Try turning Compiz off and running Gwenview again. To do so:
```
metacity --replace
```
To turn it back on:
```
compiz --replace
```

---

### Post by mount_evans on 2008-01-17
> **p_quarles said:**
> I wonder if this could be related to your Compiz settings? Try turning Compiz off and running Gwenview again. To do so:
```
metacity --replace
```
To turn it back on:
```
compiz --replace
```

Yikes.  Whatever each of these commands did, it didn't...finish.  After my screen went through convulsions, the teminal window sat there without a prompt, not accepting commands.  Did these commands do anything that a reboot can't erase?  I hope not.

---

### Post by p_quarles on 2008-01-17
Definitely not. Those commands only affect the current session. Since you didn't run them as root, they won't affect anything else. 

(what they do, btw, is change the window manager being used; normally it works fine, so not sure why your screen had a seizure)

---

