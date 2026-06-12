---
title: "Skype can't startup on edgy"
date: 2006-11-29
forum: General Help
---

### Post by aubrey on 2006-11-29
I fllowed "Unofficial Ubuntu 6.10 (Edgy Eft) Starter Guide" to install skype. And when I start it in the terminal, I got the following error:
=====================================================
aubrey@ubuntu-edgy:~$ skype
*** glibc detected *** skype: free(): invalid pointer: 0x08a64f28 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb740e8bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb740ea44]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb71cdfc1]
/usr/lib/libstdc++.so.6(_ZNSs4_Rep10_M_destroyERKSaIcE+0x1d)[0xb71aad3d]
/usr/lib/libscim-1.0.so.8[0xb6d91633]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xb6d928c7]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xb6d8d0c5]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim23QScimInputContextGlobal10initializeEv+0x257)[0xb6e2ccf7]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim17QScimInputContextC1Ev+0x31e)[0xb6e2eace]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN22ScimInputContextPlugin6createERK7QString+0x7e)[0xb6e27cae]
/usr/lib/libqt-mt.so.3(_ZN26QInputContextPluginPrivate6createERK7QString+0x25)[0xb7bc501f]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0x94)[0xb7bc4bec]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext17changeInputMethodE7QString+0xc3)[0xb6f4f85b]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext5slaveEv+0x43)[0xb6f4fa0f]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext15setHolderWidgetEP7QWidget+0x26)[0xb6f4fc7e]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0xb8)[0xb7bc4c10]
/usr/lib/libqt-mt.so.3(_ZN7QWidget18createInputContextEv+0x8f)[0xb7917a8d]
/usr/lib/libqt-mt.so.3(_ZN7QWidget17resetInputContextEv+0x1d)[0xb7917d93]
/usr/lib/libqt-mt.so.3(_ZN9QLineEdit7setTextERK7QString+0x1d)[0xb7a9819d]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setLineEditEP9QLineEdit+0x82)[0xb7a5f49e]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox13setUpLineEditEv+0x60)[0xb7a59d68]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setEditableEb+0x67)[0xb7a5d021]
skype[0x81944a7]
skype[0x8078989]
skype[0x8075972]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb73bd8cc]
skype(_ZN6QFrame10paintEventEP11QPaintEvent+0x6d)[0x806f7b1]
======= Memory map: ========
08048000-08988000 rwxp 00000000 08:02 588941     /usr/bin/skype
08988000-08a7a000 rw-p 08988000 00:00 0          [heap]
b6b00000-b6b21000 rw-p b6b00000 00:00 0 
b6b21000-b6c00000 ---p b6b21000 00:00 0 
b6cf8000-b6d03000 r-xp 00000000 08:02 638425     /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6d03000-b6d04000 rw-p 0000a000 08:02 638425     /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6d04000-b6d28000 r-xp 00000000 08:02 638424     /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6d28000-b6d29000 rw-p 00024000 08:02 638424     /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6d29000-b6dfe000 r-xp 00000000 08:02 591001     /usr/lib/libscim-1.0.so.8.1.0
b6dfe000-b6e0c000 rw-p 000d5000 08:02 591001     /usr/lib/libscim-1.0.so.8.1.0
b6e0c000-b6e0e000 r-xp 00000000 08:02 591005     /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6e0e000-b6e0f000 rw-p 00001000 08:02 591005     /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6e19000-b6e37000 r-xp 00000000 08:02 639293     /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6e37000-b6e38000 rw-p 0001e000 08:02 639293     /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6e38000-b6e3c000 r-xp 00000000 08:02 638423     /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6e3c000-b6e3d000 rw-p 00003000 08:02 638423     /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6e3d000-b6eae000 r--p 00000000 08:02 752346     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6eae000-b6ed8000 r-xp 00000000 08:02 590851     /usr/lib/liblcms.so.1.0.15
b6ed8000-b6ed9000 rw-p 00029000 08:02 590851     /usr/lib/liblcms.so.1.0.15
b6ed9000-b6edc000 rw-p b6ed9000 00:00 0 
b6edc000-b6f47000 r-xp 00000000 08:02 590882     /usr/lib/libmng.so.1.1.0.9
b6f47000-b6f4a000 rw-p 0006a000 08:02 590882     /usr/lib/libmng.so.1.1.0.9
b6f4a000-b6f53000 r-xp 00000000 08:02 638422     /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6f53000-b6f54000 rw-p 00008000 08:02 638422     /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6f54000-b6f59000 r-xp 00000000 08:02 638420     /usr/lib/qt3/plugins/imageformats/libqmng.so
b6f59000-b6f5a000 rw-p 00004000 08:02 638420     /usr/lib/qt3/plugins/imageformats/libqmng.so
b6f5a000-b6f5b000 ---p b6f5a000 00:00 0 
b6f5b000-b6fdb000 rw-p b6f5b000 00:00 0 
b6fdb000-b6fdc000 r-xp 00000000 08:02 621519     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b6fdc000-b6fdd000 rw-p 00000000 08:02 621519     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b6fdd000-b7010000 r--p 00000000 08:02 639075     /usr/lib/locale/en_US.utf8/LC_CTYPE
b7010000-b7011000 r--p 00000000 08:02 639080     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7011000-b7012000 r--p 00000000 08:02 639083     /usr/lib/locale/en_US.utf8/LC_TIME
b7012000-b70e9000 r--p 00000000 08:02 639074     /usr/lib/locale/en_US.utf8/LC_COLLATE
b70e9000-b70ea000 r--p 00000000 08:02 639078     /usr/lib/locale/en_US.utf8/LC_MONETARY
b70ea000-b70eb000 r--p 00000000 08:02 654147     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b70eb000-b70ec000 r--p 00000000 08:02 639081     /usr/lib/locale/en_US.utf8/LC_PAPER
b70ec000-b70ed000 r--p 00000000 08:02 639079     /usr/lib/locale/en_US.utf8/LC_NAME
b70ed000-b70ee000 r--p 00000000 08:02 639073     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b70ee000-b70f1000 rw-p b70ee000 00:00 0 
b70f1000-b70f5000 r-xp 00000000 08:02 590374     /usr/lib/libXfixes.so.3.1.0
b70f5000-b70f6000 rw-p 00003000 08:02 590374     /usr/lib/libXfixes.so.3.1.0
b70f6000-b7112000 r-xp 00000000 08:02 590553     /usr/lib/libexpat.so.1.0.0
b7112000-b7114000 rw-p 0001c000 08:02 590553     /usr/lib/libexpat.so.1.0.0
b7114000-b7118000 r-xp 00000000 08:02 590368     /usr/lib/libXdmcp.so.6.0.0
b7118000-b7119000 rw-p 00003000 08:02 590368     /usr/lib/libXdmcp.so.6.0.0
b7119000-b711b000 r-xp 00000000 08:02 590359     /usr/lib/libXau.so.6.0.0
b711b000-b711c000 rw-p 00001000 08:02 590359     /usr/lib/libXau.so.6.0.0
b711c000-b711d000 rw-p b711c000 00:00 0 
b711d000-b71f1000 r-xp 00000000 08:02 591042     /usr/lib/libstdc++.so.6.0.8
b71f1000-b71f4000 r--p 000d4000 08:02 591042     /usr/lib/libstdc++.so.6.0.8
b71f4000-b71f6000 rw-p 000d7000 08:02 591042     /usr/lib/libstdc++.so.6.0.8
b71f6000-b71fc000 rw-p b71f6000 00:00 0 
b71fc000-b7211000 r-xp 00000000 08:02 590331     /usr/lib/libICE.so.6.3.0
b7211000-b7212000 rw-p 00014000 08:02 590331     /usr/lib/libICE.so.6.3.0
b7212000-b7214000 rw-p b7212000 00:00 0 
b7214000-b721c000 r-xp 00000000 08:02 590349     /usr/lib/libSM.so.6.0.0
b721c000-b721d000 rw-p 00007000 08:02 590349     /usr/lib/libSM.so.6.0.0
b721d000-b7284000 r-xp 00000000 08:02 590569     /usr/lib/libfreetype.so.6.3.10
b7284000-b7287000 rw-p 00067000 08:02 590569     /usr/lib/libfreetype.so.6.3.10
b7287000-b7298000 r-xp 00000000 08:02 590378     /usr/lib/libXft.so.2.1.2
b7298000-b7299000 rw-p 00010000 08:02 590378     /usr/lib/libXft.so.2.1.2
b7299000-b729b000 r-xp 00000000 08:02 590382     /usr/lib/libXinerama.so.1.0.0
b729b000-b729c000 rw-p 00001000 08:02 590382     /usr/lib/libXinerama.so.1.0.0
b729c000-b729d000 rw-p b729c000 00:00 0 
b729d000-b72a5000 r-xp 00000000 08:02 590364     /usr/lib/libXcursor.so.1.0.2
b72a5000-b72a6000 rw-p 00007000 08:02 590364     /usr/lib/libXcursor.so.1.0.2
b72a6000-b72a8000 r-xp 00000000 08:02 590392     /usr/lib/libXrandr.so.2.0.0
b72a8000-b72a9000 rw-p 00002000 08:02 590392     /usr/lib/libXrandr.so.2.0.0
b72a9000-b72b0000 r-xp 00000000 08:02 590394     /usr/lib/libXrender.so.1.3.0
b72b0000-b72b1000 rw-p 00006000 08:02 590394     /usr/lib/libXrender.so.1.3.0
b72b1000-b72b8000 r-xp 00000000 08:02 590380     /usr/lib/libXi.so.6.0.0
b72b8000-b72b9000 rw-p 00006000 08:02 590380     /usr/lib/libXi.so.6.0.0
b72b9000-b72cc000 r-xp 00000000 08:02 591099     /usr/lib/libz.so.1.2.3
b72cc000-b72cd000 rw-p 00012000 08:02 591099     /usr/lib/libz.so.1.2.3
b72cd000-b72f0000 r-xp 00000000 08:02 588757     /usr/lib/libpng12.so.0.1.2.8
b72f0000-b72f1000 rw-p 00023000 08:02 588757     /usr/lib/libpng12.so.0.1.2.8
b72f1000-b72f2000 rw-p b72f1000 00:00 0 
b72f2000-b7310000 r-xp 00000000 08:02 590835     /usr/lib/libjpeg.so.62.0.0
b7310000-b7311000 rw-p 0001d000 08:02 590835     /usr/lib/libjpeg.so.62.0.0
b7311000-b735b000 r-xp 00000000 08:02 590398     /usr/lib/libXt.so.6.0.0
b735b000-b735f000 rw-p 00049000 08:02 590398     /usr/lib/libXt.so.6.0.0
b735f000-b7374000 r-xp 00000000 08:02 590435     /usr/lib/libaudio.so.2.4
b7374000-b7375000 rw-p 00014000 08:02 590435     /usr/lib/libaudio.so.2.4
b7375000-b739e000 r-xp 00000000 08:02 590559     /usr/lib/libfontconfig.so.1.0.4
b739e000-b73a3000 rw-p 00028000 08:02 590559     /usr/lib/libfontconfig.so.1.0.4
b73a3000-b73a4000 rw-p b73a3000 00:00 0 
b73a4000-b73a6000 r-xp 00000000 08:02 589059     /lib/tls/i686/cmov/libdl-2.4.so
b73a6000-b73a8000 rw-p 00001000 08:02 589059     /lib/tls/i686/cmov/libdl-2.4.so
b73a8000-b74d5000 r-xp 00000000 08:02 589053     /lib/tls/i686/cmov/libc-2.4.so
b74d5000-b74d7000 r--p 0012c000 08:02 589053     /lib/tls/i686/cmov/libc-2.4.so
b74d7000-b74d9000 rw-p 0012e000 08:02 589053     /lib/tls/i686/cmov/libc-2.4.so
b74d9000-b74dd000 rw-p b74d9000 00:00 0 
b74dd000-b74e7000 r-xp 00000000 08:02 556035     /lib/libgcc_s.so.1
b74e7000-b74e8000 rw-p 00009000 08:02 556035     /lib/libgcc_s.so.1
b74e8000-b750c000 r-xp 00000000 08:02 589061     /lib/tls/i686/cmov/libm-2.4.so
b750c000-b750e000 rw-p 00023000 08:02 589061     /lib/tls/i686/cmov/libm-2.4.so
b750e000-b75be000 r-xp 00000000 08:02 591040     /usr/lib/libstdc++.so.5.0.7
b75be000-b75c3000 rw-p 000af000 08:02 591040     /usr/lib/libstdc++.so.5.0.7
b75c3000-b75c8000 rw-p b75c3000 00:00 0 
b75c8000-b75d7000 r-xp 00000000 08:02 589079     /lib/tls/i686/cmov/libpthread-2.4.so
b75d7000-b75d9000 rw-p 0000f000 08:02 589079     /lib/tls/i686/cmov/libpthread-2.4.so
b75d9000-b75db000 rw-p b75d9000 00:00 0 
b75db000-b76a1000 r-xp 00000000 08:02 590353     /usr/lib/libX11.so.6.2.0
b76a1000-b76a4000 rw-p 000c5000 08:02 590353     /usr/lib/libX11.so.6.2.0
b76a4000-b76b0000 r-xp 00000000 08:02 590372     /usr/lib/libXext.so.6.4.0
b76b0000-b76b1000 rw-p 0000c000 08:02 590372     /usr/lib/libXext.so.6.4.0
b76b1000-b76b2000 rw-p b76b1000 00:00 0 
b76b2000-b7e47000 r-xp 00000000 08:02 588767     /usr/lib/libqt-mt.so.3.3.6
b7e47000-b7e8e000 rw-p 00794000 08:02 588767     /usr/lib/libqt-mt.so.3.3.6
b7e8e000-b7e91000 rw-p b7e8e000 00:00 0 
b7e91000-b7f44000 r-xp 00000000 08:02 590422     /usr/lib/libasound.so.2.0.0
b7f44000-b7f49000 rw-p 000b2000 08:02 590422     /usr/lib/libasound.so.2.0.0
b7f49000-b7f50000 r-xp 00000000 08:02 589083     /lib/tls/i686/cmov/librt-2.4.so
b7f50000-b7f52000 rw-p 00006000 08:02 589083     /lib/tls/i686/cmov/librt-2.4.so
b7f52000-b7f53000 r--p 00000000 08:02 639082     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f53000-b7f54000 r--p 00000000 08:02 639077     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f54000-b7f5b000 r--s 00000000 08:02 670667     /usr/lib/gconv/gconv-modules.cache
b7f5b000-b7f5c000 r--p 00000000 08:02 639076     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f5c000-b7f5e000 rw-p b7f5c000 00:00 0 
b7f5e000-b7f77000 r-xp 00000000 08:02 555990     /lib/ld-2.4.so
b7f77000-b7f79000 rw-p 00018000 08:02 555990     /lib/ld-2.4.so
bfb4f000-bfb65000 rw-p bfb4f000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Aborted (core dumped)
====================================================

Any clue are really appreciated!

Thanks,
-Aubrey

PS: oh, need to mention, I'm using beryl + XGL session.

---

### Post by LLRNR on 2006-11-29
Hi, if I get it correctly you installed Skype from [here](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Messenger_.28Skype.29), am I right? Which method did you use, the first or the second ?

If you used the second one, then you might simply try *sudo apt-get remove skype* and try the first method.

If you used the first method, you can try *sudo dpkg -r ExactNameOfSkypePackage* and then try the second method.

LLRNR

---

### Post by aubrey on 2006-11-29
Thanks for your clue. 
Yes, I followed that guide. But both methods are failed. They are using the same version, so, they were supposed to be the same, weren't they?
Any suggestion?

Thanks,
-Aubrey

---

### Post by LLRNR on 2006-11-30
First, do your best to remove what you (partially) installed.

Then: [http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/) and get the .deb package :mrgreen:

```
sudo dpkg -i NameOfPackage.deb
```

If this doesn't work either... I'm sorry but I can't think of anything else.

Good luck!

LLRNR

---

### Post by Charlie91 on 2006-12-02
I just saw your message (Aubrey).  As someone suggested you have to remove your Skype (may have to open your Synaptic Package Manager, go to your Skype entry and Remove or uninstall it from there).  Now you have to install the package [COLOR="Magenta"]libqt3-mt[/COLOR] also from Synaptic.  Download the DEB package from Skype (mentioned in the other replies) site.  Then open your console, go to the directory where you placed the downloaded file, and type: sudo dpkg -i PakageName.deb.

In other words, Skype needs libqt3-mt.  I hope that helps.

---

### Post by lpuente on 2006-12-02
Hi:
I'm still having trouble launching Skype, even after following all these instructions (all replies with installation info).  What I get after running Skype from Terminal is:
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Aborted (core dumped)

Any ideas?  I'm running Edgy 6.10, have Beryl, XGL installed. Skype was running fine, then all of a sudden, after installing who knows what, Skype never wanted to launch again...

Thank you.

Luis Puente

-------------------------
> **Charlie91 said:**
> I just saw your message (Aubrey).  As someone suggested you have to remove your Skype (may have to open your Synaptic Package Manager, go to your Skype entry and Remove or uninstall it from there).  Now you have to install the package [COLOR="Magenta"]libqt3-mt[/COLOR] also from Synaptic.  Download the DEB package from Skype (mentioned in the other replies) site.  Then open your console, go to the directory where you placed the downloaded file, and type: sudo dpkg -i PakageName.deb.

In other words, Skype needs libqt3-mt.  I hope that helps.

---

### Post by LLRNR on 2006-12-02
Hi, I run Skype on Edgy with no problems at all, even after installing Beryl. If you think its installation got corrupted in any way, you might try to un-install it first and then re-install it (of course, it depends on the method you used to initially install it). Another thing: instead of running it from the terminal, hit Alt+F2 first (if you're using Gnome or KDE) and launch it from there... it's "safer" ?! Not sure, but I noticed many things that are launched through the terminal return different errors, so I think you should try to launch most apps through the "Run" command (Alt+F2).

LLRNR

---

### Post by ichigo on 2006-12-13
Hi,

I have exactly the same problem with skype. I think there may be a conflict with SCIM. Your error message suggested that you have it installed. I am also using SCIM and remember that there has been some problem with SCIM and Skype once...
But I am sorry I don't know how to solve this problem and to be able to use both afterwards.

---

### Post by ffurlanete on 2007-01-09
If you want to use an input method other than the default with KDE/QT apps, I suggest you to use uim instead of scim/skim. It runs smoothly with skype and doesn't confuse the system's use of utf-8 chars (like 'ç').

Install the packages: im-switch, uim, uim-anthy
Then run: im-switch -s uim-systray

best regards

---

