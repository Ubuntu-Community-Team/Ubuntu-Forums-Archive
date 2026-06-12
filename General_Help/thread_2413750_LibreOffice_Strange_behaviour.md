---
title: "LibreOffice: Strange behaviour"
date: 2019-03-01
forum: General Help
---

### Post by claus on 2019-03-01
Hello,

when working this evening with LibreOffice Writer, all of a sudden I wasn't able to close Writer. I had to perform 'ps aux' and kill the process. When invoking LibreOffice Writer via shell, I was notified that a JRE was missing, in addition with 'libreoffice-java-common': I installed both, but the problem persists. Now, even 'ps aux' doesn't help because the process 'libreoffice' is not listed anymore. Strange! Has anyone experienced a similar behaviour, and how do I fix this? Oh, yes, I'm using Ubuntu 18.04 LTS 64-bit.

TIA,

Claus

P. S.: When I try to open Writer, an unnamed text document is being restored. Once Writer has started, it isn't possible for me to edit nor delete this document. 'libreoffic --writer' results in 

> (soffice:7461): GLib-GObject-WARNING **: 03:55:06.208: ../../../../gobject/gsignal.c:3492: signal name 'selection_changed' is invalid for instance '0x557e7c647d40' of type 'OOoAtkObjCompTxt'
func=xmlSecCheckVersionExt:file=xmlsec.c:line=188:obj=unknown:subj=unknown:error=19:invalid version:mode=abi compatible;expected minor version=2;real minor version=2;expected subminor version=25;real subminor version=26

How do I get rid of this unnamed document?

---

### Post by bjlockie on 2019-03-01
Google gave me this hit:
[https://bugs.documentfoundation.org/show_bug.cgi?id=118373](https://bugs.documentfoundation.org/show_bug.cgi?id=118373)
I don't know if it is relevant (I don't understand it).

If you cancel the recovery does it keep coming back?

---

### Post by claus on 2019-03-02
The problem disappeared.

Claus

---

