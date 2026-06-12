---
title: "locale problem in dapper"
date: 2007-01-15
forum: General Help
---

### Post by seshomaru samma on 2007-01-15
I just reinstalled dapper but ran into a locale problem
i first noticed it when i installed Java and got some locale related error
i thought it wasnt that important ,but i find it is because i cant seem to get scim to work (it only works in gedit but not firefox or OO)
when i run nautilus or  gedit i get :
```
(nautilus:17219): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(nautilus:17219): Gdk-WARNING **: locale not supported by C library
```
when i ran locale -a
i get :
```
locale: Cannot set LC_COLLATE to default locale: No such file or directory
C
POSIX
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
he_IL.utf8
ja_JP.utf8
zh_CN.utf8
zh_HK.utf8
zh_SG.utf8
zh_TW.utf8

```
what is the problem?
The only things I did since the fresh install were:
install chinese/japanese and hebrew support 
install java

---

