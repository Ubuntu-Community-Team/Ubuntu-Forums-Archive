---
title: "How to Share Printers/Files in Gutsy with XP?"
date: 2007-12-20
forum: General Help
---

### Post by Geekkit on 2007-12-20
I can't for the life of me seem to make this work. I go to System->Administration->Printers and specify  under basic server settings to show printers, share published printers, then I go to the printer's policies tab and make sure that the enabled checkbox, the accepting jobs checkbox, and the shared checkbox are all selected.

SAMBA is installed and yet .... no printer seen in XP!

Not only that but when XP sees other computers on the network it sees a workgroup of MSHOME and yet I changed this bloody line in the :/etc/samba/smb.conf file to something else but MSHOME. 

Any ideas of how to trick this OS into sharing?

---

### Post by margori on 2007-12-20
This is the guide you have to read: [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

---

### Post by Geekkit on 2007-12-20
> **margori said:**
> This is the guide you have to read: [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

margori ...

Bless you!!! Thanks, that got printing working!! Thank you for your time!!!  :)

---

