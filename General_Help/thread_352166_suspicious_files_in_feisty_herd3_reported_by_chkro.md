---
title: "suspicious files in feisty herd3 reported by chkrootkit"
date: 2007-02-03
forum: General Help
---

### Post by say2sky on 2007-02-03
I have just run chkrootkit and have following report. Anyone know if these files are harmful or not. thx!

===================================================
The following suspicious files and directories were found:
/usr/lib/jvm/java-1.5.0-sun-1.5.0.10/.systemPrefs
/usr/lib/jvm/.java-1.5.0-sun.jinfo
/usr/lib/firefox/.autoreg

/usr/lib/security
/usr/lib/security/classpath.security
eth1: PACKET SNIFFER(/sbin/wpa_supplicant[5504], /sbin/dhclient3[5542])

---

### Post by kwaanens on 2007-02-03
On my Edgy system I get almost the same, except java-6 in stead of 5, no /usr/lib/security (but .../classpath.security is there). And /lib/modules/2.6.17-10-generic/volatile/.mounted as well.

I would guess, bnothing to worry about, or?

- Ketil

---

### Post by damgaard on 2007-02-16
I get this from chkrootkit:
The following suspicious files and directories were found:
/usr/lib/firefox/.autoreg
/usr/lib/jvm/.java-1.5.0-sun.jinfo
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/.systemPrefs
/lib/modules/2.6.17-11-generic/volatile/.mounted
/lib/modules/2.6.17-10-generic/volatile/.mounted

/usr/lib/security
/usr/lib/security/classpath.security
eth0: PACKET SNIFFER(/sbin/dhclient3[13394])
eth1: PACKET SNIFFER(/sbin/dhclient3[12405])
~

Can anyone please tell me if this is anything to worry about?
Personally I don't think so, but I am not sure.
It's a shame chkrootkit does not give more details why it thinks the files are suspicious.

---

