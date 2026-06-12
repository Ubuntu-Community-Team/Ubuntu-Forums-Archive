---
title: "Enigmail refuses to encrypt and decrypt"
date: 2013-11-24
forum: General Help
---

### Post by Christoph Bier on 2013-11-24
Hello,

after upgrading to 13.10 Enigmail refuses to work. I can't decrypt older messages nor encrypt new ones. GPG is working since I can encrypt text from the CLI. For example ```
echo "Test" | gpg -s
``` works.

The OpenPGP-Debug-Log says it can not find my private key. But I did not change anything compared to 13.04. I tried deactivating every single addon, including Enigmail, since I found this hint on another forum. But it did not work. When I try to decrypt a message there's an OpenPGP dialog saying: Error - Verification of signature failed (translated from german). I can't even decrypt my own emails that were encrypted by my private key, too. Any idea what's going wrong here?

Kind regards
Christoph

---

### Post by vanadium on 2013-11-25
remove your enigmail extension, then install the extension using the software center instead.

---

### Post by Christoph Bier on 2013-11-27
I already do so and I always did use the Enigmail package provided by Ubuntu or Debian, respectively:

```
$ dpkg -l enigmail
Gewünscht=Unbekannt/Installieren/R=Entfernen/P=Vollständig Löschen/Halten
| Status=Nicht/Installiert/Config/U=Entpackt/halb konFiguriert/
         Halb installiert/Trigger erWartet/Trigger anhängig
|/ Fehler?=(kein)/R=Neuinstallation notwendig (Status, Fehler: GROSS=schlecht)
||/ Name           Version      Architektur  Beschreibung
+++-==============-============-============-=================================
ii  enigmail       2:1.5.2-0ubu i386         GPG support for Thunderbird and D
```

---

