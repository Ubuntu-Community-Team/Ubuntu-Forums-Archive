---
title: "Lubuntu 20.04 LTS, tried to upgrade LibreOffice to 7.0, crashes (but not in a test VM"
date: 2021-03-24
forum: General Help
---

### Post by mikeymikec on 2021-03-24
To upgrade, I did this:
sudo add-apt-repository ppa:libreoffice/libreoffice-7-0
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove

However, when I run LibreOffice from the application launcher, nothing happens.  When I run it from a terminal, I get:

```
mike@mike-desktop:~$ libreoffice
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'


Fatal exception: Signal 6
Stack:
/usr/lib/libreoffice/program/libuno_sal.so.3(+0x3e843)[0x7f7f021fa843]
/usr/lib/libreoffice/program/libuno_sal.so.3(+0x3e9ba)[0x7f7f021fa9ba]
/lib/x86_64-linux-gnu/libc.so.6(+0x46210)[0x7f7f01ff3210]
/lib/x86_64-linux-gnu/libc.so.6(gsignal+0xcb)[0x7f7f01ff318b]
/lib/x86_64-linux-gnu/libc.so.6(abort+0x12b)[0x7f7f01fd2859]
/lib/x86_64-linux-gnu/libstdc++.so.6(+0x9e951)[0x7f7eff19c951]
/lib/x86_64-linux-gnu/libstdc++.so.6(+0xaa47c)[0x7f7eff1a847c]
/lib/x86_64-linux-gnu/libstdc++.so.6(+0xaa4e7)[0x7f7eff1a84e7]
/lib/x86_64-linux-gnu/libstdc++.so.6(+0xaa799)[0x7f7eff1a8799]
/usr/lib/libreoffice/program/libmergedlo.so(+0xeebe18)[0x7f7f0310ee18]
/usr/lib/libreoffice/program/libmergedlo.so(+0x14edc0d)[0x7f7f03710c0d]
/usr/lib/libreoffice/program/libmergedlo.so(+0x150b1d2)[0x7f7f0372e1d2]
/usr/lib/libreoffice/program/libmergedlo.so(+0x2cfc5bd)[0x7f7f04f1f5bd]
/usr/lib/libreoffice/program/libmergedlo.so(+0x2cfc89a)[0x7f7f04f1f89a]
/usr/lib/libreoffice/program/libmergedlo.so(_ZN3utl10ConfigItemC2ERKN3rtl8OUStringE14ConfigItemMode+0x82)[0x7f7f04f19532]
/usr/lib/libreoffice/program/libmergedlo.so(+0x2d36b16)[0x7f7f04f59b16]
/usr/lib/libreoffice/program/libmergedlo.so(_ZN19SvtSysLocaleOptionsC1Ev+0x129)[0x7f7f04f5afb9]
/usr/lib/libreoffice/program/libmergedlo.so(+0x311c8e6)[0x7f7f0533f8e6]
/usr/lib/libreoffice/program/libvclplug_gtk3lo.so(+0xe1c36)[0x7f7efb2d5c36]
/usr/lib/libreoffice/program/libvclplug_gtk3lo.so(+0xe3810)[0x7f7efb2d7810]
/usr/lib/libreoffice/program/libvclplug_gtk3lo.so(+0xf015b)[0x7f7efb2e415b]
/usr/lib/libreoffice/program/libmergedlo.so(_Z7InitVCLv+0x4f2)[0x7f7f0534bbe2]
/usr/lib/libreoffice/program/libmergedlo.so(_Z10ImplSVMainv+0x115)[0x7f7f0534d185]
/usr/lib/libreoffice/program/libmergedlo.so(soffice_main+0xa3)[0x7f7f043f1153]
/usr/lib/libreoffice/program/soffice.bin(+0x10b0)[0x556d4310b0b0]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0x7f7f01fd40b3]
/usr/lib/libreoffice/program/soffice.bin(+0x10ee)[0x556d4310b0ee]


```

Yet doing the same upgrade in a test Lubuntu 20.04 LTS VM works fine.

---

### Post by GhX6GZMB on 2021-03-24
Only thing I can see is, that you're using apt-get instead of apt. Apt-get is somewhat outdated.

---

### Post by mikeymikec on 2021-03-24
Huh, I didn't realise there was a difference.  Is the format the same aside from removing -get?

---

