---
title: "errors in wireless.h"
date: 2008-01-31
forum: General Help
---

### Post by jeganmhn on 2008-01-31
Hi All,
I was trying to install a software called click.
But during the install I am getting the following errors.
It would be great if someone can help me out.

Cheers,
Jegan



/elements/local/readelement.cc:37: warning: unused parameter 'port'
../click-buildtool elem2export < elements.conf > elements.cc
  CXX elements.cc
/usr/include/linux/wireless.h:650: error: '__s32' does not name a type
/usr/include/linux/wireless.h:651: error: '__u8' does not name a type
/usr/include/linux/wireless.h:652: error: '__u8' does not name a type
/usr/include/linux/wireless.h:653: error: '__u16' does not name a type
/usr/include/linux/wireless.h:663: error: '__u16' does not name a type

/usr/include/linux/wireless.h:807: error: '__u8' does not name a type
/usr/include/linux/wireless.h:808: error: '__u8' does not name a type
/usr/include/linux/wireless.h:812: error: '__u16' does not name a type
/usr/include/linux/wireless.h:813: error: '__u16' does not name a type
/usr/include/linux/wireless.h:814: error: '__u8' does not name a type
/usr/include/linux/wireless.h:820: error: '__u16' does not name a type
/usr/include/linux/wireless.h:821: error: '__u16' does not name a type
/usr/include/linux/wireless.h:834: error: '__u32' does not name a type
/usr/include/linux/wireless.h:836: error: '__u8' does not name a type
/usr/include/linux/wireless.h:842: error: '__u32' does not name a type
/usr/include/linux/wireless.h:844: error: '__u8' does not name a type
/usr/include/linux/wireless.h:851: error: '__u32' does not name a type
/usr/include/linux/wireless.h:852: error: '__u32' does not name a type
/usr/include/linux/wireless.h:863: error: '__u16' does not name a type
/usr/include/linux/wireless.h:886: error: 'IFNAMSIZ' was not declared in this scope
/usr/include/linux/wireless.h:901: error: '__u32' does not name a type
/usr/include/linux/wireless.h:925: error: 'IFNAMSIZ' was not declared in this scope
/usr/include/linux/wireless.h:945: error: '__u32' does not name a type
/usr/include/linux/wireless.h:954: error: '__u32' does not name a type
/usr/include/linux/wireless.h:955: error: '__u32' does not name a type
/usr/include/linux/wireless.h:958: error: '__u16' does not name a type
../elements/grid/airoinfo.hh:72: error: field '_ifr2' has incomplete type
../elements/grid/airoinfo.cc: In member function 'virtual int AiroInfo::initialize(ErrorHandler*)':
../elements/grid/airoinfo.cc:82: error: 'struct iwreq' has no member named 'ifr_name'
../elements/grid/airoinfo.cc:82: error: 'struct iwreq' has no member named 'ifr_name'
../elements/grid/airoinfo.cc:83: error: 'struct iwreq' has no member named 'ifr_name'
../elements/grid/airoinfo.cc:83: error: 'struct iwreq' has no member named 'ifr_name'
../elements/grid/airoinfo.cc:85: error: '_ifr2' was not declared in this scope
../elements/grid/airoinfo.cc:92: error: 'struct iwreq' has no member named 'ifr_name'
../elements/grid/airoinfo.cc: In member function 'bool AiroInfo::get_noise(int&, int&, int&)':
../elements/grid/airoinfo.cc:264: error: '_ifr2' was not declared in this scope

---

### Post by geraldm on 2008-01-31
The best place to seek would be where the source for that program is. ??

There should be an error message prior to the code posted, such as a header file not found.
If no such message, then there might be a problem with the definition of the types, as they are "#ifndef .. #endif" bracketed in linux/types.h

Gerald

---

