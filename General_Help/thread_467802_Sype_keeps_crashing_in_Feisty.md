---
title: "Sype keeps crashing in Feisty"
date: 2007-06-08
forum: General Help
---

### Post by thikrat on 2007-06-08
Hello,

I had skype working in Ubuntu for a while there and then all of a sudden it just stopped loading, so i went to the command line and tried to run it manually and got this.  Sorry but I have no idea what this could possibly mean and i searched on the net and in the forums, nobody seems to have a skype crashing error!  I tried to install skype manually with the .deb and with automatix2, same thing happened to both.


$ skype
*** glibc detected *** skype: free(): invalid pointer: 0x08a3e8e0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb73547cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7357e30]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7109d11]
/usr/lib/libstdc++.so.6(_ZNSs4_Rep10_M_destroyERKSaIcE+0x1d)[0xb70e6a5d]
/usr/lib/libstdc++.so.6(_ZNSsD1Ev+0x57)[0xb70e95e7]
/usr/lib/libscim-1.0.so.8[0xb6afc08b]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xb6afcf77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xb6af7f05]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim23QScimInputContextGlobal10initializeEv+0x257)[0xb6b9ccf7]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim17QScimInputContextC1Ev+0x31e)[0xb6b9eace]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN22ScimInputContextPlugin6createERK7QString+0x7e)[0xb6b97cae]
/usr/lib/libqt-mt.so.3(_ZN26QInputContextPluginPrivate6createERK7QString+0x25)[0xb7b75f67]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0x94)[0xb7b75b34]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext17changeInputMethodE7QString+0xc3)[0xb6bd2c9b]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext5slaveEv+0x43)[0xb6bd2e4f]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext15setHolderWidgetEP7QWidget+0x26)[0xb6bd30be]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0xb8)[0xb7b75b58]
/usr/lib/libqt-mt.so.3(_ZN7QWidget18createInputContextEv+0x8f)[0xb78c8965]
/usr/lib/libqt-mt.so.3(_ZN7QWidget17resetInputContextEv+0x1d)[0xb78c8c6b]
/usr/lib/libqt-mt.so.3(_ZN9QLineEdit7setTextERK7QString+0x1d)[0xb7a490e5]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setLineEditEP9QLineEdit+0x82)[0xb7a103e6]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox13setUpLineEditEv+0x60)[0xb7a0acb0]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setEditableEb+0x67)[0xb7a0df69]
skype[0x81944a7]
skype[0x8078989]
skype[0x8075972]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7302ebc]
skype(_ZN6QFrame10paintEventEP11QPaintEvent+0x6d)[0x806f7b1]
======= Memory map: ========
08048000-08988000 rwxp 00000000 03:04 469920     /usr/bin/skype
08988000-08a44000 rw-p 08988000 00:00 0          [heap]
b6900000-b6921000 rw-p b6900000 00:00 0 
b6921000-b6a00000 ---p b6921000 00:00 0 
b6a94000-b6b68000 r-xp 00000000 03:04 661858     /usr/lib/libscim-1.0.so.8.1.0
b6b68000-b6b76000 rw-p 000d4000 03:04 661858     /usr/lib/libscim-1.0.so.8.1.0
b6b89000-b6ba7000 r-xp 00000000 03:04 711698     /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6ba7000-b6ba8000 rw-p 0001e000 03:04 711698     /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6ba8000-b6bcc000 r-xp 00000000 03:04 709376     /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6bcc000-b6bcd000 rw-p 00024000 03:04 709376     /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6bcd000-b6bd6000 r-xp 00000000 03:04 709374     /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6bd6000-b6bd7000 rw-p 00009000 03:04 709374     /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6bd7000-b6c54000 r--p 00000000 03:04 96813      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6c54000-b6c7e000 r-xp 00000000 03:04 661704     /usr/lib/liblcms.so.1.0.15
b6c7e000-b6c7f000 rw-p 00029000 03:04 661704     /usr/lib/liblcms.so.1.0.15
b6c7f000-b6c82000 rw-p b6c7f000 00:00 0 
b6c82000-b6ced000 r-xp 00000000 03:04 661733     /usr/lib/libmng.so.1.1.0.9
b6ced000-b6cf0000 rw-p 0006a000 03:04 661733     /usr/lib/libmng.so.1.1.0.9
b6cf7000-b6d02000 r-xp 00000000 03:04 709377     /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6d02000-b6d03000 rw-p 0000a000 03:04 709377     /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6d03000-b6d2d000 r-xp 00000000 03:04 662339     /usr/lib/libkdefx.so.4.2.0
b6d2d000-b6d2e000 rw-p 0002a000 03:04 662339     /usr/lib/libkdefx.so.4.2.0
b6d33000-b6d35000 r-xp 00000000 03:04 661862     /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6d35000-b6d36000 rw-p 00001000 03:04 661862     /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6d36000-b6d3a000 r-xp 00000000 03:04 709375     /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6d3a000-b6d3b000 rw-p 00003000 03:04 709375     /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6d3b000-b6d40000 r-xp 00000000 03:04 709372     /usr/lib/qt3/plugins/imageformatsAborted (core dumped)

---

### Post by Crafty Kisses on 2007-06-08
> **thikrat said:**
> Hello,

I had skype working in Ubuntu for a while there and then all of a sudden it just stopped loading, so i went to the command line and tried to run it manually and got this.  Sorry but I have no idea what this could possibly mean and i searched on the net and in the forums, nobody seems to have a skype crashing error!  I tried to install skype manually with the .deb and with automatix2, same thing happened to both.


$ skype
*** glibc detected *** skype: free(): invalid pointer: 0x08a3e8e0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb73547cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7357e30]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7109d11]
/usr/lib/libstdc++.so.6(_ZNSs4_Rep10_M_destroyERKSaIcE+0x1d)[0xb70e6a5d]
/usr/lib/libstdc++.so.6(_ZNSsD1Ev+0x57)[0xb70e95e7]
/usr/lib/libscim-1.0.so.8[0xb6afc08b]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xb6afcf77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xb6af7f05]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim23QScimInputContextGlobal10initializeEv+0x257)[0xb6b9ccf7]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim17QScimInputContextC1Ev+0x31e)[0xb6b9eace]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN22ScimInputContextPlugin6createERK7QString+0x7e)[0xb6b97cae]
/usr/lib/libqt-mt.so.3(_ZN26QInputContextPluginPrivate6createERK7QString+0x25)[0xb7b75f67]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0x94)[0xb7b75b34]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext17changeInputMethodE7QString+0xc3)[0xb6bd2c9b]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext5slaveEv+0x43)[0xb6bd2e4f]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext15setHolderWidgetEP7QWidget+0x26)[0xb6bd30be]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0xb8)[0xb7b75b58]
/usr/lib/libqt-mt.so.3(_ZN7QWidget18createInputContextEv+0x8f)[0xb78c8965]
/usr/lib/libqt-mt.so.3(_ZN7QWidget17resetInputContextEv+0x1d)[0xb78c8c6b]
/usr/lib/libqt-mt.so.3(_ZN9QLineEdit7setTextERK7QString+0x1d)[0xb7a490e5]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setLineEditEP9QLineEdit+0x82)[0xb7a103e6]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox13setUpLineEditEv+0x60)[0xb7a0acb0]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setEditableEb+0x67)[0xb7a0df69]
skype[0x81944a7]
skype[0x8078989]
skype[0x8075972]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7302ebc]
skype(_ZN6QFrame10paintEventEP11QPaintEvent+0x6d)[0x806f7b1]
======= Memory map: ========
08048000-08988000 rwxp 00000000 03:04 469920     /usr/bin/skype
08988000-08a44000 rw-p 08988000 00:00 0          [heap]
b6900000-b6921000 rw-p b6900000 00:00 0 
b6921000-b6a00000 ---p b6921000 00:00 0 
b6a94000-b6b68000 r-xp 00000000 03:04 661858     /usr/lib/libscim-1.0.so.8.1.0
b6b68000-b6b76000 rw-p 000d4000 03:04 661858     /usr/lib/libscim-1.0.so.8.1.0
b6b89000-b6ba7000 r-xp 00000000 03:04 711698     /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6ba7000-b6ba8000 rw-p 0001e000 03:04 711698     /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6ba8000-b6bcc000 r-xp 00000000 03:04 709376     /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6bcc000-b6bcd000 rw-p 00024000 03:04 709376     /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6bcd000-b6bd6000 r-xp 00000000 03:04 709374     /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6bd6000-b6bd7000 rw-p 00009000 03:04 709374     /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6bd7000-b6c54000 r--p 00000000 03:04 96813      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6c54000-b6c7e000 r-xp 00000000 03:04 661704     /usr/lib/liblcms.so.1.0.15
b6c7e000-b6c7f000 rw-p 00029000 03:04 661704     /usr/lib/liblcms.so.1.0.15
b6c7f000-b6c82000 rw-p b6c7f000 00:00 0 
b6c82000-b6ced000 r-xp 00000000 03:04 661733     /usr/lib/libmng.so.1.1.0.9
b6ced000-b6cf0000 rw-p 0006a000 03:04 661733     /usr/lib/libmng.so.1.1.0.9
b6cf7000-b6d02000 r-xp 00000000 03:04 709377     /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6d02000-b6d03000 rw-p 0000a000 03:04 709377     /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6d03000-b6d2d000 r-xp 00000000 03:04 662339     /usr/lib/libkdefx.so.4.2.0
b6d2d000-b6d2e000 rw-p 0002a000 03:04 662339     /usr/lib/libkdefx.so.4.2.0
b6d33000-b6d35000 r-xp 00000000 03:04 661862     /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6d35000-b6d36000 rw-p 00001000 03:04 661862     /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6d36000-b6d3a000 r-xp 00000000 03:04 709375     /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6d3a000-b6d3b000 rw-p 00003000 03:04 709375     /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6d3b000-b6d40000 r-xp 00000000 03:04 709372     /usr/lib/qt3/plugins/imageformatsAborted (core dumped)

These are the things you can try:

1. See if you have your proper plugins installed, along with your proper codecs.

2. You can see if something is taking up a lot of resources and is possibly making "Skype" crash, and you can view all your proccesses that are running by going in terminal and typing:
```
top
```

---

