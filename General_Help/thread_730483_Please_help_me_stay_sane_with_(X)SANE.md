---
title: "Please help me stay sane with (X)SANE"
date: 2008-03-20
forum: General Help
---

### Post by dryder on 2008-03-20
Hi,
Feisty

I have XSANE working with my scanner. I have efax-gtk on standby or not running when trying to fax from XSANE

I can Copy, Save, Email ... but the Fax is giving me migraines. I can fax OK with efax so I know my hardware is OK.

On the Preferences>Setup>Fax efax is one of the default fax programs XSANE is supposed to setup. It doesn't.

The command it uses to send a fax in efax is FAX SEND. Doesn't work - it 'processes and queues' the file but doesn't send it.

But if I put "efax -d /dev/ttyS0" the modem 'sends' the fax - except that it doesn't wait for a ring tone or handshake so doesn't connect. It just takes the line off hook and puts on hook up at the end. So it *looks* as if it went but doesn't (no error logging in XSANE - great logic to that oversight).

I can not even pass AT commands to XSANE it as it uses the fax or efax script and to modify those for XSANE would affect normal efax-gtk operation. As XSANE is acting as a frontend for fax/efax - bad design, developers.

The efax setup documentation is non-existent in the XSANE though it exists for the other two packages that it works with. No comment.

Does anybody have XSANE working with efax and if so how, please?

Can anybody please offer help - I am sure I have not thought of everything.

Many thanks,

David

---

