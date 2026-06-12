---
title: "Trying to install world community grid"
date: 2014-01-01
forum: General Help
---

### Post by Castlef on 2014-01-01
When I try to run it says ./boincmgr: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory


I have looked at various articles of people with similar error messages. I followed one howto.....

:~/Downloads/BOINC$ apt-file search libgtk-x11-2.0.so.0
libgtk2.0-0: /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
libgtk2.0-0: /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0.2400.20
libgtk2.0-0-dbg: /usr/lib/debug/usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0.2400.20

but when I try to install libgtk2.0 it says it's already the newest version

---

### Post by oldos2er on 2014-01-01
What Ubuntu version are you using? And what version of boinc?

---

### Post by Castlef on 2014-01-01
uname -a
 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux



boinc_6.10.58_i686-pc-linux-gnu.sh

---

### Post by Dave_L on 2014-01-01
uname tells you the kernel version, although that information may be helpful here too. To display the Ubuntu version:

```
lsb_release -a
```

---

### Post by steeldriver on 2014-01-01
it look like you installed a 32-bit (i686) version of boinc on a 64-bit system - so likely it is complaining about a missing 32-bit libgtk-x11-2.0.so.0

---

### Post by Castlef on 2014-01-01
ahh. I am using ubuntu 13.10 gnome

---

### Post by oldos2er on 2014-01-01
Here's a link to the 64-bit version of boinc, I'd give that a try: [http://boinc.berkeley.edu/dl/boinc_7.2.33_x86_64-pc-linux-gnu.sh](http://boinc.berkeley.edu/dl/boinc_7.2.33_x86_64-pc-linux-gnu.sh)

---

### Post by Dave_L on 2014-01-01
I noticed that boinc is also in the standard repositories.

---

