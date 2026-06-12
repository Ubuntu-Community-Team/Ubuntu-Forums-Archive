---
title: "Can't set print preferences on SAMBA printer"
date: 2007-06-30
forum: General Help
---

### Post by tenjin on 2007-06-30
Hi,

I share my LaserJet 1320 from Feisty via SAMBA.

I can't set any print preferences from Windows XP. Whenever I change anything the changes never get saved.

I'm assuming that this is an Ubuntu issue, but could be XP I suppose.

Does anyone have any ideas how to get print preferences working for a SAMBA shared printer?

Cheers

D.

---

### Post by tenjin on 2007-07-06
* Bump *

---

### Post by tenjin on 2007-07-06
Hi,

I've tested this on more than on XP machine now and I get the same problem.

This must be a SAMBA issue.

BTW, it was working fine on Edgy....

Cheers

D.

---

### Post by tenjin on 2007-07-06
Hi,

Set "default devmode" to "no".

This allows Windows to set its own device mode rather than rely on Samba to provide one.

On some machines / printers this may cause issues with explorer (e.g. crashes of explorer.exe) so your mileage may vary.

Cheers

D.

---

