---
title: "Vista Wubi - Nothing Happened"
date: 2008-02-24
forum: General Help
---

### Post by theironchef on 2008-02-24
I just downloaded the torrent for the Alpha 5 release. I installed using Wubi and it completed and all, but when I restart it jsut goes to vista and doesn't let me choose Ubuntu. I am runnign 32 bit. Any suggestions?

---

### Post by ago on 2008-02-24
You might not have the rights to edit the bootloader entries. You can check that with EasyBCD.

---

### Post by theironchef on 2008-02-24
Any idea how to add the bott sector using this program?

---

### Post by ago on 2008-02-25
Easy bcd should have an option to boot Wubi

Otherwise create a new boot entry pointing to wubildr.mbr (which should be in C:\)

---

### Post by theironchef on 2008-02-25
success! Thank you... now the fun begins

---

### Post by ago on 2008-02-25
Can you pls provide me with the wubi log anyway? 
It is in your temp folder (type %temp% in windows explorer).
Also what sorts of user rights do you have?

---

