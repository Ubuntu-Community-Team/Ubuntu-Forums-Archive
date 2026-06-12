---
title: "aMSN help"
date: 2008-02-12
forum: General Help
---

### Post by UK-Wobbie on 2008-02-12
Instilled aMSN and when i load it i keep getting this!

Loading TkCximage filed.
This module is needed to run aMSN. Please complie aMSN first,Instructions on how to compile are located in the file INSTALL

I had a look in the file and i do not know what to do :confused:,
And i had a go re installing aMSN, But still getting the same thing.

lol Hmm](*,)

---

### Post by Metaljaz on 2008-02-12
what method did you use to install amsn? synaptic or .deb file?

---

### Post by Claus7 on 2008-03-01
Hello,

it sounds to me that you have installed the SVN version. Go to amsn script and change the third line which is :
exec wish $0 $@
with this:
exec wish8.5 $0 $@
And then reinstall amsn.

Regards!

---

